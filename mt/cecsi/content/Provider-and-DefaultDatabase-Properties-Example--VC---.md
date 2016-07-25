---
title: "Provider and DefaultDatabase Properties Example (VC++)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - C++
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d9868c99-425a-4b10-af67-1929ed513fda
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
# Provider and DefaultDatabase Properties Example (VC++)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This example demonstrates the <legacyLink xlink:href="0ff70e72-0061-4ffc-90fb-e3ea23129bb2">Provider</legacyLink> property by opening three <legacyLink xlink:href="ef6b1824-5b12-43db-89d7-8f3d13896d4d">Connection</legacyLink> objects using different providers. It also uses the <legacyLink xlink:href="41e8a8dd-e69c-4a09-8736-93502e01961c">DefaultDatabase</legacyLink> property to set the default database for the Microsoft ODBC Provider.</para>
    <code>// Provider_and_DefaultDatabase_Properties.cpp
// compile with: /EHsc
#import "msado15.dll" no_namespace rename("EOF", "EndOfFile")

// Function declarations
inline void TESTHR(HRESULT x) {if FAILED(x) _com_issue_error(x);};
void ProviderX();
void PrintProviderError(_ConnectionPtr pConnection);
void PrintComError(_com_error &amp;e);

int main() {
   if (FAILED(::CoInitialize(NULL)))
      return -1;

   ProviderX();
   ::CoUninitialize();
}

void ProviderX() {
   HRESULT hr = S_OK;

   // Define ADO object pointers.  Initialize pointers on define. These are in the ADODB::  namespace.
   _ConnectionPtr pConnection1 = NULL;
   _ConnectionPtr pConnection2 = NULL;
   _ConnectionPtr pConnection3 = NULL;

   try {
      // Open a Connection using the Microsoft ODBC provider.
      TESTHR(pConnection1.CreateInstance(__uuidof(Connection)));
      pConnection1-&gt;ConnectionString = "DSN=Data;user id='MyUserId';password='MyPassword';";
      pConnection1-&gt;Open("", "", "", adConnectUnspecified);
      pConnection1-&gt;DefaultDatabase = "pubs";
      // Display the provider
      printf("\n\nConnection1 provider: %s \n\n", (LPCSTR)pConnection1-&gt;Provider);

      // Open a connection using the OLE DB Provider for Microsoft Jet.
      TESTHR(pConnection2.CreateInstance(__uuidof(Connection)));
      pConnection2-&gt;Provider = "Microsoft.Jet.OLEDB.4.0";

      char *sConn = "c:\\Northwind.mdb";
      pConnection2-&gt;Open(sConn, "admin", "", NULL);
      // Display the provider
      printf("Connection2 provider: %s \n\n",(LPCSTR)pConnection2-&gt;Provider);

      // Requires SQL Server authentication
      // Open a Connection using the Microsoft SQL Server provider.
      TESTHR(pConnection3.CreateInstance(__uuidof(Connection)));
      pConnection3-&gt;Provider = "sqloledb";
      pConnection3-&gt;Open("Data Source='(local)';Initial Catalog='pubs';Integrated Security=SSPI", "", "", NULL);
      // Display the provider.
      printf("Connection3 provider: %s\n\n", (LPCSTR)pConnection3-&gt;Provider);
   }

   catch (_com_error &amp;e) {
      // Notify the user of errors if any.
      PrintProviderError(pConnection1);
      if (pConnection2)
         PrintProviderError(pConnection2);

      if (pConnection3) 
         PrintProviderError(pConnection3);

      PrintComError(e);
   }

   if (pConnection1)
      if (pConnection1-&gt;State == adStateOpen)
         pConnection1-&gt;Close();

   if (pConnection2)
      if (pConnection2-&gt;State == adStateOpen)
         pConnection2-&gt;Close();

   if (pConnection3)
      if (pConnection3-&gt;State == adStateOpen)
         pConnection3-&gt;Close();
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

   // Print COM errors. 
   printf("Error\n");
   printf("\tCode = %08lx\n", e.Error());
   printf("\tCode meaning = %s\n", e.ErrorMessage());
   printf("\tSource = %s\n", (LPCSTR) bstrSource);
   printf("\tDescription = %s\n", (LPCSTR) bstrDescription);
}</code>
  </introduction>
  <relatedTopics>
<link xlink:href="ef6b1824-5b12-43db-89d7-8f3d13896d4d">Connection Object</link>
<link xlink:href="41e8a8dd-e69c-4a09-8736-93502e01961c">DefaultDatabase Property</link>
<link xlink:href="0ff70e72-0061-4ffc-90fb-e3ea23129bb2">Provider Property</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>