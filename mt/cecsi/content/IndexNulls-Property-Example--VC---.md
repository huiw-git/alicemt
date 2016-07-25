---
title: "IndexNulls Property Example (VC++)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - C++
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ee407e03-4889-4a22-b031-ca542d637c96
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
# IndexNulls Property Example (VC++)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This example demonstrates the <legacyLink xlink:href="313b0bf7-3f37-4823-8fca-bd9c80e078a7">IndexNulls</legacyLink> property of an <legacyLink xlink:href="6b9578c0-bc94-46b9-b801-c18e14b04b31">Index</legacyLink>. The code creates a new index and sets the value of <legacyBold>IndexNulls</legacyBold> based on user input. Then, the <legacyBold>Index</legacyBold> is appended to the <legacyBold>Employees</legacyBold> <legacyLink xlink:href="a6d74000-0828-49ba-850a-63da865f8802">Table</legacyLink> in the <legacyItalic>Northwind</legacyItalic> <legacyLink xlink:href="bb651639-a488-4e38-b6de-0ed99fa4dd92">Catalog</legacyLink>. The new <legacyBold>Index</legacyBold> is applied to a <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink> based on the <legacyBold>Employees</legacyBold> table, and the <legacyBold>Recordset</legacyBold> is opened. A new record is added to the <legacyBold>Employees</legacyBold> table, with a <legacyBold>Null</legacyBold> value in the indexed field. Whether this new record is displayed depends on the setting of the <legacyBold>IndexNulls</legacyBold> property.</para>
    <code>// BeignIndexNullCpp.cpp
// compile with: /EHsc
#import "msado15.dll" rename("EOF", "EndOfFile")
#import "msadox.dll" no_namespace

#include "iostream"
#include "icrsint.h"
using namespace std;

// This class extracts LastName,Country,FirstName from Employees table
class CEmployeeRs : public CADORecordBinding {
   BEGIN_ADO_BINDING(CEmployeeRs)
      // Column LastName is the 2nd field in the table
      ADO_VARIABLE_LENGTH_ENTRY2(2, adVarChar, m_szemp_LastName, sizeof(m_szemp_LastName), lemp_LastNameStatus, TRUE)

      // Column Country is the 11th field in the table
      ADO_VARIABLE_LENGTH_ENTRY2(11, adVarChar, m_szemp_Country, sizeof(m_szemp_Country), lemp_CountryStatus, TRUE)

      // Column Country is the 17th field in the table
      ADO_VARIABLE_LENGTH_ENTRY2(17, adVarChar, m_szemp_FirstName, sizeof(m_szemp_FirstName), lemp_FirstNameStatus, TRUE)
      END_ADO_BINDING()

public:
   CHAR m_szemp_LastName[21];
   ULONG lemp_LastNameStatus;
   CHAR m_szemp_Country[16];
   ULONG lemp_CountryStatus;
   CHAR m_szemp_FirstName[11];
   ULONG lemp_FirstNameStatus;
};

// Function declarations
inline void TESTHR(HRESULT x) {if FAILED(x) _com_issue_error(x);};
void IndexNullsX(_bstr_t);

int main() {
   if ( FAILED(::CoInitialize(NULL)) )
      return -1; 

   printf("\nShow records having indexed field value = NULL? (Y/N):");
   // char input = getche();
   // Let's pretend you said Yes
   char input = 'Y';

   if ( toupper(input) == 'Y' )
      IndexNullsX("Allow");
   else if ( toupper(input) == 'N' )
      IndexNullsX("Ignore");
   else
      exit(0);

   ::CoUninitialize();
}

