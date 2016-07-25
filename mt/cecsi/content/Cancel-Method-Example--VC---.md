---
title: "Cancel Method Example (VC++)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - C++
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7e0eaa39-0c24-4d8c-87e8-f9c4fd3455e7
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
# Cancel Method Example (VC++)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This example uses the <legacyLink xlink:href="e0db4e15-6787-41e2-8f13-9e9b524d620a">Cancel</legacyLink> method to cancel a command executing on a <legacyLink xlink:href="ef6b1824-5b12-43db-89d7-8f3d13896d4d">Connection</legacyLink> object if the connection is busy.</para>
    <code>// CancelMethodExample.cpp
// compile with: /EHsc
#import "msado15.dll" no_namespace rename("EOF", "EndOfFile")

#include &lt;ole2.h&gt;
#include &lt;stdio.h&gt;
#include&lt;conio.h&gt;

// Function declarations
inline void TESTHR(HRESULT x) { if FAILED(x) _com_issue_error(x); };
void CancelX();
void PrintProviderError(_ConnectionPtr pConnection);
void PrintComError(_com_error &amp;e);

int main() {
   if ( FAILED(::CoInitialize(NULL)) )
      return -1;

   CancelX();
   ::CoUninitialize();
}

void CancelX() {
   // Define ADO object pointers.  Initialize pointers on define.
   // These are in the ADODB::  namespace
   _ConnectionPtr pConnection = NULL;

   // Define Other Variables
   _bstr_t strCmdChange;
   _bstr_t strCmdRestore;
   BOOL booChanged = FALSE;

   _bstr_t strCnn("Provider='sqloledb'; Data Source='My_Data_Source'; Initial Catalog='pubs'; Integrated Security='SSPI';");

   try {
      // open a connection.
      TESTHR(pConnection.CreateInstance(__uuidof(Connection)));
      pConnection-&gt;Open(strCnn, "", "", adConnectUnspecified);

      // Define command strings.
      strCmdChange = "UPDATE titles SET type = 'self_help' WHERE type = 'psychology'";

      strCmdRestore = "UPDATE titles SET type = 'psychology' WHERE type = 'self_help'";

      // Begin a transaction, then execute a command asynchronously.
      pConnection-&gt;BeginTrans();
      pConnection-&gt;Execute(strCmdChange, NULL, adAsyncExecute);

      // do something else for a little while - this could be changed
      for ( int i = 1 ; i &lt;= 100000 ; i++ )
         printf("%d\n", i);      

      // If the command has NOT completed, cancel the execute and roll back the 
      // transaction. Otherwise, commit the transaction.
      if ( (pConnection-&gt;GetState()) ) {
         pConnection-&gt;Cancel();
         pConnection-&gt;RollbackTrans();
         booChanged = FALSE;
         printf("Update canceled.\n");
         printf("GetState = %d\n", pConnection-&gt;GetState());
      }
      else {
         pConnection-&gt;CommitTrans();
         booChanged = TRUE;
         printf("Update complete.\n");
      }

      // If the change was made, restore the data because this is a demonstration.
      if (booChanged) {
         pConnection-&gt;Execute(strCmdRestore, NULL, 0);
         printf("Data restored.\n");
      }
   }
   catch(_com_error &amp;e) {
      // Notify user of any errors that result from executing the query.
      // Pass a connection pointer accessed from the Connection.
      PrintProviderError(pConnection);
      PrintComError(e);
   }

   // Cleanup object before exit    
   if (pConnection)
      if (pConnection-&gt;State == adStateOpen)
         pConnection-&gt;Close();
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
         printf("Error number: %x\t%s", pErr-&gt;Number, pErr-&gt;Description);
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
<link xlink:href="e0db4e15-6787-41e2-8f13-9e9b524d620a">Cancel Method</link>
<link xlink:href="ef6b1824-5b12-43db-89d7-8f3d13896d4d">Connection Object</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>