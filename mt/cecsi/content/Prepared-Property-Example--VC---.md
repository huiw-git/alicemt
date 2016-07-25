---
title: "Prepared Property Example (VC++)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - C++
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f697ac1a-f125-42b5-bbf6-762a7fa30ae3
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
# Prepared Property Example (VC++)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This example demonstrates the <legacyLink xlink:href="11ca8825-765e-4bb4-a6ce-3f6564ad8755">Prepared</legacyLink> property by opening two <legacyLink xlink:href="a02c22fb-542d-465e-a629-30fd59dcbebf">Command</legacyLink> objects — one prepared and one not prepared.</para>
  </introduction>
  <codeExample>
    <code>// Prepared_Property_Sample.cpp
// compile with: /EHsc
#import "msado15.dll" no_namespace rename("EOF", "EndOfFile")

#include &lt;ole2.h&gt;
#include &lt;stdio.h&gt;
#include &lt;conio.h&gt;
#include &lt;winbase.h&gt;

// Function declarations
inline void TESTHR(HRESULT x) { if FAILED(x) _com_issue_error(x); };
void PreparedX();
void PrintProviderError(_ConnectionPtr pConnection);
void PrintComError(_com_error &amp;e);

int main() {
   if ( FAILED(::CoInitialize(NULL)) )
      return -1;

   PreparedX();
   ::CoUninitialize();
}

void PreparedX() {
   // Define ADO object pointers.  Initialize pointers on define.
   // These are in the ADODB:: namespace.
   _ConnectionPtr pConnection = NULL;
   _CommandPtr pCmd1 = NULL;
   _CommandPtr pCmd2 = NULL;

   // Define string variables.  
   _bstr_t strCnn("Provider='sqloledb'; Data Source='My_Data_Source'; Initial Catalog='pubs'; Integrated Security='SSPI';");

   try {
      // Open a connection.
      TESTHR(pConnection.CreateInstance(__uuidof(Connection)));
      pConnection-&gt;Open (strCnn, "", "", adConnectUnspecified);

      _bstr_t strCmd ("SELECT title,type FROM titles ORDER BY type");

      // Create two command objects for the same command; one prepared and one not.
      TESTHR(pCmd1.CreateInstance(__uuidof(Command)));
      pCmd1-&gt;ActiveConnection = pConnection;
      pCmd1-&gt;CommandText = strCmd;

      TESTHR(pCmd2.CreateInstance(__uuidof(Command)));
      pCmd2-&gt;ActiveConnection = pConnection;
      pCmd2-&gt;CommandText = strCmd;
      pCmd2-&gt;PutPrepared(true);

      // Set a timer,then execute the unprepared command 20 times.
      DWORD sngStart = GetTickCount(); 

      for ( int intLoop = 1 ; intLoop &lt;= 20 ; intLoop++ )
         pCmd1-&gt;Execute(NULL, NULL, adCmdText);

      DWORD sngEnd=GetTickCount(); 
      float sngNotPrepared = (float)(sngEnd - sngStart) / (float)1000;

      // Reset the timer,then execute the prepared command 20 times
      sngStart = GetTickCount(); 
      for ( int intLoop = 1 ; intLoop &lt;= 20 ; intLoop++ )
         pCmd2-&gt;Execute(NULL, NULL, adCmdText);

      sngEnd=GetTickCount(); 

      float sngPrepared = (float)(sngEnd - sngStart) / (float)1000;

      // Display performance results
      printf("Performance Results:");
      printf("\n\nNot Prepared: %6.3f seconds", sngNotPrepared);
      printf("\nPrepared:     %6.3f seconds", sngPrepared);
   }
   catch (_com_error &amp;e) {
      // Display errors, if any. Pass a connection pointer accessed from the Connection.
      PrintProviderError(pConnection);
      PrintComError(e);
   }

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
        <computerOutput>Performance Results:

Not Prepared:  0.016 seconds
Prepared:      0.016 seconds</computerOutput>
      </content>
    </comments>
  </codeExample>
  <relatedTopics>
<link xlink:href="a02c22fb-542d-465e-a629-30fd59dcbebf">Command Object</link>
<link xlink:href="11ca8825-765e-4bb4-a6ce-3f6564ad8755">Prepared Property</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>