---
title: "Attributes and Name Properties Example (VC++)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - C++
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2db7c9ca-d7d0-4c8e-840b-b27d7933ec40
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
# Attributes and Name Properties Example (VC++)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This example displays the value of the <legacyLink xlink:href="acc15d40-68a6-4ba9-85bd-12d331aecaa6">Attributes</legacyLink> property for <legacyLink xlink:href="ef6b1824-5b12-43db-89d7-8f3d13896d4d">Connection</legacyLink>, <legacyLink xlink:href="b10a72fc-3c4b-4186-a70b-993dc9f7a092">Field</legacyLink>, and <legacyLink xlink:href="b2a4767c-03c7-4935-a3bc-df3e1a38a009">Property</legacyLink> objects. It uses the <legacyLink xlink:href="cfd0e29c-8310-44ab-85c3-5761184b865d">Name</legacyLink> property to display the name of each <legacyBold>Field</legacyBold> and <legacyBold>Property</legacyBold> object.</para>
    <code>// BeginAttributesCpp.cpp
// compile with: /EHsc
#import "msado15.dll" no_namespace rename("EOF", "EndOfFile")

#include &lt;ole2.h&gt;
#include &lt;stdio.h&gt;
#include &lt;conio.h&gt;
#include "icrsint.h"

// This class extracts LastName, FirstName, FaxPhone from Employees table

class CEmployeeRs : public CADORecordBinding {
   BEGIN_ADO_BINDING(CEmployeeRs)

      // Column LastName is the 2nd field in the table
      ADO_VARIABLE_LENGTH_ENTRY2(2, adVarChar, m_szemp_LastName, sizeof(m_szemp_LastName), lemp_LastNameStatus, TRUE)

      // Column FirstName is the 17th field in the table
      ADO_VARIABLE_LENGTH_ENTRY2(17, adVarChar, m_szemp_FirstName, sizeof(m_szemp_FirstName), lemp_FirstNameStatus, TRUE)

      // Column FaxPhone is the 18th field in the table
      ADO_VARIABLE_LENGTH_ENTRY2(18, adVarChar, m_szemp_Faxphone, sizeof(m_szemp_Faxphone), lemp_FaxphoneStatus, TRUE)

      END_ADO_BINDING()

public:
   CHAR  m_szemp_LastName[21];
   ULONG lemp_LastNameStatus;
   CHAR  m_szemp_FirstName[11];
   ULONG lemp_FirstNameStatus;
   CHAR  m_szemp_Faxphone[25];
   ULONG lemp_FaxphoneStatus;
};

// Function declarations
inline void TESTHR(HRESULT x) { if FAILED(x) _com_issue_error(x); };
void AttributesX();
void PrintProviderError(_ConnectionPtr pConnection);
void PrintComError(_com_error &amp;e);

int main() {
   if ( FAILED(::CoInitialize(NULL)) )
      return -1;
   AttributesX();
   ::CoUninitialize();
}

