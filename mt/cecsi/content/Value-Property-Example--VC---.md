---
title: "Value Property Example (VC++)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - C++
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2a104245-56df-44f3-b9b7-b3d18643d57b
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
# Value Property Example (VC++)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This example demonstrates the <legacyLink xlink:href="48919c74-86d4-462e-99b9-8854ceb8d683">Value</legacyLink> property with <legacyLink xlink:href="b10a72fc-3c4b-4186-a70b-993dc9f7a092">Field</legacyLink> and <legacyLink xlink:href="b2a4767c-03c7-4935-a3bc-df3e1a38a009">Property</legacyLink> objects by displaying field and property values for the <legacyBold><legacyItalic>Employees</legacyItalic></legacyBold> table.</para>
    <code>// BeginValueCpp.cpp
// compile with: /EHsc
#import "msado15.dll" no_namespace rename("EOF", "EndOfFile")

#include &lt;ole2.h&gt;
#include &lt;stdio.h&gt;
#include &lt;conio.h&gt;

// Function declarations
inline void TESTHR(HRESULT x) { if FAILED(x) _com_issue_error(x); };
void ValueX();
void PrintProviderError(_ConnectionPtr pConnection);
void PrintComError(_com_error &amp;e);

int main() {
   if ( FAILED(::CoInitialize(NULL)) )
      return -1;

   ValueX();
   ::CoUninitialize();
}

void ValueX() {
   HRESULT  hr = S_OK;

   // Define string variables.
   _bstr_t strCnn("Provider='sqloledb'; Data Source='My_Data_Source'; Initial Catalog='pubs'; Integrated Security='SSPI';");

   // Define ADO object pointers. Initialize pointers on define.
   // These are in the ADODB::  namespace.
   _RecordsetPtr pRstEmployees = NULL;
   FieldsPtr pFldLoop = NULL;
   PropertiesPtr pPrpLoop = NULL;
   _variant_t vtIndex;
   vtIndex.vt = VT_I2;

   try {
      // Open recordset with data from Employee table.
      TESTHR(pRstEmployees.CreateInstance(__uuidof(Recordset)));
      pRstEmployees-&gt;Open ("employee", strCnn , adOpenForwardOnly, adLockReadOnly, adCmdTable);

      printf("Field values in rstEmployees\n\n");

      // Enumerate the Fields collection of the Employees table.
      pFldLoop = pRstEmployees-&gt;GetFields();  

      for (int intFields = 0 ; intFields &lt; (int)pFldLoop-&gt;GetCount() ; intFields++) {
         vtIndex.iVal = intFields;

         // Because Value is the default property of a Field object,the use of 
         // the actual keyword here is optional.
         printf(" %s = %s\n\n" ,
            (LPCSTR) pFldLoop-&gt;GetItem(vtIndex)-&gt;GetName(),
            (LPCSTR) (_bstr_t) pFldLoop-&gt;GetItem(vtIndex)-&gt;Value);
      }

      printf("Property values in rstEmployees\n\n");

      // Enumerate the Properties collection of the Recordset object.
      pPrpLoop = pRstEmployees-&gt;GetProperties();
      int intLine = 0;

      for (int intProperties = 0 ; intProperties &lt; (int)pPrpLoop-&gt;GetCount() ; intProperties++) {
         vtIndex.iVal = intProperties;

         // Because Value is the default property of a Property object,
         // the use of the actual keyword here is optional.
         _variant_t propValue = pPrpLoop-&gt;GetItem(vtIndex)-&gt;Value;
         switch(propValue.vt) {

         case (VT_BOOL):
            if(propValue.boolVal)
               printf(" %s = True\n\n", (LPCSTR) pPrpLoop-&gt;GetItem(vtIndex)-&gt;GetName());
            else
               printf(" %s = False\n\n", (LPCSTR) pPrpLoop-&gt;GetItem(vtIndex)-&gt;GetName());
            break;

         case (VT_I4):
            printf(" %s = %d\n\n", (LPCSTR) pPrpLoop-&gt;GetItem(vtIndex)-&gt;GetName(),
               pPrpLoop-&gt;GetItem(vtIndex)-&gt;Value.lVal);
            break;

         case (VT_EMPTY):
            printf(" %s = \n\n", (LPCSTR) pPrpLoop-&gt;GetItem(vtIndex)-&gt;GetName());
            break;

         default:
            break;
         }
      }
   }
   catch (_com_error &amp;e) {
      // Notify the user of errors if any.
      // Pass a connection pointer accessed from the Recordset.
      _variant_t vtConnect = pRstEmployees-&gt;GetActiveConnection();

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

   if (pRstEmployees)
      if (pRstEmployees-&gt;State == adStateOpen)
         pRstEmployees-&gt;Close();
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

   // Print Com errors.
   printf("Error\n");
   printf("\tCode = %08lx\n", e.Error());
   printf("\tCode meaning = %s\n", e.ErrorMessage());
   printf("\tSource = %s\n", (LPCSTR) bstrSource);
   printf("\tDescription = %s\n", (LPCSTR) bstrDescription);
}</code>
  </introduction>
  <relatedTopics>
<link xlink:href="b10a72fc-3c4b-4186-a70b-993dc9f7a092">Field Object</link>
<link xlink:href="b2a4767c-03c7-4935-a3bc-df3e1a38a009">Property Object</link>
<link xlink:href="48919c74-86d4-462e-99b9-8854ceb8d683">Value Property</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>