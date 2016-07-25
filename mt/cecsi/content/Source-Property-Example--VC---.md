---
title: "Source Property Example (VC++)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - C++
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e10d33da-ea30-4138-ae40-e9f6aa9d17d9
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
# Source Property Example (VC++)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This example demonstrates the <legacyLink xlink:href="a05ba2c9-2821-4343-8607-4de9b764ec91">Source</legacyLink> property by opening three <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink> objects based on different data sources.</para>
    <code>// Source_Property_Sample.cpp
// compile with: /EHsc
#import "msado15.dll" no_namespace rename("EOF", "EndOfFile")

#include &lt;ole2.h&gt;
#include &lt;stdio.h&gt;
#include &lt;conio.h&gt;

// Function declarations
inline void TESTHR(HRESULT x) { if FAILED(x) _com_issue_error(x); };
void SourceX();
void PrintProviderError(_ConnectionPtr pConnection);
void PrintComError(_com_error &amp;e);

int main() {
   if ( FAILED(::CoInitialize(NULL)) )
      return -1;

   SourceX();
   ::CoUninitialize();
}

void SourceX() {
   // Define string variables.
   _bstr_t strCmdSQL("Select title ,type, pubdate FROM titles ORDER BY title");  
   _bstr_t strSQL("SELECT title_ID AS TitleID, title AS Title, " 
      "publishers.pub_id AS PubID, pub_name AS PubName "
      "FROM publishers INNER JOIN titles " 
      "ON publishers.pub_id = titles.pub_id " 
      "ORDER BY Title");
   _bstr_t strCnn("Provider='sqloledb'; Data Source='My_Data_Source'; Initial Catalog='pubs'; Integrated Security='SSPI';");

   // Define ADO object pointers.  Initialize pointers on define.
   // These are in the ADODB:: namespace.
   _ConnectionPtr pConnection = NULL;
   _RecordsetPtr pRstTitles = NULL;
   _RecordsetPtr pRstPublishers = NULL;
   _RecordsetPtr pRstPublishersDirect = NULL;
   _RecordsetPtr pRstTitlesPublishers = NULL;
   _CommandPtr pCmdSQL = NULL;

   try {
      // Open a connection.
      TESTHR(pConnection.CreateInstance(__uuidof(Connection)));
      pConnection-&gt;Open (strCnn, "", "", adConnectUnspecified);

      // Open a recordset based on a command object.
      TESTHR(pCmdSQL.CreateInstance(__uuidof(Command)));
      pCmdSQL-&gt;ActiveConnection = pConnection;
      pCmdSQL-&gt;CommandText = strCmdSQL;
      pRstTitles = pCmdSQL-&gt;Execute(NULL, NULL, adCmdText);

      // Open a recordset based on a a table
      TESTHR(pRstPublishers.CreateInstance(__uuidof(Recordset)));
      pRstPublishers-&gt;Open ("publishers", _variant_t((IDispatch *) pConnection, true),
         adOpenForwardOnly, adLockReadOnly, adCmdTable);

      // Open a recordset based on a table
      TESTHR(pRstPublishersDirect.CreateInstance(__uuidof(Recordset)));
      pRstPublishersDirect-&gt;Open ("publishers", _variant_t((IDispatch *) pConnection, true),
         adOpenForwardOnly, adLockReadOnly, adCmdTableDirect);

      // Open a recordset based on a SQL string.
      TESTHR(pRstTitlesPublishers.CreateInstance(__uuidof(Recordset)));
      pRstTitlesPublishers-&gt;Open(strSQL, _variant_t((IDispatch *) pConnection, true),
         adOpenForwardOnly, adLockReadOnly, adCmdText);

      // Use the Source property to display the source of each recordset.
      printf("rstTitles source: \n%s\n\n",
         (LPCSTR)(_bstr_t) pRstTitles-&gt;GetSource().bstrVal);

      printf("rstPublishers source: \n%s\n\n",
         (LPCSTR)(_bstr_t) pRstPublishers-&gt;GetSource().bstrVal);

      printf("rstPublishersDirect source: \n%s\n\n",
         (LPCSTR)(_bstr_t) pRstPublishersDirect-&gt;GetSource().bstrVal);

      printf("rstTitlesPublishers source: \n%s\n\n",
         (LPCSTR)(_bstr_t) pRstTitlesPublishers-&gt;GetSource().bstrVal);
   }
   catch (_com_error &amp;e) {
      // Notify the user of errors if any.
      PrintProviderError(pConnection);
      PrintComError(e);
   }

   if (pRstTitles)
      if (pRstTitles-&gt;State == adStateOpen)
         pRstTitles-&gt;Close();
   if (pRstPublishers)
      if (pRstPublishers-&gt;State == adStateOpen)
         pRstPublishers-&gt;Close();
   if (pRstPublishersDirect)
      if (pRstPublishersDirect-&gt;State == adStateOpen)
         pRstPublishersDirect-&gt;Close();
   if (pRstTitlesPublishers)
      if (pRstTitlesPublishers-&gt;State == adStateOpen)
         pRstTitlesPublishers-&gt;Close();
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
<link xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset Object</link>
<link xlink:href="a05ba2c9-2821-4343-8607-4de9b764ec91">Source Property (ADO Recordset)</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>