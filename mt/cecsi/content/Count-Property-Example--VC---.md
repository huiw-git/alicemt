---
title: "Count Property Example (VC++)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - C++
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 54dfb1dd-636c-4560-8a3f-32b1f6aa07d7
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
# Count Property Example (VC++)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This example demonstrates the <legacyLink xlink:href="da9ccd1f-d402-41a2-940c-45556fc5340d">Count</legacyLink> property with two collections in the <legacyBold><legacyItalic>Employee</legacyItalic></legacyBold> database. The property obtains the number of objects in each collection, and sets the upper limit for loops that enumerate these collections. </para>
    <code>// BeginCountCpp.cpp
// compile with: /EHsc
#import "msado15.dll" no_namespace rename("EOF", "EndOfFile")

#include &lt;ole2.h&gt;
#include &lt;stdio.h&gt;
#include&lt;conio.h&gt;

// Function declarations
inline void TESTHR(HRESULT x) { if FAILED(x) _com_issue_error(x); };
void CountX();
void PrintProviderError(_ConnectionPtr pConnection);
void PrintComError(_com_error &amp;e);

int main() {
   if ( FAILED(::CoInitialize(NULL)) )
      return -1;
   CountX();
   ::CoUninitialize();
}

void CountX() {
   // Define ADO object pointers.  Initialize pointers on define.
   // These are in the ADODB::  namespace
   _RecordsetPtr pRstEmployee = NULL;

   // Define Other Variables
   _variant_t Index;
   Index.vt = VT_I2;
   int j = 0;

   _bstr_t strCnn("Provider='sqloledb'; Data Source='My_Data_Source'; Initial Catalog='pubs'; Integrated Security='SSPI';");

   try {
      // Open recordset with data from Employee table.
      TESTHR(pRstEmployee.CreateInstance(__uuidof(Recordset)));
      pRstEmployee-&gt;Open("Employee", strCnn, adOpenForwardOnly, adLockReadOnly, adCmdTable);

      // Print information about Fields collection.
      printf("%d Fields in Employee\n", pRstEmployee-&gt;Fields-&gt;Count);
      for (short int intLoop = 0 ; intLoop &lt;= (pRstEmployee-&gt;Fields-&gt;Count-1) ; intLoop++) {
         Index.iVal = intLoop;
         printf(" %s\n", (LPSTR) pRstEmployee-&gt;Fields-&gt;GetItem(Index)-&gt;Name);
      }

      // Print information about Properties collection.
      printf("\n%d Properties in Employee\n", pRstEmployee-&gt;Properties-&gt;Count);
      for (short int intLoop = 0 ; intLoop &lt;= (pRstEmployee-&gt;Properties-&gt;Count - 1) ; intLoop++) {
         j++;
         Index.iVal = intLoop;
         printf(" %s\n" , (LPSTR)pRstEmployee-&gt;Properties-&gt;GetItem(Index)-&gt;Name);
      }
   }
   catch(_com_error &amp;e) {
      // Display any errors that result from executing the query.
      // Pass a connection pointer accessed from the Recordset.
      _variant_t vtConnect = pRstEmployee-&gt;GetActiveConnection();

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
   if (pRstEmployee)
      if (pRstEmployee-&gt;State == adStateOpen)
         pRstEmployee-&gt;Close();
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
         printf("Error number: %x\t%s\n", pErr-&gt;Number, pErr-&gt;Description);
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
<link xlink:href="da9ccd1f-d402-41a2-940c-45556fc5340d">Count Property</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>