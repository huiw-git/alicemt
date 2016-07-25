---
title: "CompareBookmarks Method Example (VC++)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - C++
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 24ab3f3a-29c5-4ee1-942e-2634c02d0778
caps.latest.revision: 11
manager: sonalm
translation.priority.ht: 
  - de-de
  - es-es
  - fr-fr
  - it-it
  - ja-jp
  - ko-kr
  - pt-br
  - ru-ru
  - zh-cn
  - zh-tw
---
# CompareBookmarks Method Example (VC++)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This example demonstrates the <legacyLink xlink:href="d0b64286-2cc4-4a22-8f1d-9aefeebbcbc6">CompareBookmarks</legacyLink> method. The relative value of bookmarks is seldom needed unless a particular bookmark is somehow special.</para>
    <para>Designate a random row of a <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink> derived from the <legacyBold><legacyItalic>Authors</legacyItalic></legacyBold> table as the target of a search. Then display the position of each row relative to that target.</para>
    <code>// BeginCompareBookmarksCpp.cpp
// compile with: /EHsc
#import "msado15.dll" no_namespace rename("EOF", "EndOfFile")

#include &lt;ole2.h&gt;
#include &lt;stdio.h&gt;
#include &lt;conio.h&gt;
#include &lt;time.h&gt;
#include &lt;stdlib.h&gt;

// Function declarations
inline void TESTHR(HRESULT x) { if FAILED(x) _com_issue_error(x); };
void CompareBookMarksX();
void PrintProviderError(_ConnectionPtr pConnection);
void PrintComError(_com_error &amp;e);

int main() {
   if ( FAILED(::CoInitialize(NULL)) )
      return -1;

   CompareBookMarksX();
   ::CoUninitialize();
}

void CompareBookMarksX() {
   HRESULT hr = S_OK;

   _bstr_t strCnn("Provider='sqloledb'; Data Source='My_Data_Source'; Initial Catalog='pubs'; Integrated Security='SSPI';");

   // Initialize pointers on define. These are in the ADODB::  namespace.
   _RecordsetPtr pRstAuthors = NULL;
   _variant_t vTarget;
   _bstr_t strAns;
   _bstr_t strTitle;
   strTitle = "CompareBookmarks Example";
   try {    
      TESTHR(pRstAuthors.CreateInstance(__uuidof(Recordset)));

      pRstAuthors-&gt;Open("SELECT * FROM authors ORDER BY au_id", strCnn, adOpenStatic, adLockReadOnly, adCmdText);

      long count = pRstAuthors-&gt;RecordCount;
      printf("Rows in the Recordset = %d\n", count);
      if (count == 0) 
         exit(1);   // Exit if an empty recordset

      srand( (unsigned)time( NULL ) );   // Randomize

      count = int(rand() % (count-1));   // Get position between 1 and count-1
      if (!count) 
         count++;

      printf("Randomly chosen row position = %d\n", count);
      _variant_t vtBookMark = (short)adBookmarkFirst;
      pRstAuthors-&gt;Move(count,vtBookMark);   // Move row to random position

      vTarget = pRstAuthors-&gt;Bookmark;   // Remember the mystery row.
      count = 0;
      pRstAuthors-&gt;MoveFirst();

      while (!(pRstAuthors-&gt;EndOfFile)) {   // Loop through recordset
         long result = pRstAuthors-&gt;CompareBookmarks(pRstAuthors-&gt;Bookmark, vTarget);

         if (result == adCompareNotEqual)
            printf("Row %d: Bookmarks are not equal. %d\n", count, result);
         else if  (result == adCompareNotComparable) 
            printf("Row %d: Bookmarks are not comparable.\n", count);
         else {
            switch(result) {
            case adCompareLessThan:
               strAns = "less than";
               break;
            case adCompareEqual:
               strAns = "equal to";
               break;
            case adCompareGreaterThan:
               strAns = "greater than";
               break;
            default:
               strAns = "in error comparing to";
               break;
            }
            printf ("Row position  %d  is  %s  the target.\n",
               count,(LPCSTR)strAns);
         }
         count++;
         pRstAuthors-&gt;MoveNext();
      }
   }
   catch(_com_error &amp;e) {
      // Notify the user of errors if any.
      // Pass a connection pointer accessed from the Recordset.
      _variant_t vtConnect = pRstAuthors-&gt;GetActiveConnection();

      // GetActiveConnection returns connect string if connection
      // is not open, else returns Connection object.
      switch(vtConnect.vt) {
      case VT_BSTR:
         PrintComError(e);
         break;
      case VT_DISPATCH:
         PrintProviderError(vtConnect);
         break;
      default:
         printf("Errors occured.");
         break;
      }
   }

   // Clean up objects before exit.
   if (pRstAuthors)
      if (pRstAuthors-&gt;State == adStateOpen)
         pRstAuthors-&gt;Close();
}

void PrintProviderError(_ConnectionPtr pConnection) {
   // Print Provider Errors from Connection object.
   // pErr is a record object in the Connection's Error collection.
   ErrorPtr pErr = NULL;

   if ( (pConnection-&gt;Errors-&gt;Count) &gt; 0) {
      long nCount = pConnection-&gt;Errors-&gt;Count;
      // Collection ranges from 0 to nCount -1.
      for (long i = 0 ; i &lt; nCount ; i++) {
         pErr = pConnection-&gt;Errors-&gt;GetItem(i);
         printf("Error number: %x\t%s\n", pErr-&gt;Number, pErr-&gt;Description);
      }
   }
}

void PrintComError(_com_error &amp;e) {
   _bstr_t bstrSource(e.Source());
   _bstr_t bstrDescription(e.Description());

   // Print Com errors.  
   printf("Error\n");
   printf("\tCode = %08lx\n", e.Error());
   printf("\tCode meaning = %s\n", e.ErrorMessage());
   printf("\tSource = %s\n", (LPCSTR) bstrSource);
   printf("\tDescription = %s\n", (LPCSTR) bstrDescription);
}</code>
  </introduction>
  <relatedTopics>
<link xlink:href="d0b64286-2cc4-4a22-8f1d-9aefeebbcbc6">CompareBookmarks Method</link>
<link xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset Object</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>