void AttributesX() {
   // Define ADO object pointers.  Initialize pointers on define.
   // These are in the ADODB::  namespace
   _RecordsetPtr pRstEmployee  = NULL;
   _ConnectionPtr pConnection = NULL;
   FieldsPtr fldLoop = NULL;    
   PropertiesPtr proLoop = NULL;

   // Define Other Variables
   HRESULT hr = S_OK;
   _variant_t Index;
   Index.vt = VT_I2;
   int j = 0;      
   // Open a recordset using a Client Cursor for the Employee Table
   _bstr_t strCnn("Provider='sqloledb'; Data Source='(local)'; Initial Catalog='pubs'; Integrated Security='SSPI';");

   try {
      // open connection and record set
      TESTHR(pConnection.CreateInstance(__uuidof(Connection)));
      pConnection-&gt;Open(strCnn, "", "", adConnectUnspecified);

      TESTHR(pRstEmployee.CreateInstance(__uuidof(Recordset)));
      pRstEmployee-&gt;Open("Employee", _variant_t((IDispatch *)pConnection,true), adOpenForwardOnly,
         adLockReadOnly, adCmdTable);

      // Display the attributes of Connection.
      printf("Connection attributes: %d \n", pConnection-&gt;Attributes);

      // Display the attribute of the employee table's fields
      printf("\nFields attributes:\n");
      fldLoop = pRstEmployee-&gt;GetFields();

      for (int i = 0 ; i &lt; (int)fldLoop-&gt;GetCount() ; i++) {
         Index.iVal = i;
         printf ("   %s = %d \n", (LPSTR)fldLoop-&gt;GetItem(Index)-&gt;GetName(),
            (int)fldLoop-&gt;GetItem(Index)-&gt;GetAttributes());
      }

      // Display Fields of the Employee table which are NULLBALE
      printf("\nNULLABLE Fields :");

      for (int i1 = 0 ; i1 &lt; (int)fldLoop-&gt;GetCount() ; i1++) {
         Index.iVal = i1;

         if (fldLoop-&gt;GetItem(Index)-&gt;GetAttributes()  &amp; adFldIsNullable)
            printf ("%s  \n", (LPSTR)fldLoop-&gt;GetItem(Index)-&gt;GetName());    
      }

      // Display the attributes of the Employee tables's  properties
      printf("\nProperty attributes:\n");
      proLoop = pRstEmployee-&gt;GetProperties();

      for (int i2 = 0 ; i2 &lt; (int)proLoop-&gt;GetCount() ; i2++) {
         j = j + 1;
         Index.iVal = i2;
         printf (" %s = %d \n", (LPSTR)(_bstr_t)proLoop-&gt;GetItem(Index)-&gt;GetName(),
            (int)proLoop-&gt;GetItem(Index)-&gt;GetAttributes()); 
      }
   }
   catch(_com_error &amp;e) {
      // Notify the user of errors if any.

      PrintProviderError(pConnection);
      PrintComError(e);
   }

   // Clean up objects before exit.
   if (pRstEmployee)
      if (pRstEmployee-&gt;State == adStateOpen)
         pRstEmployee-&gt;Close();
   if (pConnection)
      if (pConnection-&gt;State == adStateOpen)
         pConnection-&gt;Close();
}

void PrintProviderError(_ConnectionPtr pConnection) {
   // Print Provider Errors from Connection object.

   // pErr is a record object in the Connection's Error collection.
   ErrorPtr pErr = NULL;
   long nCount = 0;    
   long i = 0;

   if ( (pConnection-&gt;Errors-&gt;Count) &gt; 0) {
      nCount = pConnection-&gt;Errors-&gt;Count;

      // Collection ranges from 0 to nCount -1.
      for (i = 0 ; i &lt; nCount ; i++) {
         pErr = pConnection-&gt;Errors-&gt;GetItem(i);
         printf("\t Error number: %x\t%s", (LPCSTR) pErr-&gt;Number, (LPCSTR) pErr-&gt;Description);
      }
   }
}

void PrintComError(_com_error &amp;e) {
   _bstr_t bstrSource(e.Source());
   _bstr_t bstrDescription(e.Description());

   // Print Com errors.  
   printf("\nError\n");
   printf("Code = %08lx\n", e.Error());
   printf("Code meaning = %s\n", e.ErrorMessage());
   printf("Source = %s\n", (LPCSTR) bstrSource);
   printf("Description = %s\n", (LPCSTR) bstrDescription);  
}</code>
  </introduction>
  <relatedTopics>
<link xlink:href="acc15d40-68a6-4ba9-85bd-12d331aecaa6">Attributes Property</link>
<link xlink:href="ef6b1824-5b12-43db-89d7-8f3d13896d4d">Connection Object</link>
<link xlink:href="b10a72fc-3c4b-4186-a70b-993dc9f7a092">Field Object</link>
<link xlink:href="cfd0e29c-8310-44ab-85c3-5761184b865d">Name Property</link>
<link xlink:href="b2a4767c-03c7-4935-a3bc-df3e1a38a009">Property Object</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>