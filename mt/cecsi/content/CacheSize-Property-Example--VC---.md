---
title: "CacheSize Property Example (VC++)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - C++
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e0e7b7ba-3943-43cb-a2cd-0e4667187973
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
# CacheSize Property Example (VC++)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This example uses the <legacyLink xlink:href="49dc9a49-af7b-433b-be36-7a14ca984fb7">CacheSize</legacyLink> property to show the difference in performance for an operation performed with and without a 30-record cache.</para>
    <code>// CacheSize_Property_Sample.cpp
// compile with: /EHsc
#import "msado15.dll" no_namespace rename("EOF", "EndOfFile")

#include &lt;ole2.h&gt;
#include &lt;stdio.h&gt;
#include &lt;conio.h&gt;
#include &lt;winbase.h&gt;

// Function declarations
inline void TESTHR(HRESULT x) { if FAILED(x) _com_issue_error(x); };
void CacheSizeX();
void PrintProviderError(_ConnectionPtr pConnection);
void PrintComError(_com_error &amp;e);

int main() {
   if ( FAILED(::CoInitialize(NULL)) )
      return -1;

   CacheSizeX();
   ::CoUninitialize();
}

void CacheSizeX() {
   // Define ADO object pointers.  Initialize pointers on define.
   // These are in the ADODB:: namespace
   _RecordsetPtr pRstRoySched = NULL;

   // Define Other Variables
   DWORD sngStart;
   DWORD sngEnd; 
   float sngNoCache;
   float sngCache;
   int intLoop = 0;
   _bstr_t strTemp;

   _bstr_t strCnn("Provider='sqloledb'; Data Source='My_Data_Source'; Initial Catalog='pubs'; Integrated Security='SSPI';");

   try {
      // Open the RoySched table.
      TESTHR(pRstRoySched.CreateInstance(__uuidof(Recordset)));
      pRstRoySched-&gt;Open("roysched", strCnn, adOpenForwardOnly, adLockReadOnly, adCmdTable);

      // Enumerate the Recordset object twice and record the elapsed time.
      sngStart = GetTickCount();

      for ( intLoop = 1 ; intLoop &lt; 2 ; intLoop++ ) {
         pRstRoySched-&gt;MoveFirst();

         while ( !(pRstRoySched-&gt;EndOfFile) ) {
            // Execute a simple operation for the performance test.
            strTemp = pRstRoySched-&gt;Fields-&gt;Item["title_id"]-&gt;Value;
            pRstRoySched-&gt;MoveNext();
         }
      }
      sngEnd = GetTickCount();
      sngNoCache = (float)(sngEnd - sngStart) / (float)1000;

      // Cache records in groups of 30 records.
      pRstRoySched-&gt;MoveFirst();
      pRstRoySched-&gt;CacheSize = 30;

      sngStart = GetTickCount();

      // Enumerate the Recordset object twice and record the elapsed time.
      for ( intLoop = 1 ; intLoop &lt; 2 ; intLoop++ ) {
         pRstRoySched-&gt;MoveFirst();
         while ( !(pRstRoySched-&gt;EndOfFile) ) {
            // Execute a simple operation for the performance test.
            strTemp = pRstRoySched-&gt;Fields-&gt;Item["title_id"]-&gt;Value;
            pRstRoySched-&gt;MoveNext();
         }
      }
      sngEnd = GetTickCount();
      sngCache = (float)(sngEnd - sngStart) / (float)1000;

      // Display performance results.
      printf("Caching Performance Results:\n");
      printf("No cache: %6.3f  seconds \n", sngNoCache);
      printf("30-record cache: %6.3f  seconds", sngCache);
   }
   catch(_com_error &amp;e) {
      // Notify the user of errors if any.
      _variant_t vtConnect = pRstRoySched-&gt;GetActiveConnection();

      // GetActiveConnection returns connect string if connection
      // is not open, else returns Connection object.
      switch(vtConnect.vt) {
      case VT_BSTR:
         PrintComError(e);
         break;
      case VT_DISPATCH:
         // Pass a connection pointer accessed from the Recordset.
         PrintProviderError(vtConnect);
         break;
      default:
         printf("Errors occured.");
         break;
      }
   }

   // Clean up objects before exit.
   if (pRstRoySched)
      if (pRstRoySched-&gt;State == adStateOpen)
         pRstRoySched-&gt;Close();
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
<link xlink:href="49dc9a49-af7b-433b-be36-7a14ca984fb7">CacheSize Property</link>
<link xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset Object</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>