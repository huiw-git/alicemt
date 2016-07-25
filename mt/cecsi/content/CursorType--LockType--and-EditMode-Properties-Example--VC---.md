---
title: "CursorType, LockType, and EditMode Properties Example (VC++)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - C++
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b2a80e44-03d8-426e-81b6-dd9dfc30e181
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
# CursorType, LockType, and EditMode Properties Example (VC++)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This example demonstrates setting the <legacyLink xlink:href="b62c66ca-58d5-430e-9257-eb38c65e48c2">CursorType</legacyLink> and <legacyLink xlink:href="9920c14e-033a-4de1-8149-0ce9737a3246">LockType</legacyLink> properties before opening a <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink>. It also shows the value of the <legacyLink xlink:href="a1b04bb2-8c8b-47f9-8477-bfd0368b6f68">EditMode</legacyLink> property under various conditions. The EditModeOutput function is required for this procedure to run.</para>
  </introduction>
  <codeExample>
    <code>// CursorType_LockType_EditMode_Property_Example.cpp
// compile with: /EHsc
#import "msado15.dll" no_namespace rename("EOF", "EndOfFile")

#include &lt;ole2.h&gt;
#include &lt;stdio.h&gt;
#include &lt;conio.h&gt;

// Function declaration
inline void TESTHR(HRESULT x) { if FAILED(x) _com_issue_error(x); };
void EditModeX();
void EditModeOutput(char *, int);
void PrintProviderError(_ConnectionPtr pConnection);
void PrintComError(_com_error &amp;e);

int main() {
   if ( FAILED(::CoInitialize(NULL)) )
      return -1;

   EditModeX();
   ::CoUninitialize();
}

void EditModeX() {
   // Define ADO object pointers.  Initialize pointers on define.
   // These are in the ADODB:: namespace.
   _RecordsetPtr pRstEmployees = NULL;
   _ConnectionPtr pConnection = NULL;

   HRESULT hr = S_OK;

   _bstr_t strCnn("Provider='sqloledb'; Data Source='My_Data_Source'; Initial Catalog='pubs'; Integrated Security='SSPI';");

   try {
      // Open a connection
      TESTHR(pConnection.CreateInstance(__uuidof(Connection)));
      hr = pConnection-&gt;Open(strCnn, "", "", adConnectUnspecified);

      // Open recordset with data from employee table 
      TESTHR(pRstEmployees.CreateInstance(__uuidof(Recordset)));

      pRstEmployees-&gt;CursorLocation = adUseClient;
      pRstEmployees-&gt;CursorType = adOpenStatic;
      pRstEmployees-&gt;LockType = adLockBatchOptimistic;

      pRstEmployees-&gt;Open("employee", _variant_t((IDispatch *) pConnection,true),
         adOpenStatic, adLockBatchOptimistic, adCmdTable);

      // Show the EditMode property under different editing states.
      pRstEmployees-&gt;AddNew ();
      pRstEmployees-&gt;Fields-&gt;Item["emp_id"]-&gt;Value = (_bstr_t)("T-T55555M");
      pRstEmployees-&gt;Fields-&gt;Item["fname"]-&gt;Value = (_bstr_t)("temp_fname");
      pRstEmployees-&gt;Fields-&gt;Item["lname"]-&gt;Value = (_bstr_t)("temp_lname");
      EditModeOutput("After AddNew: ", pRstEmployees-&gt;EditMode);

      pRstEmployees-&gt;UpdateBatch(adAffectCurrent);
      EditModeOutput("After Update: ", pRstEmployees-&gt;EditMode);

      pRstEmployees-&gt;Fields-&gt;Item["fname"]-&gt;Value = (_bstr_t)("test");
      EditModeOutput("After Edit: ", pRstEmployees-&gt;EditMode);

      // Delete new record because this is a demonstration.
      pConnection-&gt;Execute("DELETE FROM employee WHERE emp_id = 'T-T55555M'", 
         NULL, adCmdText);
   }
   catch(_com_error &amp;e) {
      // Display errors, if any. Pass connection pointer accessed from the Recordset.
      PrintProviderError(pConnection);
      PrintComError(e);
   }

   // Clean up objects before exit.
   if (pRstEmployees)
      if (pRstEmployees-&gt;State == adStateOpen)
         pRstEmployees-&gt;Close();
   if (pConnection)
      if (pConnection-&gt;State == adStateOpen)
         pConnection-&gt;Close();
}

void EditModeOutput(char *strTemp, int intEditMode) {
   // Print report based on the value of the EditMode property.
   printf("\n%s", strTemp);
   printf("\n  EditMode = ");

   switch (intEditMode) {
   case adEditNone :
      printf("adEditNone");
      break;
   case adEditInProgress :
      printf("adEditInProgress");
      break;
   case adEditAdd :
      printf("adEditAdd");
      break;
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
         printf("\n\t Error number: %x\t%s\n", pErr-&gt;Number, (LPCSTR)pErr-&gt;Description);
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
        <computerOutput>
After AddNew: 
  EditMode = adEditAdd
After Update: 
  EditMode = adEditNone
After Edit: 
  EditMode = adEditInProgress</computerOutput>
      </content>
    </comments>
  </codeExample>
  <relatedTopics>
<link xlink:href="b62c66ca-58d5-430e-9257-eb38c65e48c2">CursorType Property</link>
<link xlink:href="a1b04bb2-8c8b-47f9-8477-bfd0368b6f68">EditMode Property</link>
<link xlink:href="9920c14e-033a-4de1-8149-0ce9737a3246">LockType Property</link>
<link xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset Object</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>