---
title: "Indexes Append Method Example (VC++)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - C++
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 33c559c4-4db7-4850-9309-2743a7ae5521
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
# Indexes Append Method Example (VC++)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The following code demonstrates how to create a new index. The index is on two columns in the table.</para>
    <code>// BeginCreateIndexCpp.cpp
// compile with: /EHsc
#import "msadox.dll" no_namespace

#include "iostream"
using namespace std;

// Function declarations
inline void TESTHR(HRESULT x) {if FAILED(x) _com_issue_error(x);};

int main() {
   if ( FAILED(::CoInitialize(NULL)) )
      return -1;

   HRESULT hr = S_OK;

   // Define and initialize ADOX object pointers.  These are in ADODB namespace.
   _TablePtr m_pTable = NULL;
   _IndexPtr m_pIndex = NULL;
   _CatalogPtr m_pCatalog = NULL;

   // Define other variables
   _bstr_t strcnn("Provider='Microsoft.JET.OLEDB.4.0';Data source = 'c:\\Northwind.mdb';");
   try {
      TESTHR(hr = m_pTable.CreateInstance(__uuidof(Table)));
      TESTHR(hr = m_pIndex.CreateInstance(__uuidof(Index)));
      TESTHR(hr = m_pCatalog.CreateInstance(__uuidof (Catalog)));

      // Open the catalog.
      m_pCatalog-&gt;PutActiveConnection(strcnn);

      // Define the table and append it to the catalog.
      m_pTable-&gt;Name = "MyTable";
      m_pTable-&gt;Columns-&gt;Append("Column1", adInteger,0);
      m_pTable-&gt;Columns-&gt;Append("Column2", adInteger,0);
      m_pTable-&gt;Columns-&gt;Append("Column3", adVarWChar,50);
      m_pCatalog-&gt;Tables-&gt;Append(_variant_t((IDispatch *)m_pTable));
      printf("Table 'MyTable' is appended.\n");

      // Define a multi-column index.
      m_pIndex-&gt;Name = "multicolidx";
      m_pIndex-&gt;Columns-&gt;Append("Column1", adInteger,0);
      m_pIndex-&gt;Columns-&gt;Append("Column2", adInteger,0);

      // Append the index to the table.
      m_pTable-&gt;Indexes-&gt;Append(_variant_t((IDispatch *)m_pIndex));
      printf("Index 'multicolidx' is appended.\n");

      // Delete the table.
      m_pCatalog-&gt;Tables-&gt;Delete("MyTable");
      printf("Table 'MyTable' is deleted.\n");
   }
   catch(_com_error &amp;e) {
      // Notify the user of errors if any.
      _bstr_t bstrSource(e.Source());
      _bstr_t bstrDescription(e.Description());

      printf("\n\tSource :  %s \n\tdescription : %s \n ", (LPCSTR)bstrSource, (LPCSTR)bstrDescription);
   }
   catch(...) {
      cout &lt;&lt; "Error occured in CreateIndexX...." &lt;&lt; endl;
   }
   ::CoUninitialize();
}</code>
  </introduction>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>