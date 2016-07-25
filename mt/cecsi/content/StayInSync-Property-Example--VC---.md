---
title: "StayInSync Property Example (VC++)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - C++
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3a5db5f0-094b-46e1-939b-d9fa9417a406
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
# StayInSync Property Example (VC++)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This example demonstrates how the <legacyLink xlink:href="502d69b5-dc9a-455d-b115-a03bd39a552b">StayInSync</legacyLink> property facilitates accessing rows in a hierarchical <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink>.</para>
    <para>The outer loop displays each author's first and last name, state, and identification. The appended <legacyBold>Recordset</legacyBold> for each row is retrieved from the <legacyLink xlink:href="7c371474-b88f-4730-afa5-44163a0488d5">Fields</legacyLink> collection and automatically assigned to <legacyBold>rstTitleAuthor</legacyBold> by the <legacyBold>StayInSync</legacyBold> property whenever the parent <legacyBold>Recordset</legacyBold> moves to a new row. The inner loop displays four fields from each row in the appended recordset.</para>
    <code>// BeginStayInSyncCpp.cpp
// compile with: /EHsc
#import "msado15.dll" no_namespace rename("EOF", "EndOfFile")

#include &lt;ole2.h&gt;
#include &lt;stdio.h&gt;
#include &lt;conio.h&gt;

// Function declarations
inline void TESTHR(HRESULT x) { if FAILED(x) _com_issue_error(x); };
void StayInSyncX();
void PrintProviderError(_ConnectionPtr pConnection);
void PrintComError(_com_error &amp;e);

int main() {
   if ( FAILED(::CoInitialize(NULL)) )
      return -1 ;

   StayInSyncX();
   ::CoUninitialize();
}

void StayInSyncX() {
   HRESULT  hr = S_OK;

   // Define string variables.
   _bstr_t strCnn("Provider='MSDataShape'; Data Provider='sqloledb'; Data Source='My_Data_Source'; Initial Catalog='pubs'; Integrated Security='SSPI';");


   // Define ADO object pointers.  Initialize pointers on define.
   // These are in the ADODB::  namespace.
   _ConnectionPtr pConnection = NULL;
   _RecordsetPtr pRst = NULL;
   _RecordsetPtr pRstTitleAuthor = NULL;

   try {
      TESTHR(pRstTitleAuthor.CreateInstance(__uuidof(Recordset)));
      TESTHR(pConnection.CreateInstance(__uuidof(Connection)));
      TESTHR(pRst.CreateInstance(__uuidof(Recordset)));

      // Open connection.
      pConnection-&gt;Open (strCnn, "", "", adConnectUnspecified);
      pRst-&gt;PutStayInSync(true);

      // Open recordset with names from Author &amp; titleauthor table.
      pRst-&gt;Open("SHAPE  {select * from authors} " 
         "APPEND ({select * from titleauthor}"
         "RELATE au_id TO au_id) AS chapTitleAuthor",
         _variant_t((IDispatch*)pConnection, true), adOpenStatic, adLockReadOnly, adCmdText);

      pRstTitleAuthor = pRst-&gt;GetFields()-&gt;GetItem("chapTitleAuthor")-&gt;Value;
      while (!(pRst-&gt;EndOfFile)) {    
         printf("\n%s  %s  %s    %s\n", (LPCSTR)(_bstr_t)pRst-&gt;
            Fields-&gt;GetItem("au_fname")-&gt;Value,
            (LPCSTR)(_bstr_t)pRst-&gt;Fields-&gt;GetItem("au_lname")-&gt;Value,
            (LPCSTR)(_bstr_t)pRst-&gt;Fields-&gt;GetItem("state")-&gt;Value, 
            (LPCSTR)(_bstr_t)pRst-&gt;Fields-&gt;GetItem("au_id")-&gt;Value);


         _variant_t vIndex;
         while ( !(pRstTitleAuthor-&gt;EndOfFile) ) {
            vIndex = (short) 0;
            printf("%s    ",(LPCSTR)(_bstr_t)pRstTitleAuthor-&gt;Fields-&gt;Item[&amp;vIndex]-&gt;Value);
            vIndex = (short) 1;
            printf("%s    ",(LPCSTR)(_bstr_t)pRstTitleAuthor-&gt;Fields-&gt;Item[&amp;vIndex]-&gt;Value);
            vIndex = (short) 2;
            printf("%s    ",(LPCSTR)(_bstr_t)pRstTitleAuthor-&gt;Fields-&gt;Item[&amp;vIndex]-&gt;Value);
            vIndex = (short) 3;
            printf("%s\n",(LPCSTR)(_bstr_t)pRstTitleAuthor-&gt;Fields-&gt;Item[&amp;vIndex]-&gt;Value);

            pRstTitleAuthor-&gt;MoveNext();
         }
         pRst-&gt;MoveNext();
      }
   }
   catch(_com_error &amp;e) {
      // Notify user of errors, if any.  Pass connection pointer accessed from the Recordset.
      PrintProviderError(pConnection);
      PrintComError(e);   
   }

   // Clean up objects before exit.
   if (pRst)
      if (pRst-&gt;State == adStateOpen)
         pRst-&gt;Close();
   if (pConnection)
      if (pConnection-&gt;State == adStateOpen)
         pConnection-&gt;Close();
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
<link xlink:href="7c371474-b88f-4730-afa5-44163a0488d5">Fields Collection</link>
<link xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset Object</link>
<link xlink:href="502d69b5-dc9a-455d-b115-a03bd39a552b">StayInSync Property</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>