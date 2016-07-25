---
title: "NumericScale and Precision Properties Example (VC++)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - C++
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 55d91ba8-4d80-4df6-af8e-060a19ddc138
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
# NumericScale and Precision Properties Example (VC++)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This example uses the <legacyLink xlink:href="29a02992-64be-4fcd-be13-445cba205893">NumericScale</legacyLink> and <legacyLink xlink:href="1fa38e78-6b5b-414d-ba0a-3dd26b29b766">Precision</legacyLink> properties to display the numeric scale and precision of fields in the <legacyBold><legacyItalic>Discounts</legacyItalic></legacyBold> table of the <legacyBold><legacyItalic>Pubs</legacyItalic></legacyBold> database.</para>
    <code>// BeginNumericScaleCpp.cpp
// compile with: /EHsc
#import "msado15.dll" no_namespace rename("EOF", "EndOfFile")

#include &lt;ole2.h&gt;
#include &lt;stdio.h&gt;
#include &lt;conio.h&gt;

// Function declarations
inline void TESTHR(HRESULT x) { if FAILED(x) _com_issue_error(x); };
void NumericScaleX();
void PrintProviderError(_ConnectionPtr pConnection);
void PrintComError(_com_error &amp;e);

int main() {
   if ( FAILED(::CoInitialize(NULL)) )
      return -1;

   NumericScaleX();
   ::CoUninitialize();
}

void NumericScaleX() {
   // Define ADO object pointers.  Initialize pointers on define.
   // These are in the ADODB::  namespace
   _RecordsetPtr pRstDiscounts = NULL;
   FieldsPtr fldTemp = NULL;

   // Define Other Variables
   _variant_t Index;
   Index.vt = VT_I2;

   _bstr_t strCnn("Provider='sqloledb'; Data Source='My_Data_Source'; Initial Catalog='pubs'; Integrated Security='SSPI';");

   try {
      // Open recordset.
      TESTHR(pRstDiscounts.CreateInstance(__uuidof(Recordset)));
      pRstDiscounts-&gt;Open("discounts", strCnn, adOpenForwardOnly, adLockReadOnly, adCmdTable);

      // Display numeric scale and precision of numeric and small integer fields.
      fldTemp = pRstDiscounts-&gt;GetFields();

      for (short int intLoop = 0 ; intLoop &lt; (int)fldTemp-&gt;GetCount() ; intLoop++ ) {
         Index.iVal = intLoop;

         if ( (fldTemp-&gt;GetItem(Index)-&gt;Type == adNumeric) || 
            (fldTemp-&gt;GetItem(Index)-&gt;Type == adSmallInt) ) { 
            printf("Field: %s\n" , (LPCSTR)fldTemp-&gt;GetItem(Index)-&gt;GetName());
            printf("Numeric scale: %d\n", fldTemp-&gt;GetItem(Index)-&gt;GetNumericScale());
            printf("Precision: %d\n", fldTemp-&gt;GetItem(Index)-&gt;GetPrecision());
         }
      }
   }
   catch(_com_error &amp;e) {    
      // Display errors, if any. Pass a connection pointer accessed from the Recordset.
      _variant_t vtConnect = pRstDiscounts-&gt;GetActiveConnection();

      // GetActiveConnection returns connect string if connection
      // is not open, else returns Connection object.
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
   if (pRstDiscounts)
      if (pRstDiscounts-&gt;State == adStateOpen)
         pRstDiscounts-&gt;Close();
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
  </introduction>
  <relatedTopics>
<link xlink:href="29a02992-64be-4fcd-be13-445cba205893">NumericScale Property</link>
<link xlink:href="1fa38e78-6b5b-414d-ba0a-3dd26b29b766">Precision Property</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>