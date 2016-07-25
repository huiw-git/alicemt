---
title: "DefinedSize Property Example (VC++)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - C++
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: cc752ae4-58c4-4a7b-bfb2-0454e90fe2e7
caps.latest.revision: 9
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
# DefinedSize Property Example (VC++)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This example demonstrates the <legacyLink xlink:href="762b8937-c31c-4e90-bb85-506d991e8280">DefinedSize</legacyLink> property of a <legacyLink xlink:href="6e772783-1bc8-4ea7-94b2-7d7a52ea5c47">Column</legacyLink>. The code will redefine the size of the FirstName column of the <legacyBold>Employees</legacyBold> table of the <legacyItalic>Northwind</legacyItalic> database. Then, the change in the values of the FirstName <legacyLink xlink:href="b10a72fc-3c4b-4186-a70b-993dc9f7a092">Field</legacyLink> of a <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink> based on the <legacyBold>Employees</legacyBold> table is displayed. Note that by default, the FirstName field becomes padded with spaces after you redefine the <legacyBold>DefinedSize</legacyBold> property.</para>
    <code>// BeginDefinedSizeCpp.cpp
// compile with: /EHsc
#import "msado15.dll" rename("EOF", "EndOfFile")
#import "msadox.dll" no_namespace

#include "iostream"
using namespace std;

inline void TESTHR(HRESULT x) {if FAILED(x) _com_issue_error(x);};

