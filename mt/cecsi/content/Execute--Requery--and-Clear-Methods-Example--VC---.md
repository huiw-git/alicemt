---
title: "Execute, Requery, and Clear Methods Example (VC++)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - C++
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ada6acc1-82eb-4cfa-8f2f-617a916ffd8d
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
# Execute, Requery, and Clear Methods Example (VC++)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This example demonstrates the <legacyBold>Execute</legacyBold> method when run from both a <legacyLink xlink:href="a02c22fb-542d-465e-a629-30fd59dcbebf">Command</legacyLink> object and a <legacyLink xlink:href="ef6b1824-5b12-43db-89d7-8f3d13896d4d">Connection</legacyLink> object. It also uses the <legacyLink xlink:href="d81ab76f-1aa8-4ccf-92ec-b65254dc3ea1">Requery</legacyLink> method to retrieve current data in a <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">recordset</legacyLink>, and the <legacyLink xlink:href="0a61ba7a-20b8-426a-91a0-9040e7c5a98a">Clear</legacyLink> method to clear the contents of the <legacyLink xlink:href="290819e1-7b39-4e1e-a93b-801257138b00">Errors</legacyLink> collection. The ExecuteCommand and PrintOutput functions are required for this example to run.</para>
    <code>// Execute_Requery_Clear_Method_Sample.cpp
// compile with: /EHsc
#include &lt;ole2.h&gt;
#include &lt;stdio.h&gt;

#import "msado15.dll" no_namespace rename("EOF", "EndOfFile")

// Function declarations
inline void TESTHR(HRESULT x) { if FAILED(x) _com_issue_error(x); };
void ExecuteX();
void ExecuteCommand(_CommandPtr pCmdTemp, _RecordsetPtr pRstTemp);
void PrintOutput(_RecordsetPtr pRstTemp);
void PrintProviderError(_ConnectionPtr pConnection);
void PrintComError(_com_error &amp;e);

int main() {
   if ( FAILED(::CoInitialize(NULL)) )
      return -1;

   ExecuteX();
   ::CoUninitialize();
}

void ExecuteX() {
   // Define string variables.
   _bstr_t strSQLChange("UPDATE Titles SET Type = 'self_help' WHERE Type = 'psychology'");
   _bstr_t strSQLRestore("UPDATE Titles SET Type = 'psychology' WHERE Type = 'self_help'");
   _bstr_t strCnn("Provider='sqloledb'; Data Source='My_Data_Source'; Initial Catalog='pubs'; Integrated Security='SSPI';");

   // Define ADO object pointers.  Initialize pointers on define.
   // These are in the ADODB::  namespace.
   _ConnectionPtr pConnection = NULL;
   _CommandPtr pCmdChange = NULL;
   _RecordsetPtr pRstTitles = NULL;

   try {
      // Open connection.
      TESTHR(pConnection.CreateInstance(__uuidof(Connection)));
      pConnection-&gt;Open (strCnn, "", "", adConnectUnspecified);

      // Create command object.
      TESTHR(pCmdChange.CreateInstance(__uuidof(Command)));
      pCmdChange-&gt;ActiveConnection = pConnection;
      pCmdChange-&gt;CommandText = strSQLChange;

      // Open titles table, casting Connection pointer to an 
      // IDispatch type so converted to correct type of variant.
      TESTHR(pRstTitles.CreateInstance(__uuidof(Recordset)));
      pRstTitles-&gt;Open ("Titles", _variant_t((IDispatch *) pConnection, true), 
         adOpenStatic, adLockOptimistic, adCmdTable);

      // Print report of original data.
      printf("\n\nData in Titles table before executing the query: \n");

      // Call function to print loop recordset contents.
      PrintOutput(pRstTitles);

      // Clear extraneous errors from the Errors collection.
      pConnection-&gt;Errors-&gt;Clear();

      // Call ExecuteCommand subroutine to execute pCmdChange command.
      ExecuteCommand(pCmdChange, pRstTitles);

      // Print report of new data.
      printf("\n\n\tData in Titles table after executing the query: \n");
      PrintOutput(pRstTitles);

      // Use Connection object's Execute method to execute SQL statement to restore data.
      pConnection-&gt;Execute(strSQLRestore, NULL, adExecuteNoRecords);

      // Retrieve the current data by requerying the recordset.
      pRstTitles-&gt;Requery(adCmdUnknown);

      // Print report of restored data.
      printf("\n\n\tData after exec. query to restore original info: \n");
      PrintOutput(pRstTitles);
   }
   catch (_com_error &amp;e) {
      PrintProviderError(pConnection);
      PrintComError(e);
   }

   // Clean up objects before exit.
   if (pRstTitles)
      if (pRstTitles-&gt;State == adStateOpen)
         pRstTitles-&gt;Close();
   if (pConnection)
      if (pConnection-&gt;State == adStateOpen)
         pConnection-&gt;Close();
}

void ExecuteCommand(_CommandPtr pCmdTemp, _RecordsetPtr pRstTemp) {
   try {
      // CommandText property already set before function was called.
      pCmdTemp-&gt;Execute(NULL, NULL, adCmdText);

      // Retrieve the current data by requerying the recordset.
      pRstTemp-&gt;Requery(adCmdUnknown);
   }

   catch(_com_error &amp;e) {
      // Notify user of any errors that result from executing the query.
      // Pass a connection pointer accessed from the Recordset.
      PrintProviderError(pRstTemp-&gt;GetActiveConnection());
      PrintComError(e);
   }
}

void PrintOutput(_RecordsetPtr pRstTemp) {
   // Ensure at top of recordset.
   pRstTemp-&gt;MoveFirst();

   // If EOF is true, then no data and skip print loop.
   if ( pRstTemp-&gt;EndOfFile )
      printf("\tRecordset empty\n");
   else {
      // Define strings for output conversions.  Initialize to first record's values.
      _bstr_t bstrTitle;
      _bstr_t bstrType;

      // Enumerate Recordset and print from each.
      while ( !(pRstTemp-&gt;EndOfFile) ) {
         // Convert variant string to convertable string type.
         bstrTitle = pRstTemp-&gt;Fields-&gt;GetItem("Title")-&gt;Value;
         bstrType  = pRstTemp-&gt;Fields-&gt;GetItem("Type")-&gt;Value;
         printf("\t%s, %s \n", (LPCSTR) bstrTitle, (LPCSTR) bstrType);

         pRstTemp-&gt;MoveNext();
      }
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
  </introduction>
  <relatedTopics>
<link xlink:href="0a61ba7a-20b8-426a-91a0-9040e7c5a98a">Clear Method</link>
<link xlink:href="a02c22fb-542d-465e-a629-30fd59dcbebf">Command Object</link>
<link xlink:href="ef6b1824-5b12-43db-89d7-8f3d13896d4d">Connection Object</link>
<link xlink:href="290819e1-7b39-4e1e-a93b-801257138b00">Errors Collection</link>
<link xlink:href="f84a5ff3-0528-4ad7-9bea-9a15103378dd">Execute Method (ADO Command)</link>
<link xlink:href="03c69320-96b2-4d85-8d49-a13b13e31578">Execute Method (ADO Connection)</link>
<link xlink:href="d81ab76f-1aa8-4ccf-92ec-b65254dc3ea1">Requery Method</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>