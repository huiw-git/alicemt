---
title: "Attributes Property Example (VC++)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - C++
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1057b57b-5ace-4830-9a20-562e88aeef86
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
# Attributes Property Example (VC++)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This example demonstrates the <legacyLink xlink:href="e3abb359-79a3-4c22-b3a8-2900817e0d23">Attributes</legacyLink> property of a <legacyLink xlink:href="6e772783-1bc8-4ea7-94b2-7d7a52ea5c47">Column</legacyLink>. Setting it to <legacyBold>adColNullable</legacyBold> allows the user to set the value of a <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink> <legacyLink xlink:href="b10a72fc-3c4b-4186-a70b-993dc9f7a092">Field</legacyLink> to an empty string. In this situation, the user can distinguish between a record where data is not known and a record where the data does not apply.</para>
    <code>// Attributes_Property_Sample.cpp
// compile with: /EHsc
#import "msado15.dll" rename("EOF", "EndOfFile")
#import "msadox.dll" no_namespace

#include "iostream"
#include "icrsint.h"
using namespace std;

// class extracts LastName, FirstName, FaxPhone from Employees table
class CEmployeeRs : public CADORecordBinding {
   BEGIN_ADO_BINDING(CEmployeeRs)

   // Column LastName is the 2nd field in the table
   ADO_VARIABLE_LENGTH_ENTRY2(2, 
                              adVarChar, 
                              m_szemp_LastName, 
                              sizeof(m_szemp_LastName), 
                              lemp_LastNameStatus, 
                              TRUE)

   // Column FirstName is the 17th field in the table
   ADO_VARIABLE_LENGTH_ENTRY2(17, 
                              adVarChar, 
                              m_szemp_FirstName, 
                              sizeof(m_szemp_FirstName), 
                              lemp_FirstNameStatus, 
                              TRUE)

   // Column FaxPhone is the 18th field in the table
   ADO_VARIABLE_LENGTH_ENTRY2(18, 
                              adVarChar, 
                              m_szemp_Faxphone, 
                              sizeof(m_szemp_Faxphone), 
                              lemp_FaxphoneStatus, 
                              TRUE)

END_ADO_BINDING()

public:
   CHAR m_szemp_LastName[21];
   ULONG lemp_LastNameStatus;
   CHAR m_szemp_FirstName[11];
   ULONG lemp_FirstNameStatus;
   CHAR m_szemp_Faxphone[25];
   ULONG lemp_FaxphoneStatus;
};

inline void TESTHR(HRESULT x) { if FAILED(x) _com_issue_error(x); };

