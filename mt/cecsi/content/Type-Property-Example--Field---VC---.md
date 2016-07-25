---
title: "Type Property Example (Field) (VC++)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - C++
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 440dbdb1-16fc-4cfe-9451-59a153852537
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
# Type Property Example (Field) (VC++)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This example demonstrates the <legacyLink xlink:href="8a4c079f-9f4f-4545-801d-85983b8db71e">Type</legacyLink> property by displaying the name of the constant that corresponds to the value of the <legacyBold>Type</legacyBold> property of all the <legacyLink xlink:href="b10a72fc-3c4b-4186-a70b-993dc9f7a092">Field</legacyLink> objects in the <legacyBold><legacyItalic>Employees</legacyItalic></legacyBold> table. The FieldType function is required for this procedure to run.</para>
  </introduction>
  <codeExample>
    <code>// BeginTypeFieldCpp.cpp
// compile with: /EHsc
#import "msado15.dll" no_namespace rename("EOF", "EndOfFile")

#include &lt;ole2.h&gt;
#include &lt;stdio.h&gt;
#include &lt;conio.h&gt;

// Function declarations
inline void TESTHR(HRESULT x) { if FAILED(x) _com_issue_error(x); };

void TypeX();
_bstr_t FieldType(int intType); 
void PrintProviderError(_ConnectionPtr pConnection);
void PrintComError(_com_error &amp;e);

int main() {
   if ( FAILED(::CoInitialize(NULL)) )
      return -1;

   TypeX();
   ::CoUninitialize();
}

void TypeX() {
   // Define string variables.
   _bstr_t strCnn("Provider='sqloledb'; Data Source='(local)'; Initial Catalog='pubs'; Integrated Security='SSPI';");

   // Define ADO object pointers, initialize pointers.  These are in the ADODB:: namespace.
   _RecordsetPtr pRstEmployees = NULL;
   FieldsPtr pFldLoop = NULL;

   try {  
      // Open recordset with data from Employee table.
      TESTHR(pRstEmployees.CreateInstance(__uuidof(Recordset)));
      pRstEmployees-&gt;Open ("employee", strCnn, adOpenForwardOnly, adLockReadOnly, adCmdTable);

      printf("Fields in Employee Table:\n\n");

      // Enumerate the Fields collection of the Employees table.
      pFldLoop = pRstEmployees-&gt;GetFields();
      for (short int intFields = 0 ; intFields &lt; (int)pFldLoop-&gt;GetCount() ; intFields++) {
         _variant_t Index;
         Index.vt = VT_I2;
         Index.iVal = intFields;
         printf("  Name: %s\n" , (LPCSTR) pFldLoop-&gt;GetItem(Index)-&gt;GetName());
         printf("  Type: %s\n\n", (LPCTSTR)FieldType(pFldLoop-&gt;GetItem(Index)-&gt;Type));
      }
   }
   catch (_com_error &amp;e) {
      // Display errors, if any.  Pass connection pointer accessed from the Recordset.
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

   // Clean up objects before exit.
   if (pRstEmployees)
      if (pRstEmployees-&gt;State == adStateOpen)
         pRstEmployees-&gt;Close();
}

_bstr_t FieldType(int intType) {
   _bstr_t strType; 
   switch(intType) {
   case adChar:
      strType = "adChar";
      break;
   case adVarChar:
      strType = "adVarChar";
      break;
   case adSmallInt:
      strType = "adSmallInt";
      break;
   case adUnsignedTinyInt:
      strType = "adUnsignedTinyInt";
      break;
   case adDBTimeStamp:
      strType = "adDBTimeStamp";
      break;
   default:
      break;
   }
   return strType;
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
    <comments>
      <content>
        <computerOutput>Fields in Employee Table:

  Name: emp_id
  Type: adChar

  Name: fname
  Type: adVarChar

  Name: minit
  Type: adChar

  Name: lname
  Type: adVarChar

  Name: job_id
  Type: adSmallInt

  Name: job_lvl
  Type: adUnsignedTinyInt

  Name: pub_id
  Type: adChar

  Name: hire_date
  Type: adDBTimeStamp
</computerOutput>
      </content>
    </comments>
  </codeExample>
  <relatedTopics>
<link xlink:href="b10a72fc-3c4b-4186-a70b-993dc9f7a092">Field Object</link>
<link xlink:href="8a4c079f-9f4f-4545-801d-85983b8db71e">Type Property</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>