int main() {
   if ( FAILED(::CoInitialize(NULL)) )
      return -1;

   HRESULT hr = S_OK;

   // Define ADOX object pointers, initialize pointers. These are in the ADODB namespace.
   _CatalogPtr m_pCatNorthwind = NULL;
   _ColumnPtr m_pColFirstName = NULL;
   _ColumnPtr m_pColNewFirstName = NULL;

   // Define ADODB object pointers
   ADODB::_RecordsetPtr m_pRstEmployees = NULL;

   // Define string variables.
   _bstr_t strCnn("Provider='Microsoft.JET.OLEDB.4.0';data source='c:\\Northwind.mdb';");
   _bstr_t aryFirstName[10];

   try {
      // Open a Recordset for the Employees table.
      TESTHR(hr = m_pRstEmployees.CreateInstance(__uuidof(ADODB::Recordset)));
      TESTHR(hr = m_pCatNorthwind.CreateInstance(__uuidof (Catalog)));
      TESTHR(hr = m_pColNewFirstName.CreateInstance(__uuidof(Column)));

      m_pRstEmployees-&gt;Open("Employees", strCnn,ADODB::adOpenKeyset, ADODB::adLockReadOnly, ADODB::adCmdTable);

      long lngSize = m_pRstEmployees-&gt;RecordCount;
      aryFirstName[lngSize];

      // Open a catalog for the Northwind database, using same connection as rstEmployees.
      m_pCatNorthwind-&gt;PutActiveConnection(m_pRstEmployees-&gt;GetActiveConnection());

      // Loop through the recordset displaying the contents, of the FirstName field, the field's defined size,
      // and its actual size.  Also store FirstName values in aryFirstName array.
      m_pRstEmployees-&gt;MoveFirst();
      printf("\nOriginal Defined Size and Actual Size");
      int iCount = 0;
      while (!(m_pRstEmployees-&gt;EndOfFile)) {
         printf("\nEmployee Name:");
         printf("%s ", (LPSTR)(_bstr_t)m_pRstEmployees-&gt;Fields-&gt;GetItem("FirstName")-&gt;Value);
         printf("%s\n", (LPSTR)(_bstr_t)m_pRstEmployees-&gt;Fields-&gt;GetItem("LastName")-&gt;Value);
         printf("  FirstName Defined size: %d\n", m_pRstEmployees-&gt;Fields-&gt;GetItem("FirstName")-&gt;DefinedSize);
         printf("  FirstName Actual size: %d\n", m_pRstEmployees-&gt;Fields-&gt;GetItem("FirstName")-&gt;ActualSize);
         aryFirstName[iCount] = (_bstr_t) m_pRstEmployees-&gt;Fields-&gt;GetItem("FirstName")-&gt;Value;
         m_pRstEmployees-&gt;MoveNext();
      }
      m_pRstEmployees-&gt;Close();

      // Redefine the DefinedSize of FirstName in the catalog.
      m_pColFirstName = m_pCatNorthwind-&gt;Tables-&gt;GetItem("Employees")-&gt;Columns-&gt;GetItem("FirstName");
      m_pColNewFirstName-&gt;Name = m_pColFirstName-&gt;Name;
      m_pColNewFirstName-&gt;Type = m_pColFirstName-&gt;Type;
      m_pColNewFirstName-&gt;DefinedSize = (m_pColFirstName-&gt;DefinedSize) + 1;

      // Append new FirstName column to catalog.
      m_pCatNorthwind-&gt;Tables-&gt;GetItem("Employees")-&gt;Columns-&gt;Delete(m_pColFirstName-&gt;Name);
      m_pCatNorthwind-&gt;Tables-&gt;GetItem("Employees")-&gt;Columns-&gt;Append(_variant_t((IDispatch*)m_pColNewFirstName, true), 
         adVarWChar,
         m_pColNewFirstName-&gt;DefinedSize);

      // Open Employee table in Recordset for updating.
      m_pRstEmployees-&gt;Open("Employees",
         m_pCatNorthwind-&gt;GetActiveConnection(), 
         ADODB::adOpenKeyset,
         ADODB::adLockOptimistic,
         ADODB::adCmdTable);

      // Loop through the recordset displaying the contents of the FirstName field,the field's defined size,
      // and its actual size. Also restore FirstName values from aryFirstName.
      m_pRstEmployees-&gt;MoveFirst();
      printf("\n\nNew Defined Size and Actual Size");
      iCount = 0;
      while (!(m_pRstEmployees-&gt;EndOfFile)) {
         m_pRstEmployees-&gt;Fields-&gt;GetItem("FirstName")-&gt;Value = aryFirstName[iCount];
         printf("\nEmployee Name: ");
         printf("%s ", (LPSTR) (_bstr_t)m_pRstEmployees-&gt;Fields-&gt;GetItem("FirstName")-&gt;Value);
         printf("%s\n", (LPSTR)(_bstr_t)m_pRstEmployees-&gt;Fields-&gt;GetItem("LastName")-&gt;Value);
         printf("  FirstName Defined size: %d\n", m_pRstEmployees-&gt;Fields-&gt;GetItem("FirstName")-&gt;DefinedSize);
         printf("  FirstName Actual size: %d\n", m_pRstEmployees-&gt;Fields-&gt;GetItem("FirstName")-&gt;ActualSize);
         m_pRstEmployees-&gt;MoveNext();
      }
      m_pRstEmployees-&gt;Close();

      // Restore original FirstName column to catalog
      m_pCatNorthwind-&gt;Tables-&gt;GetItem("Employees")-&gt;Columns-&gt;Delete(m_pColNewFirstName-&gt;Name);

      m_pCatNorthwind-&gt;Tables-&gt;GetItem("Employees")-&gt;Columns-&gt;Append(_variant_t((IDispatch*)m_pColFirstName, 
         true), 
         adVarWChar,
         m_pColFirstName-&gt;DefinedSize);

      // Restore original FirstName values to Employees table.
      m_pRstEmployees-&gt;Open("Employees", 
         m_pCatNorthwind-&gt;GetActiveConnection(), 
         ADODB::adOpenKeyset, 
         ADODB::adLockOptimistic,
         ADODB::adCmdTable);

      m_pRstEmployees-&gt;MoveFirst();
      iCount = 0;
      while ( !(m_pRstEmployees-&gt;EndOfFile) ) {
         m_pRstEmployees-&gt;Fields-&gt;GetItem("FirstName")-&gt;Value = aryFirstName[iCount];
         m_pRstEmployees-&gt;MoveNext();
         iCount++;
      }
   }
   catch(_com_error &amp;e) {
      // Notify the user of errors if any.
      _bstr_t bstrSource(e.Source());
      _bstr_t bstrDescription(e.Description());

      printf("\n\tSource :  %s \n\tdescription : %s \n ", (LPCSTR)bstrSource, (LPCSTR)bstrDescription);
   }
   catch(...) {
      cout &lt;&lt; "Error occured in DefinedSizeX...." &lt;&lt; endl;
   }

   if (m_pRstEmployees)
      if (m_pRstEmployees-&gt;State == 1)
         m_pRstEmployees-&gt;Close();

   m_pCatNorthwind = NULL;

   ::CoUninitialize();
}</code>
  </introduction>
  <relatedTopics>
<link xlink:href="6e772783-1bc8-4ea7-94b2-7d7a52ea5c47">Column Object</link>
<link xlink:href="762b8937-c31c-4e90-bb85-506d991e8280">DefinedSize Property</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>