int main() {
   if ( FAILED( ::CoInitialize(NULL) ) )
      return -1;

   HRESULT hr = S_OK;
   char * token;

   // Define ADOX object pointers, initialize pointers.  These are in ADODB namespace.
   _CatalogPtr m_pCatalog = NULL;
   _ColumnPtr m_pColumn = NULL;
   _TablePtr m_pTable = NULL;

   // Define ADODB object pointers
   ADODB::_ConnectionPtr m_pCnn = NULL;
   ADODB::_RecordsetPtr m_pRstEmployees = NULL;

   IADORecordBinding *picRs = NULL;   // Interface Pointer Declared
   CEmployeeRs emprs;   // C++ Class Object

   // Define string variables.
   _bstr_t strcnn("Provider='Microsoft.JET.OLEDB.4.0';Data Source= 'c:\\Northwind.mdb';");

   try {
      // Connect the catalog.
      TESTHR(hr = m_pCnn.CreateInstance(__uuidof (ADODB::Connection)));
      TESTHR(hr = m_pCatalog.CreateInstance(__uuidof (Catalog)));
      TESTHR(hr = m_pColumn.CreateInstance(__uuidof(Column)));
      TESTHR(hr = m_pRstEmployees.CreateInstance(__uuidof(ADODB::Recordset)));

      m_pCnn-&gt;Open(strcnn, "", "", NULL);
      m_pCatalog-&gt;PutActiveConnection(_variant_t((IDispatch *) m_pCnn));
      m_pTable= m_pCatalog-&gt;Tables-&gt;GetItem("Employees");

      // Create a new Field object and append it to the Fields
      // collection of the Employees table.
      m_pColumn-&gt;Name = "FaxPhone";
      m_pColumn-&gt;Type = adVarWChar;
      m_pColumn-&gt;DefinedSize = 24;
      m_pColumn-&gt;Attributes = adColNullable;

      m_pCatalog-&gt;Tables-&gt;GetItem("Employees")-&gt;Columns-&gt;Append(m_pColumn-&gt;Name, adVarWChar, 24);
      // Append("FaxPhone", adVarWChar, 24);

      // Open the Employees table for updating as a Recordset.
      m_pRstEmployees-&gt;Open("Employees", 
         _variant_t((IDispatch *) m_pCnn), 
         ADODB::adOpenKeyset, 
         ADODB::adLockOptimistic, 
         ADODB::adCmdTable);

      // Get user input.
      printf("Enter fax number for : %s %s\n", 
         (LPSTR)(_bstr_t) m_pRstEmployees-&gt;Fields-&gt;GetItem("LastName")-&gt;Value,
         (LPSTR) (_bstr_t) m_pRstEmployees-&gt;Fields-&gt;GetItem("FirstName")-&gt;Value);
      printf("[? - unknown, X - has no fax] : \n");

      // Skip user input routine, just supply a value.
      char* strTemp = strtok_s("X", " \t", &amp;token);
      _variant_t vNull;
      vNull.vt = VT_BSTR;
      vNull.bstrVal = NULL;

      if (strTemp != NULL) {
         if (strcmp(strTemp, "?") == 0)
            m_pRstEmployees-&gt;Fields-&gt;GetItem("FaxPhone")-&gt;PutValue(vNull);
         else if( (strcmp(strTemp,"X") == 0) | (strcmp(strTemp,"x") == 0) )
            m_pRstEmployees-&gt;Fields-&gt;GetItem("FaxPhone")-&gt;PutValue("");
         else
            m_pRstEmployees-&gt;Fields-&gt;GetItem("FaxPhone")-&gt;PutValue(strTemp);

         m_pRstEmployees-&gt;Update();

         // Open IADORecordBinding interface pointer for binding Recordset to a class
         TESTHR(hr = m_pRstEmployees-&gt;QueryInterface(__uuidof(IADORecordBinding),(LPVOID*)&amp;picRs));

         // Bind the Recordset to a C++ class here
         TESTHR(hr = picRs-&gt;BindToRecordset(&amp;emprs));

         // Print report.
         printf("\nName - Fax number\n");
         printf("%s %s ", emprs.lemp_LastNameStatus == adFldOK ? 
            emprs.m_szemp_LastName : "&lt;NULL&gt;",
            emprs.lemp_FirstNameStatus == adFldOK ? 
            emprs.m_szemp_FirstName : "&lt;NULL&gt;");

         if (emprs.lemp_FaxphoneStatus == adFldNull)
            printf("- [Unknown]\n");
         else if (strcmp((LPSTR)emprs.m_szemp_Faxphone, "") == 0)
            printf("- [Has no fax]\n");
         else
            printf("- %s\n", emprs.m_szemp_Faxphone);
      }

      // Delete new field because this is a demonstration.  
      // m_pTable-&gt;Columns-&gt;Delete(m_pColumn-&gt;Name);
   }
   catch(_com_error &amp;e) {
      // Notify the user of errors if any.
      _bstr_t bstrSource(e.Source());
      _bstr_t bstrDescription(e.Description());

      printf("\n\tSource :  %s \n\tdescription : %s \n ", (LPCSTR)bstrSource, (LPCSTR)bstrDescription);
   }
   catch(...) {
      cout &lt;&lt; "Error occured in AttributesX...." &lt;&lt; endl;
   }

   if (m_pRstEmployees)
      if (m_pRstEmployees-&gt;State == 1)
         m_pRstEmployees-&gt;Close();

   // Delete new field because this is a demonstration.
   if (m_pTable != NULL)
      m_pTable-&gt;Columns-&gt;Delete(m_pColumn-&gt;Name);

   if (m_pCnn)
      if (m_pCnn-&gt;State == 1)
         m_pCnn-&gt;Close();

   // Release the IADORecordset Interface here
   if (picRs)
      picRs-&gt;Release();

   ::CoUninitialize();
}</code>
  </introduction>
  <relatedTopics>
<link xlink:href="e3abb359-79a3-4c22-b3a8-2900817e0d23">Attributes Property</link>
<link xlink:href="6e772783-1bc8-4ea7-94b2-7d7a52ea5c47">Column Object</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>