void IndexNullsX(_bstr_t strSel) {
   HRESULT hr = S_OK;

   // Define and initialie ADOX object pointers. These are in the ADODB namespace.
   _CatalogPtr m_pCatalog = NULL;
   _IndexPtr m_pIndexNew = NULL;

   // Define ADODB object pointers
   ADODB::_ConnectionPtr m_pCnn = NULL;
   ADODB::_RecordsetPtr m_pRstEmployees = NULL;

   // Define other variables
   IADORecordBinding *picRs = NULL;   // Interface Pointer Declared
   CEmployeeRs emprs;   // C++ Class Object

   // Define string variable.
   _bstr_t strCnn("Provider='Microsoft.JET.OLEDB.4.0';data source='c:\\Northwind.mdb';");

   try {
      TESTHR(hr = m_pCnn.CreateInstance(__uuidof(ADODB::Connection)));
      TESTHR(hr = m_pCatalog.CreateInstance(__uuidof (Catalog)));
      TESTHR(hr = m_pIndexNew.CreateInstance(__uuidof(Index)));
      TESTHR(hr = m_pRstEmployees.CreateInstance(__uuidof(ADODB::Recordset)));

      // Connect the catalog.
      m_pCnn-&gt;Open(strCnn, "", "", NULL);
      m_pCatalog-&gt;PutActiveConnection(_variant_t((IDispatch *)m_pCnn));

      // Append Country column to new index.
      m_pIndexNew-&gt;Columns-&gt;Append("Country", adVarWChar, 0);
      m_pIndexNew-&gt;Name = "NewIndex";

      // Set IndexNulls based on user input
      if (strcmp((LPSTR)strSel, "Allow") == 0 )
         m_pIndexNew-&gt;IndexNulls = adIndexNullsAllow;
      else if (strcmp((LPSTR)strSel, "Ignore") == 0 )
         m_pIndexNew-&gt;IndexNulls = adIndexNullsIgnore;

      // Append new index to Employees table
      m_pCatalog-&gt;Tables-&gt;GetItem("Employees")-&gt;Indexes-&gt;Append(_variant_t((IDispatch *)m_pIndexNew));
      m_pRstEmployees-&gt;Index = m_pIndexNew-&gt;Name;
      m_pRstEmployees-&gt;Open("Employees", 
         _variant_t((IDispatch *)m_pCnn), 
         ADODB::adOpenKeyset, 
         ADODB::adLockOptimistic,
         ADODB::adCmdTableDirect);

      // Add a new record to the Employees table.
      m_pRstEmployees-&gt;AddNew();
      m_pRstEmployees-&gt;Fields-&gt;GetItem("FirstName")-&gt;Value = (_bstr_t) "Gary";
      m_pRstEmployees-&gt;Fields-&gt;GetItem("LastName")-&gt;Value = (_bstr_t) "Haarsager";
      m_pRstEmployees-&gt;Update();

      // Bookmark the newly added record.
      _variant_t varBookmark = m_pRstEmployees-&gt;Bookmark;

      // Use the new index to set the order of the records.
      m_pRstEmployees-&gt;MoveFirst();
      printf("\n\nIndex = %s,", (LPSTR) m_pRstEmployees-&gt;Index);
      printf("IndexNulls = %d\n\n", m_pIndexNew-&gt;IndexNulls);
      cout&lt;&lt;"Country            -        Name" &lt;&lt; endl;

      // Open an IADORecordBinding interface pointer for binding Recordset to a class
      TESTHR(hr = m_pRstEmployees-&gt;QueryInterface(__uuidof(IADORecordBinding), (LPVOID*)&amp;picRs));

      // Bind the Recordset to a C++ class here 
      TESTHR(hr = picRs-&gt;BindToRecordset(&amp;emprs));

      // Enumerate the Recordset.The value of the IndexNulls property will determine if the newly
      // added record appears in the output.
      while ( !(m_pRstEmployees-&gt;EndOfFile) ) {
         printf("%s    -    %s %s\n",
            emprs.lemp_CountryStatus == adFldOK ? emprs.m_szemp_Country :"[Null]",
            emprs.lemp_FirstNameStatus == adFldOK ? emprs.m_szemp_FirstName :"&lt;NULL&gt;",
            emprs.lemp_LastNameStatus == adFldOK ? emprs.m_szemp_LastName :"&lt;NULL&gt;");

         m_pRstEmployees-&gt;MoveNext();
      }

      // Delete new record because this is a demonstration.
      m_pRstEmployees-&gt;Bookmark = varBookmark;
      m_pRstEmployees-&gt;Delete(ADODB::adAffectCurrent);
   }
   catch(_com_error &amp;e) {
      // Notify the user of errors if any.
      _bstr_t bstrSource(e.Source());
      _bstr_t bstrDescription(e.Description());
      printf("\n\tSource :  %s \n\tdescription : %s \n ", (LPCSTR)bstrSource, (LPCSTR)bstrDescription);
   }
   catch(...) {
      cout &lt;&lt; "Error occured in include files...." &lt;&lt; endl;
   }

   if (m_pRstEmployees)
      if (m_pRstEmployees-&gt;State == 1) {
         m_pRstEmployees-&gt;Close();
         m_pRstEmployees = NULL;
      }

      // Delete new Index because this is a demonstration.
      if (m_pCatalog)
         m_pCatalog-&gt;Tables-&gt;GetItem("Employees")-&gt;Indexes-&gt;Delete(m_pIndexNew-&gt;Name);

      if (m_pCnn)
         if (m_pCnn-&gt;State == 1) {
            m_pCnn-&gt;Close();
            m_pCnn = NULL;
         }

         m_pCatalog = NULL;
}</code>
  </introduction>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>