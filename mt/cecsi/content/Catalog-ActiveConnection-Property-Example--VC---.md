---
title: "Catalog ActiveConnection Property Example (VC++)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - C++
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 518905a9-6044-4194-af6c-84952d95939d
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
# Catalog ActiveConnection Property Example (VC++)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Setting the <legacyLink xlink:href="25fff69b-7556-4a28-b6f5-600a4bb0f607">ActiveConnection</legacyLink> property to a valid, open connection "opens" the catalog. From an open catalog, you can access the schema objects contained within that catalog.</para>
    <code>// CatalogActiveConnectionCpp.cpp
// compile with: /EHsc
#import "msado15.dll" rename("EOF", "EndOfFile")
#import "msadox.dll" no_namespace

#include "iostream"
using namespace std;

// Function declarations
inline void TESTHR(HRESULT x) {if FAILED(x) _com_issue_error(x);};
void OpenConnectionX();
void OpenConnectionWithStringX();

int main() {
   if ( FAILED( ::CoInitialize(NULL) ) )
      return -1;

   OpenConnectionX();
   OpenConnectionWithStringX();
   ::CoUninitialize();
}

void OpenConnectionX() {
   HRESULT hr = S_OK;

   // Define ADOX object pointers, initialize pointers. These are in ADODB namespace.
   _CatalogPtr m_pCatalog = NULL;

   // Define ADODB object pointers
   ADODB::_ConnectionPtr m_pCnn = NULL;

   // Define string variables.
   _bstr_t strcnn("Provider='Microsoft.JET.OLEDB.4.0';Data source = 'c:\\Northwind.mdb';");

   try {
      TESTHR(hr = m_pCnn.CreateInstance(__uuidof(ADODB::Connection)));
      TESTHR(hr = m_pCatalog.CreateInstance(__uuidof (Catalog)));
      m_pCnn-&gt;Open(strcnn, "", "", NULL);
      m_pCatalog-&gt;PutActiveConnection(_variant_t((IDispatch *) m_pCnn));
      _variant_t vIndex = (short) 0;
      cout&lt;&lt;m_pCatalog-&gt;Tables-&gt;GetItem(vIndex)-&gt;Type&lt;&lt;endl;
   }
   catch(_com_error &amp;e) {
      // Notify the user of errors if any.
      _bstr_t bstrSource(e.Source());
      _bstr_t bstrDescription(e.Description());

      printf("\n\tSource :  %s \n\tdescription : %s \n ", (LPCSTR)bstrSource, (LPCSTR)bstrDescription);
   }
   catch(...) {
      cout &lt;&lt; "Error occured in OpenConnectionX...." &lt;&lt; endl;
   }

   if (m_pCnn)
      if (m_pCnn-&gt;State == 1)
         m_pCnn-&gt;Close();
}

void OpenConnectionWithStringX() {
   HRESULT hr = S_OK;

   // Define ADOX object pointers, initialize pointers. These are in ADODB namespace.
   _CatalogPtr m_pCatalog = NULL;

   // Define string variables.
   _bstr_t strcnn("Provider='Microsoft.JET.OLEDB.4.0';Data source = 'c:\\Northwind.mdb';");

   try {
      TESTHR(hr = m_pCatalog.CreateInstance(__uuidof (Catalog)));
      m_pCatalog-&gt;PutActiveConnection(strcnn);
      _variant_t vIndex = (short) 0;
      cout&lt;&lt;m_pCatalog-&gt;Tables-&gt;GetItem(vIndex)-&gt;Type&lt;&lt;endl;
   }
   catch(_com_error &amp;e) {
      // Notify the user of errors if any.
      _bstr_t bstrSource(e.Source());
      _bstr_t bstrDescription(e.Description());

      printf("\n\tSource :  %s \n\tdescription : %s \n ", (LPCSTR)bstrSource, (LPCSTR)bstrDescription);
   }
   catch(...) {
      cout &lt;&lt; "Error occured in OpenConnectionWithStringX...." &lt;&lt; endl;
   }
}</code>
  </introduction>
  <relatedTopics>
<link xlink:href="25fff69b-7556-4a28-b6f5-600a4bb0f607">ActiveConnection Property</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>