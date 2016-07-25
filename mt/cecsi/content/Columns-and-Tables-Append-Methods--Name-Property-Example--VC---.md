---
title: "Columns and Tables Append Methods, Name Property Example (VC++)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - C++
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2b6dfef9-bcdf-483d-a164-2fa3ec81a43f
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
# Columns and Tables Append Methods, Name Property Example (VC++)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The following code demonstrates how to create a new table.</para>
    <code>// BeginCreateTableCpp.cpp
// compile with: /EHsc
#import "msadox.dll" no_namespace

#include "iostream"
using namespace std;

// Function declarations
inline void TESTHR(HRESULT x) {if FAILED(x) _com_issue_error(x);};

int main() {
   if ( FAILED(::CoInitialize(NULL) ) )
      return -1;

   HRESULT hr = S_OK;

   // Define ADOX object pointers, initialize pointers.  These are in ADOX namespace.
   _CatalogPtr m_pCatalog = NULL;
   _TablePtr m_pTable = NULL;

   try {
      TESTHR(hr = m_pCatalog.CreateInstance(__uuidof(Catalog)));

      // Open the catalog
      m_pCatalog-&gt;PutActiveConnection("Provider='Microsoft.JET.OLEDB.4.0';data source='c:\\Northwind.mdb';");

      TESTHR(hr = m_pTable.CreateInstance(__uuidof(Table)));
      m_pTable-&gt;PutName("MyTable");
      m_pTable-&gt;Columns-&gt;Append("Column1",adInteger,0);
      m_pTable-&gt;Columns-&gt;Append("Column2",adInteger,0);
      m_pTable-&gt;Columns-&gt;Append("Column3",adVarWChar,50);
      m_pCatalog-&gt;Tables-&gt;Append(_variant_t((IDispatch *)m_pTable));
      printf("Table 'MyTable' is added.\n");

      // Delete the table as this is a demonstration.
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
      cout &lt;&lt; "Error occured in include files...."&lt;&lt; endl;
   }

   ::CoUninitialize();
}</code>
  </introduction>
  <relatedTopics>
<link xlink:href="7a46d23c-efef-4ec7-815d-cd3ac86787dd">Append Method (Columns)</link>
<link xlink:href="a362ed51-314c-4783-9598-538dbf755f3d">Append Method (Tables)</link>
<link xlink:href="81b92baf-b6b9-4f4e-9f33-4503795518cd">Name Property</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>