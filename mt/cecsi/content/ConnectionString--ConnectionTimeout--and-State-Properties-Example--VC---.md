---
title: "ConnectionString, ConnectionTimeout, and State Properties Example (VC++)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - C++
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c6bd2609-4c49-462f-a1aa-7bee0f615adb
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
# ConnectionString, ConnectionTimeout, and State Properties Example (VC++)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This example demonstrates different ways of using the <legacyLink xlink:href="3be75b75-4d36-4479-ab64-9a456869252a">ConnectionString</legacyLink> property to open a <legacyLink xlink:href="ef6b1824-5b12-43db-89d7-8f3d13896d4d">Connection</legacyLink> object. It also uses the <legacyLink xlink:href="8904a403-1383-4b4b-b53d-5c01d6f5deac">ConnectionTimeout</legacyLink> property to set a connection timeout period, and the <legacyLink xlink:href="0b993bac-2653-40b1-bcbb-5b57b6aae2bf">State</legacyLink> property to check the state of the connections. The GetState function is required for this procedure to run.</para>
    <alert class="note">
      <para>If you are connecting to a data source provider that supports Windows authentication, you should specify <languageKeyword>Trusted_Connection=yes</languageKeyword> or <languageKeyword>Integrated Security = SSPI</languageKeyword> instead of user ID and password information in the connection string.</para>
    </alert>
    <code>// ConnectionStringSampleCpp.cpp
// compile with: /EHsc
#import "msado15.dll" no_namespace rename("EOF", "EndOfFile")

// Function declarations
inline void TESTHR(HRESULT x) {if FAILED(x) _com_issue_error(x);};
void ConnectionStringX();
_bstr_t GetState(int intState); 
void PrintProviderError(_ConnectionPtr pConnection);
void PrintComError(_com_error &amp;e);

int main() {
   if (FAILED(::CoInitialize(NULL)))
      return 0;

   ConnectionStringX();
   ::CoUninitialize();
}

void ConnectionStringX() {
   // Define Connection object pointers.  Initialize pointers on define.  These are in the ADODB::  namespace
   _ConnectionPtr pConnection1 = NULL;
   _ConnectionPtr pConnection2 = NULL;
   _ConnectionPtr pConnection3 = NULL;
   _ConnectionPtr pConnection4 = NULL;

   // Define Other Variables
   HRESULT hr = S_OK;

   try {
      // Open a connection using OLE DB syntax.
      TESTHR(pConnection1.CreateInstance(__uuidof(Connection)));
      pConnection1-&gt;ConnectionString = "Provider='sqloledb';Data Source='(local)';"
         "Initial Catalog='Pubs';Integrated Security='SSPI';";
      pConnection1-&gt;ConnectionTimeout = 30;
      pConnection1-&gt;Open("", "", "",adConnectUnspecified);
      printf("cnn1 state: %s\n", (LPCTSTR)GetState(pConnection1-&gt;State));

      // Open a connection using a DSN and ODBC tags.
      // It is assumed that you have create DSN 'DataPubs' with a user name as 
      // 'MyUserId' and password as 'MyPassword'.
      TESTHR(pConnection2.CreateInstance(__uuidof(Connection)));
      pConnection2-&gt;ConnectionString = "DSN=DataPubs;UID=MyUserId;PWD=MyPassword;";
      pConnection2-&gt;Open("", "", "", adConnectUnspecified);
      printf("cnn2 state: %s\n", (LPCTSTR)GetState(pConnection2-&gt;State));

      // Open a connection using a DSN and OLE DB tags.
      TESTHR(pConnection3.CreateInstance(__uuidof(Connection)));
      pConnection3-&gt;ConnectionString = "Data Source=DataPubs;";
      pConnection3-&gt;Open("", "", "", adConnectUnspecified);
      printf("cnn3 state: %s\n", (LPCTSTR)GetState(pConnection3-&gt;State));

      // Open a connection using a DSN and individual arguments instead of a connection string.
      // It is assumed that you have create DSN 'DataPubs' with a user name as 
      // 'MyUserId' and password as 'MyPassword'.
      TESTHR(pConnection4.CreateInstance(__uuidof(Connection)));
      pConnection4-&gt;Open("DataPubs", "MyUserId", "MyPassword", adConnectUnspecified);
      printf("cnn4 state: %s\n", (LPCTSTR)GetState(pConnection4-&gt;State));
   }
   catch(_com_error &amp;e) {
      // Notify user of any errors.  Pass a connection pointer accessed from the Connection.
      PrintProviderError(pConnection1);
      if (pConnection2)
         PrintProviderError(pConnection2);

      if (pConnection3)
         PrintProviderError(pConnection3);

      if (pConnection4)
         PrintProviderError(pConnection4);

      PrintComError(e);
   }

   // Cleanup objects before exit.
   if (pConnection1)
      if (pConnection1-&gt;State == adStateOpen)
         pConnection1-&gt;Close();

   if (pConnection2)
      if (pConnection2-&gt;State == adStateOpen)
         pConnection2-&gt;Close();

   if (pConnection3)
      if (pConnection3-&gt;State == adStateOpen)
         pConnection3-&gt;Close();

   if (pConnection4)
      if (pConnection4-&gt;State == adStateOpen)
         pConnection4-&gt;Close();
}

_bstr_t GetState(int intState) {
   _bstr_t strState; 
   switch(intState) {
   case adStateClosed:
      strState = "adStateClosed";
      break;
   case adStateOpen:
      strState = "adStateOpen";
      break;
   default:
      ;
   }
   return strState;
}

void PrintProviderError(_ConnectionPtr pConnection) {
   // Print Provider Errors from Connection object.
   // pErr is a record object in the Connection's Error collection.
   ErrorPtr  pErr = NULL;

   if ( (pConnection-&gt;Errors-&gt;Count) &gt; 0) {
      long nCount = pConnection-&gt;Errors-&gt;Count;

      // Collection ranges from 0 to nCount -1.
      for ( long i = 0 ; i &lt; nCount ; i++ ) {
         pErr = pConnection-&gt;Errors-&gt;GetItem(i);
         printf("Error number: %x\t%s\n", pErr-&gt;Number, (LPCSTR)pErr-&gt;Description);
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
<link xlink:href="ef6b1824-5b12-43db-89d7-8f3d13896d4d">Connection Object</link>
<link xlink:href="3be75b75-4d36-4479-ab64-9a456869252a">ConnectionString Property</link>
<link xlink:href="8904a403-1383-4b4b-b53d-5c01d6f5deac">ConnectionTimeout Property</link>
<link xlink:href="0b993bac-2653-40b1-bcbb-5b57b6aae2bf">State Property</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>