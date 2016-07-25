---
title: "Resync Method Example (VC++)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - C++
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d34dfd26-9ca7-4c9c-a918-396f05fecca9
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
# Resync Method Example (VC++)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This example demonstrates using the <legacyLink xlink:href="73b355d4-a4c0-434b-bfc4-039b1c76b32e">Resync</legacyLink> method to refresh data in a static recordset.</para>
    <code>// Resync_Method_Sample.cpp
// compile with: /EHsc
#import "msado15.dll" no_namespace rename("EOF", "EndOfFile")

#include &lt;ole2.h&gt;
#include &lt;stdio.h&gt;
#include &lt;conio.h&gt;

// Function declarations
inline void TESTHR(HRESULT x) { if FAILED(x) _com_issue_error(x); };
void ResyncX();
void PrintProviderError(_ConnectionPtr pConnection);
void PrintComError(_com_error &amp;e);

int main() {
   if ( FAILED(::CoInitialize(NULL)) )
      return -1;

   ResyncX();
   ::CoUninitialize();
}

void ResyncX() {
   // Define string variables.
   _bstr_t strCnn("Provider='sqloledb'; Data Source='My_Data_Source'; Initial Catalog='pubs'; Integrated Security='SSPI';");

   // Define ADO object pointers.  Initialize pointers on define.
   // These are in the ADODB:: namespace.
   _RecordsetPtr pRstTitles = NULL;

   try {
      // Open recordset for titles table.
      TESTHR(pRstTitles.CreateInstance(__uuidof(Recordset)));
      pRstTitles-&gt;CursorLocation = adUseClient;
      pRstTitles-&gt;CursorType = adOpenStatic;
      pRstTitles-&gt;LockType = adLockBatchOptimistic;
      pRstTitles-&gt;Open ("titles", strCnn, adOpenStatic, adLockBatchOptimistic, adCmdTable);

      // Change the type of the first title in the recordset.
      pRstTitles-&gt;Fields-&gt;GetItem("type")-&gt;Value = (_bstr_t) ("database");

      // Display the results of the change.
      printf("\nBefore resync: \n\n");

      printf("Title - %s\n\n", 
         (LPSTR)(_bstr_t) pRstTitles-&gt;Fields-&gt;GetItem("title")-&gt;Value);

      printf("Type - %s\n\n",
         (LPSTR)(_bstr_t) pRstTitles-&gt;Fields-&gt;GetItem("type")-&gt;Value);

      // Resync with database.
      pRstTitles-&gt;Resync(adAffectAll,adResyncAllValues);

      // Display the results of the resynch.
      printf("\n\nAfter resync: \n\n");

      printf("Title - %s\n\n",
         (LPSTR)(_bstr_t) pRstTitles-&gt;Fields-&gt;GetItem("title")-&gt;Value);

      printf("Type - %s\n\n",
         (LPSTR)(_bstr_t) pRstTitles-&gt;Fields-&gt;GetItem("type")-&gt;Value);
   }
   catch (_com_error &amp;e) {
      // Display errors, if any. Pass a connection pointer accessed from the Recordset.
      _variant_t vtConnect = pRstTitles-&gt;GetActiveConnection();

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

   if (pRstTitles)
      if (pRstTitles-&gt;State == adStateOpen) {
         pRstTitles-&gt;CancelBatch(adAffectAll);
         pRstTitles-&gt;Close();
      }
}

void PrintProviderError(_ConnectionPtr pConnection) {
   // Print Provider Errors from Connection object.
   // pErr is a record object in the Connection's Error collection.
   ErrorPtr pErr = NULL;

   if ( (pConnection-&gt;Errors-&gt;Count) &gt; 0 ) {
      long nCount = pConnection-&gt;Errors-&gt;Count;

      // Collection ranges from 0 to nCount -1.
      for ( long i = 0 ; i &lt; nCount ; i++ ) {
         pErr = pConnection-&gt;Errors-&gt;GetItem(i);
         printf("\t Error number: %x\t%s\n", pErr-&gt;Number, (LPCSTR) pErr-&gt;Description);
      }
   }
}

void PrintComError(_com_error &amp;e) {
   _bstr_t bstrSource(e.Source());
   _bstr_t bstrDescription(e.Description());

   // Print COM errors. 
   printf("Error\n");
   printf("\tCode = %08lx\n", e.Error());
   printf("\tCode meaning = %s\n", e.ErrorMessage());
   printf("\tSource = %s\n", (LPCSTR) bstrSource);
   printf("\tDescription = %s\n", (LPCSTR) bstrDescription);
}</code>
  </introduction>
  <relatedTopics>
<link xlink:href="73b355d4-a4c0-434b-bfc4-039b1c76b32e">Resync Method</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>