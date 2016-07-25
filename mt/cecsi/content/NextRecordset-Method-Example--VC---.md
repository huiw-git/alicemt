---
title: "NextRecordset Method Example (VC++)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - C++
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 8bb72817-0cf5-4ce9-9fb8-043c89da941c
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
# NextRecordset Method Example (VC++)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This example uses the <legacyLink xlink:href="ab1fa449-a695-4987-b1ee-bc68f89418dd">NextRecordset</legacyLink> method to view the data in a recordset that uses a compound command statement made up of three separate <legacyBold>SELECT</legacyBold> statements.</para>
    <code>// BeginNextRecordsetCpp.cpp
// compile with: /EHsc
#import "msado15.dll" no_namespace rename("EOF", "EndOfFile")

#include &lt;stdio.h&gt;
#include &lt;ole2.h&gt;
#include &lt;conio.h&gt;
#include &lt;stdlib.h&gt;

//Function Declaration.
inline void TESTHR(HRESULT x) {if FAILED(x) _com_issue_error(x);};
void NextRecordsetX();
void PrintProviderError(_ConnectionPtr pConnection);
void PrintComError(_com_error &amp;e);

int main() {
   if (FAILED(::CoInitialize(NULL)))
      return -1;

   NextRecordsetX();
   ::CoUninitialize();
}

void NextRecordsetX() {
   // Define ADO object pointers.  Initialize pointers on define.  These are in the ADODB::  namespace.
   _RecordsetPtr pRstCompound = NULL;

   // Define Other Variables
   _variant_t index;
   index.vt = VT_I2;

   // Assign connection string to a variable.
   _bstr_t strCnn("Provider='sqloledb';Data Source='(local)';Initial Catalog='pubs';Integrated Security='SSPI';");

   try {
      // Open recordset from Authors table.
      TESTHR(pRstCompound.CreateInstance(__uuidof(Recordset)));

      // Pass the Cursor type and Lock type to the Recordset.
      pRstCompound-&gt;Open("SELECT * FROM authors; SELECT * FROM stores;SELECT * FROM jobs", 
         strCnn, adOpenForwardOnly, adLockReadOnly, adCmdText);

      // Display results from each SELECT statement.
      int intCount = 1;
      while (!(pRstCompound == NULL)) {
         printf("\n\nContents of recordset #%d\n", intCount);

         while (!pRstCompound-&gt;EndOfFile) {
            index.iVal = 0;
            printf("%s\t", (LPCSTR)(_bstr_t)pRstCompound-&gt;GetFields()-&gt;GetItem(&amp; index)-&gt;Value);
            index.iVal = 1;
            printf("%s\n", (LPCSTR)(_bstr_t)pRstCompound-&gt;Fields-&gt;GetItem(&amp; index)-&gt;Value);

            pRstCompound-&gt;MoveNext();

         }
         long lngRec = 0;
         pRstCompound = pRstCompound-&gt;NextRecordset((VARIANT *)lngRec);

         intCount = intCount + 1;
      }
   }
   catch(_com_error &amp;e) {
      // Notify the user of errors if any.  Pass a connection pointer accessed from the Recordset.
      _variant_t vtConnect = pRstCompound-&gt;GetActiveConnection();

      // GetActiveConnection returns connect string if connection is not open, else returns Connection object.
      switch(vtConnect.vt) {
      case VT_BSTR:
         PrintComError(e);
         break;
      case VT_DISPATCH:
         PrintProviderError(vtConnect);
         break;
      default:
         printf("Errors occured.");
         break;
      }
   }

   // Clean up objects before exit.
   if (pRstCompound)
      if (pRstCompound-&gt;State == adStateOpen)
         pRstCompound-&gt;Close();
}

void PrintProviderError(_ConnectionPtr pConnection) {
   // Print Provider Errors from Connection object.  pErr is a record object in the Connection's Error collection.
   ErrorPtr pErr = NULL;

   if ( (pConnection-&gt;Errors-&gt;Count) &gt; 0) {
      long nCount = pConnection-&gt;Errors-&gt;Count;
      // Collection ranges from 0 to nCount -1.
      for ( long i = 0 ; i &lt; nCount ; i++ ) {
         pErr = pConnection-&gt;Errors-&gt;GetItem(i);
         printf("\t Error number: %x\t%s", pErr-&gt;Number, (LPCSTR) pErr-&gt;Description);
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
<link xlink:href="ab1fa449-a695-4987-b1ee-bc68f89418dd">NextRecordset Method</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>