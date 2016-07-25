---
title: "Sort Property Example (VC++)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - C++
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 58199284-747b-4312-b97f-797ee7bd4435
caps.latest.revision: 10
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
# Sort Property Example (VC++)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This example uses the <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink> object's <legacyLink xlink:href="3683ffa0-6f93-4906-9533-ef6942f24f39">Sort</legacyLink> property to reorder the rows of a <legacyBold>Recordset</legacyBold> derived from the <legacyBold><legacyItalic>Authors</legacyItalic></legacyBold> table of the <legacyBold>Pubs</legacyBold> database. A secondary utility routine prints each row.</para>
    <code>// SortPropertyExample.cpp
// compile with: /EHsc
#import "msado15.dll" no_namespace rename("EOF", "EndOfFile")

#include &lt;ole2.h&gt;
#include &lt;stdio.h&gt;
#include &lt;conio.h&gt;

// Function declarations
inline void TESTHR(HRESULT x) { if FAILED(x) _com_issue_error(x); };
void SortX();
void SortXprint(_bstr_t title, _RecordsetPtr rstp);
void PrintProviderError(_ConnectionPtr pConnection);
void PrintComError(_com_error &amp;e);

int main() {
   if ( FAILED(::CoInitialize(NULL)) )
      return -1;
   SortX();
   ::CoUninitialize();
}

void SortX() {
   // Initialize pointers on define. These are in the ADODB::  namespace.
   _ConnectionPtr pConnection = NULL;
   _RecordsetPtr pRstAuthors = NULL;

   // Define string variables.
   _bstr_t strCnn("Provider='sqloledb'; Data Source='My_Data_Source'; Initial Catalog='pubs'; Integrated Security='SSPI';");

   try {
      TESTHR(pConnection.CreateInstance(__uuidof(Connection)));
      TESTHR(pRstAuthors.CreateInstance(__uuidof(Recordset)));

      pRstAuthors-&gt;CursorLocation = adUseClient;
      pConnection-&gt;Open (strCnn, "", "", adConnectUnspecified);
      pRstAuthors-&gt;Open("SELECT * FROM authors",
         _variant_t((IDispatch *) pConnection),
         adOpenStatic, adLockReadOnly, adCmdText);

      SortXprint("    Initial Order    ", pRstAuthors);

      pRstAuthors-&gt;Sort = "au_lname ASC, au_fname ASC";
      SortXprint("Last Name Ascending", pRstAuthors);

      pRstAuthors-&gt;Sort = "au_lname DESC, au_fname ASC";
      SortXprint("Last Name Descending", pRstAuthors);
   }
   catch(_com_error &amp;e) {
      PrintProviderError(pConnection);
      PrintComError(e);
   }

   // Clean up objects before exit.
   if (pRstAuthors)
      if (pRstAuthors-&gt;State == adStateOpen)
         pRstAuthors-&gt;Close();
   if (pConnection)
      if (pConnection-&gt;State == adStateOpen)
         pConnection-&gt;Close();
}

// This is the secondary utility routine that prints 
// the given title, and the contents of the specified Recordset.
void SortXprint(_bstr_t title, _RecordsetPtr rstp) {
   printf("---------------%s---------------\n", (LPCSTR)title);
   printf("First Name  Last Name\n"
      "---------------------------------------------------\n");
   rstp-&gt;MoveFirst();
   while (!(rstp-&gt;EndOfFile)) {
      _bstr_t aufname;
      _bstr_t aulname;
      aufname = rstp-&gt;GetFields()-&gt;GetItem("au_fname")-&gt;Value;
      aulname = rstp-&gt;GetFields()-&gt;GetItem("au_lname")-&gt;Value,
         printf("%s    %s\n",(LPCSTR) aufname, (LPCSTR) aulname);
      rstp-&gt;MoveNext();
   }
}

void PrintProviderError(_ConnectionPtr pConnection) {
   // Print Provider Errors from Connection object.
   // pErr is a record object in the Connection's Error collection.
   ErrorPtr pErr = NULL;

   if ( (pConnection-&gt;Errors-&gt;Count) &gt; 0) {
      long nCount = pConnection-&gt;Errors-&gt;Count;
      // Collection ranges from 0 to nCount -1.
      for ( long i = 0 ; i &lt; nCount ; i++ ) {
         pErr = pConnection-&gt;Errors-&gt;GetItem(i);
         printf("Error number: %x\t%s\n", pErr-&gt;Number, (LPCSTR) pErr-&gt;Description);
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
<link xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset Object</link>
<link xlink:href="3683ffa0-6f93-4906-9533-ef6942f24f39">Sort Property</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>