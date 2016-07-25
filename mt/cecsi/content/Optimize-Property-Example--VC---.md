---
title: "Optimize Property Example (VC++)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - C++
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: cb335455-b027-4f66-868d-d0d8b2175de1
caps.latest.revision: 12
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
# Optimize Property Example (VC++)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This example demonstrates the <legacyLink xlink:href="b10a72fc-3c4b-4186-a70b-993dc9f7a092">Field</legacyLink> object dynamic <legacyBold>Optimize</legacyBold> property. The <legacyBold>zip</legacyBold> field of the <legacyBold>Authors</legacyBold> table in the <legacyBold>Pubs</legacyBold> database is not indexed. Setting the <legacyLink xlink:href="a491c4ce-2b04-4c84-be83-3846bde8d16b">Optimize</legacyLink> property to <languageKeyword>True</languageKeyword> on the <legacyBold>zip</legacyBold> field authorizes ADO to build an index that improves the performance of the <legacyLink xlink:href="55c9810a-d8ca-46c2-a9dc-80e7ee7aa188">Find</legacyLink> method.</para>
  </introduction>
  <codeExample>
    <code>// Optimize_Property_Sample.cpp
// compile with: /EHsc
#import "msado15.dll" no_namespace rename("EOF", "EndOfFile")

#include &lt;ole2.h&gt;
#include &lt;stdio.h&gt;
#include &lt;conio.h&gt;

// Function declarations
inline void TESTHR(HRESULT x) { if FAILED(x) _com_issue_error(x); };
void OptimizeX();
void PrintProviderError(_ConnectionPtr pConnection);
void PrintComError(_com_error &amp;e);

int main() {
   if ( FAILED(::CoInitialize(NULL)) )
      return -1;

   OptimizeX();
   ::CoUninitialize();
}

void OptimizeX() {
   _bstr_t strCnn("Provider='sqloledb'; Data Source='My_Data_Source'; Initial Catalog='pubs'; Integrated Security='SSPI';");

   // Define ADO object pointers.  Initialize pointers on define.
   // These are in the ADODB:: namespace.
   _RecordsetPtr pRst = NULL;

   try {
      TESTHR(pRst.CreateInstance(__uuidof(Recordset)));

      // Enable Index creation.
      pRst-&gt;CursorLocation = adUseClient;
      pRst-&gt;Open ("SELECT * FROM authors", strCnn, adOpenStatic, adLockReadOnly, adCmdText);

      // Create the index
      pRst-&gt;Fields-&gt;GetItem("zip")-&gt;Properties-&gt;GetItem("Optimize")-&gt;PutValue("True");

      // Find Akiko Yokomoto
      pRst-&gt;Find("zip = '94595'", 1, adSearchForward);
      printf("%s %s    %s %s %s",
         (LPSTR) (_bstr_t) pRst-&gt;Fields-&gt;GetItem("au_fname")-&gt;Value,
         (LPSTR) (_bstr_t) pRst-&gt;Fields-&gt;GetItem("au_lname")-&gt;Value,
         (LPSTR) (_bstr_t) pRst-&gt;Fields-&gt;GetItem("address")-&gt;Value,
         (LPSTR) (_bstr_t) pRst-&gt;Fields-&gt;GetItem("city")-&gt;Value,
         (LPSTR) (_bstr_t) pRst-&gt;Fields-&gt;GetItem("state")-&gt;Value);

      // Delete the index
      pRst-&gt;Fields-&gt;GetItem("zip")-&gt;Properties-&gt;GetItem("Optimize")-&gt;PutValue("False");
   }
   catch (_com_error &amp;e) {
      // Display errors, if any.  Pass connection pointer accessed from the Recordset.
      _variant_t vtConnect = pRst-&gt;GetActiveConnection();

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
   if (pRst)
      if (pRst-&gt;State == adStateOpen)
         pRst-&gt;Close();
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
         printf("\t Error number: %x\t%s", pErr-&gt;Number, pErr-&gt;Description);
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
    <comments>
      <content>
        <computerOutput>Akiko Yokomoto    3 Silver Ct. Walnut Creek CA</computerOutput>
      </content>
    </comments>
  </codeExample>
  <relatedTopics>
<link xlink:href="b10a72fc-3c4b-4186-a70b-993dc9f7a092">Field Object</link>
<link xlink:href="a491c4ce-2b04-4c84-be83-3846bde8d16b">Optimize Property — Dynamic (ADO)</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>