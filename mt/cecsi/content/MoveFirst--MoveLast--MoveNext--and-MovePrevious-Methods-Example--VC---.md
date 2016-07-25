---
title: "MoveFirst, MoveLast, MoveNext, and MovePrevious Methods Example (VC++)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - C++
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7f8aea7b-9183-4b29-8ac0-a393ed2e8bd5
caps.latest.revision: 13
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
# MoveFirst, MoveLast, MoveNext, and MovePrevious Methods Example (VC++)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This example uses the <legacyLink xlink:href="a61a01a7-5b33-4150-9126-21dfa63654cb">MoveFirst</legacyLink>, <legacyLink xlink:href="a61a01a7-5b33-4150-9126-21dfa63654cb">MoveLast</legacyLink>, <legacyLink xlink:href="a61a01a7-5b33-4150-9126-21dfa63654cb">MoveNext</legacyLink>, and <legacyLink xlink:href="a61a01a7-5b33-4150-9126-21dfa63654cb">MovePrevious</legacyLink> methods to move the record pointer of a <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink> based on the supplied command. The MoveAny function is required for this example to run.</para>
  </introduction>
  <codeExample>
    <code>// MoveFirstMoveLastMoveNextSample.cpp
// compile with: /EHsc
#include &lt;ole2.h&gt;
#include &lt;stdio.h&gt;

#import "msado15.dll" no_namespace rename("EOF", "EndOfFile")

// Function declarations
inline void TESTHR(HRESULT x) { if FAILED(x) _com_issue_error(x); };
void MoveFirstX();
void MoveAny(int intChoice, _RecordsetPtr pRstTemp);
void PrintProviderError(_ConnectionPtr pConnection);
void PrintComError(_com_error &amp;e);

int main() {
   if ( FAILED(::CoInitialize(NULL)) )
      return -1;

   MoveFirstX();
   ::CoUninitialize();
}

void MoveFirstX() {
   HRESULT hr = S_OK;
   _RecordsetPtr pRstAuthors = NULL;
   _bstr_t strCnn("Provider='sqloledb'; Data Source='My_Data_Source'; Initial Catalog='pubs'; Integrated Security='SSPI';");
   _bstr_t strMessage("UPDATE Titles SET Type = "
      "'psychology' WHERE Type = 'self_help'");
   int intCommand = 0;

   // Temporary string variable for type conversion for printing.
   _bstr_t  bstrFName;
   _bstr_t  bstrLName;

   try {
      // Open recordset from Authors table.
      TESTHR(pRstAuthors.CreateInstance(__uuidof(Recordset)));
      pRstAuthors-&gt;CursorType = adOpenStatic;

      // Use client cursor to enable AbsolutePosition property.
      pRstAuthors-&gt;CursorLocation = adUseClient;
      pRstAuthors-&gt;Open("Authors", strCnn, adOpenStatic, adLockBatchOptimistic, adCmdTable);

      // Show current record information and get user's method choice.
      while (true) {   // Continuous loop.
         // Convert variant string to convertable string type.
         bstrFName = pRstAuthors-&gt;Fields-&gt;Item["au_fName"]-&gt;Value;
         bstrLName = pRstAuthors-&gt;Fields-&gt;Item["au_lName"]-&gt;Value;

         printf("Name: %s %s\n Record %d of %d\n\n",
            (LPCSTR) bstrFName,
            (LPCSTR) bstrLName,
            pRstAuthors-&gt;AbsolutePosition,
            pRstAuthors-&gt;RecordCount);
         printf("[1 - MoveFirst, 2 - MoveLast, \n");
         printf(" 3 - MoveNext, 4 - MovePrevious, 5 - Quit]\n");

         scanf_s("%d", &amp;intCommand);

         if ((intCommand &lt; 1) || (intCommand &gt; 4))
            break;   // Out of range entry exits program loop.

         // Call method based on user's input.
         MoveAny(intCommand, pRstAuthors);
      }
   }
   catch (_com_error &amp;e) {
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

void MoveAny(int intChoice, _RecordsetPtr pRstTemp) {
   // Use specified method, trapping for BOF and EOF
   try {
      switch(intChoice) {
         case 1:
            pRstTemp-&gt;MoveFirst();
            break;
         case 2:
            pRstTemp-&gt;MoveLast();
            break;
         case 3:
            pRstTemp-&gt;MoveNext();
            if (pRstTemp-&gt;EndOfFile) {
               printf("\nAlready at end of recordset!\n");
               pRstTemp-&gt;MoveLast();
            }    // End If
            break;
         case 4:
            pRstTemp-&gt;MovePrevious();
            if (pRstTemp-&gt;BOF) {
               printf("\nAlready at beginning of recordset!\n");
               pRstTemp-&gt;MoveFirst();
            }
            break;
         default:
            ;
      }
   }

   catch(_com_error &amp;e) {
      // Notify the user of errors if any.
      // Pass a connection pointer accessed from the Recordset.
      _variant_t vtConnect = pRstTemp-&gt;GetActiveConnection();

      // GetActiveConnection returns connect string if connection
      // is not open, else returns Connection object.
      switch(vtConnect.vt)  {
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
}

void PrintProviderError(_ConnectionPtr pConnection) {
   // Print Provider Errors from Connection object.

   // pErr is a record object in the Connection's Error collection.
   ErrorPtr pErr = NULL;

   if ( (pConnection-&gt;Errors-&gt;Count) &gt; 0) {
      long nCount = pConnection-&gt;Errors-&gt;Count;
      // Collection ranges from 0 to nCount - 1.
      for ( long i = 0 ; i &lt; nCount ; i++) {
         pErr = pConnection-&gt;Errors-&gt;GetItem(i);
         printf("\t Error number: %x\t%s", pErr-&gt;Number, pErr-&gt;Description);
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
    <comments>
      <content>
        <para>Input</para>
        <code>5</code>
      </content>
    </comments>
  </codeExample>
  <relatedTopics>
<link xlink:href="a61a01a7-5b33-4150-9126-21dfa63654cb">MoveFirst, MoveLast, MoveNext, and MovePrevious Methods</link>
<link xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset Object</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>