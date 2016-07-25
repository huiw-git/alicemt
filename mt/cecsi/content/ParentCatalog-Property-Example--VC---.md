---
title: "ParentCatalog Property Example (VC++)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - C++
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 43ae202e-1972-4aab-9cc1-3b6612bad363
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
# ParentCatalog Property Example (VC++)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The following code demonstrates how to use the <legacyLink xlink:href="a0bb2ed8-d4cb-4f92-8de7-769bbe0e6273">ParentCatalog</legacyLink> property to access a provider-specific property prior to appending a table to a catalog. The property is <unmanagedCodeEntityReference>AutoIncrement</unmanagedCodeEntityReference>, which creates an AutoIncrement field in a Microsoft Jet database.</para>
    <code>// BeginCreateAutoIncrColumnCpp.cpp
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

   // Define and initialize ADOX object pointers. These are in ADODB namespace.
   _CatalogPtr m_pCatalog = NULL;
   _TablePtr m_pTable = NULL;

   // Define ADODB object pointers.
   ADODB::_ConnectionPtr m_pCnn = NULL;

   // Define string variables
   _bstr_t strCnn("Provider='Microsoft.JET.OLEDB.4.0';Data Source='c:\\Northwind.mdb';");

   try {
      TESTHR(hr = m_pCnn.CreateInstance(__uuidof(ADODB::Connection)));
      TESTHR(hr = m_pCatalog.CreateInstance(__uuidof (Catalog)));
      TESTHR(hr = m_pTable.CreateInstance(__uuidof (Table)));

      // Connect the catalog.
      m_pCnn-&gt;Open (strCnn, "", "", NULL);

      m_pCatalog-&gt;PutActiveConnection(variant_t((IDispatch *)m_pCnn));

      m_pTable-&gt;Name = "MyContacts";
      m_pTable-&gt;ParentCatalog = m_pCatalog;

      // Create fields and append them to the new Table object.
      m_pTable-&gt;Columns-&gt;Append("ContactId", adInteger,0);

      // Make the ContactId column and auto incrementing column
      m_pTable-&gt;Columns-&gt;GetItem("ContactId")-&gt;Properties-&gt;GetItem("AutoIncrement")-&gt;Value = true;
      m_pTable-&gt;Columns-&gt;Append("CustomerID", adVarWChar,0);
      m_pTable-&gt;Columns-&gt;Append("FirstName", adVarWChar,0);
      m_pTable-&gt;Columns-&gt;Append("LastName", adVarWChar,0);
      m_pTable-&gt;Columns-&gt;Append("Phone", adVarWChar, 20);
      m_pTable-&gt;Columns-&gt;Append("Notes", adLongVarWChar,0);
      m_pCatalog-&gt;Tables-&gt;Append(_variant_t((IDispatch*)m_pTable));

      // Refresh the database.
      m_pCatalog-&gt;Tables-&gt;Refresh();

      printf("Table 'MyContacts' is added.\n");

      // Delete new table, since this is only an example
      m_pCatalog-&gt;Tables-&gt;Delete("MyContacts");

      printf("Table 'MyContacts' is deleted.\n");
   }
   catch(_com_error &amp;e) {
      // Notify the user of errors if any.
      _bstr_t bstrSource(e.Source());
      _bstr_t bstrDescription(e.Description());

      printf("\n\tSource :  %s \n\tdescription : %s \n ", (LPCSTR)bstrSource, (LPCSTR)bstrDescription);
   }
   catch(...) {
      cout &lt;&lt; "Error occured in CreateAutoIncrColumnX...."&lt;&lt; endl;
   }

   m_pCatalog = NULL;
   ::CoUninitialize();
}</code>
  </introduction>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>