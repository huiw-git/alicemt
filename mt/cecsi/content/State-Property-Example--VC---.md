---
title: "State Property Example (VC++)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - C++
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1c38cd3b-e4f5-4754-b115-ef5e46d24ab9
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
# State Property Example (VC++)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This example uses the <legacyLink xlink:href="0b993bac-2653-40b1-bcbb-5b57b6aae2bf">State</legacyLink> property to display a message while asynchronous connections are opening and asynchronous commands are executing.</para>
    <code>// BeginStateCpp.cpp
// compile with: /EHsc
#import "msado15.dll" no_namespace rename("EOF", "EndOfFile")

#include &lt;ole2.h&gt;
#include &lt;stdio.h&gt;
#include &lt;conio.h&gt;

// Function declarations
inline void TESTHR(HRESULT x) {if FAILED(x) _com_issue_error(x);};
void StateX();
void PrintProviderError(_ConnectionPtr pConnection);
void PrintComError(_com_error &amp;e);

int main() {
   if (FAILED(::CoInitialize(NULL)))
      return -1;

   StateX();
   ::CoUninitialize();
}

void StateX() {
   HRESULT  hr = S_OK;

   // Define string variables.
   _bstr_t strSQLChange("UPDATE Titles SET Type = 'self_help' WHERE Type = 'psychology'");
   _bstr_t strSQLRestore("UPDATE Titles SET Type = 'psychology' WHERE Type = 'self_help'");
   _bstr_t strCnn("Provider='sqloledb'; Data Source='My_Data_Source'; Initial Catalog='pubs'; Integrated Security='SSPI';");

   // Define ADO object pointers.  Initialize pointers on define.
   // These are in the ADODB::  namespace.
   _ConnectionPtr pConnection = NULL;
   _ConnectionPtr pConnection2 = NULL;
   _CommandPtr pCmdChange = NULL;
   _CommandPtr pCmdRestore = NULL;

   try {
      // Open two asynchronous connections,displaying a message while connecting.
      TESTHR(pConnection.CreateInstance(__uuidof(Connection)));
      TESTHR(pConnection2.CreateInstance(__uuidof(Connection)));

      pConnection-&gt;Open (strCnn, "", "", adAsyncConnect);
      while(pConnection-&gt;State == adStateConnecting)
         printf("Opening first connection....\n\n");

      pConnection2-&gt;Open (strCnn, "", "", adAsyncConnect);
      while(pConnection2-&gt;State == adStateConnecting)
         printf("Opening second connection....\n\n");

      // Create two command objects.
      TESTHR(pCmdChange.CreateInstance(__uuidof(Command)));
      pCmdChange-&gt;ActiveConnection = pConnection;
      pCmdChange-&gt;CommandText = strSQLChange;

      TESTHR(pCmdRestore.CreateInstance(__uuidof(Command)));
      pCmdRestore-&gt;ActiveConnection = pConnection2;
      pCmdRestore-&gt;CommandText = strSQLRestore;

      // Executing the commands,displaying a message while they are executing.
      pCmdChange-&gt;Execute(NULL,NULL,adAsyncExecute);
      while(pCmdChange-&gt;State == adStateExecuting)
         printf("Change command executing...\n\n");

      pCmdRestore-&gt;Execute(NULL,NULL,adAsyncExecute);
      while(pCmdRestore-&gt;State == adStateExecuting)
         printf("Restore command executing...\n\n");
   }
   catch (_com_error &amp;e) {
      // Notify the user of errors if any.
      PrintProviderError(pConnection);
      PrintComError(e);
   }

   if (pConnection)
      if (pConnection-&gt;State == adStateOpen)
         pConnection-&gt;Close();
   if (pConnection2)
      if (pConnection2-&gt;State == adStateOpen)
         pConnection2-&gt;Close();
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
<link xlink:href="0b993bac-2653-40b1-bcbb-5b57b6aae2bf">State Property</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>