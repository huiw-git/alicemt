---
title: "Connection Close Method, Table Type Property Example (VC++)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - C++
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d0e250aa-fc57-4fd3-9610-d64f50c5507f
caps.latest.revision: 12
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
# Connection Close Method, Table Type Property Example (VC++)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Setting the <legacyLink xlink:href="25fff69b-7556-4a28-b6f5-600a4bb0f607">ActiveConnection</legacyLink> property to <legacyBold>Nothing</legacyBold> should "close" the catalog. Associated collections will be empty. Any objects that were created from schema objects in the catalog will be orphaned. Any properties on those objects that have been cached will still be available, but attempting to read properties that require a call to the provider will fail.</para>
    <code>// BeginCloseConnectionCpp.cpp
// compile with: /EHsc
#import "msado15.dll" rename("EOF", "EndOfFile")
#import "msadox.dll" no_namespace

#include "iostream"
using namespace std;

// Function declarations
inline void TESTHR(HRESULT x) {if FAILED(x) _com_issue_error(x);};
void CloseConnectionByNothingX();
void CloseConnectionX();

int main() {
   if ( FAILED(::CoInitialize(NULL) ) )
      return -1;

   CloseConnectionByNothingX();
   CloseConnectionX();

   ::CoUninitialize();
}

void CloseConnectionByNothingX() {
   HRESULT hr = S_OK;

   // Define and initialize ADOX object pointers, in ADODB namespace.
   _CatalogPtr m_pCatalog = NULL;
   _TablePtr m_pTable = NULL;

   // Define ADODB object pointers
   ADODB::_ConnectionPtr m_pCnn = NULL;

   // Define other variables
   _variant_t vIndex = (short) 0;

   try {
      TESTHR(hr = m_pCnn.CreateInstance(__uuidof(ADODB::Connection)));
      TESTHR(hr = m_pCatalog.CreateInstance(__uuidof(Catalog)));

      m_pCnn-&gt;Open("Provider='Microsoft.JET.OLEDB.4.0';Data Source= 'c:\\Northwind.mdb';", "", "", NULL);
      m_pCatalog-&gt;PutActiveConnection(_variant_t((IDispatch *)m_pCnn));
      m_pTable = m_pCatalog-&gt;Tables-&gt;GetItem(vIndex);

      // Cache m_pTable.Type info
      cout &lt;&lt; m_pTable-&gt;Type &lt;&lt; endl;

      _variant_t vCnn;
      vCnn.vt = VT_DISPATCH;
      vCnn.pdispVal = NULL;
      m_pCatalog-&gt;PutActiveConnection(vCnn);

      // m_pTable is orphaned, will succeed if this was cached
      cout &lt;&lt; m_pTable-&gt;Type &lt;&lt; endl;

      cout &lt;&lt; m_pTable-&gt;Columns-&gt;GetItem(vIndex)-&gt;DefinedSize &lt;&lt; endl;
      // Previous line will fail if this info has not been cached
   }
   catch(_com_error &amp;e) {
      // Notify the user of errors if any.
      _bstr_t bstrSource(e.Source());
      _bstr_t bstrDescription(e.Description());

      printf("\nError\n\tSource :  %s \n\tdescription : %s \n", (LPCSTR)bstrSource, (LPCSTR)bstrDescription);
   }
   catch(...) {
      cout &lt;&lt; "Error occured in CloseConnectionByNothingX...." &lt;&lt; endl;
   }
}

void CloseConnectionX() {
   HRESULT hr = S_OK;

   // Define ADOX object pointers, initialize pointers. These are in ADODB  namespace.

   _CatalogPtr m_pCatalog = NULL;
   _TablePtr m_pTable = NULL;

   // Define ADODB object pointers
   ADODB::_ConnectionPtr m_pCnn = NULL;

   // Define other variables
   _variant_t vIndex = (short) 0;
   try {
      TESTHR(hr = m_pCnn.CreateInstance(__uuidof(ADODB::Connection)));
      m_pCnn-&gt;Open("Provider='Microsoft.JET.OLEDB.4.0';Data Source= 'c:\\Northwind.mdb';", "", "", NULL);

      TESTHR(hr = m_pCatalog.CreateInstance(__uuidof(Catalog)));
      m_pCatalog-&gt;PutActiveConnection(_variant_t((IDispatch *)m_pCnn));

      m_pTable = m_pCatalog-&gt;Tables-&gt;GetItem(vIndex);

      // Cache m_pTable.Type info
      cout &lt;&lt; m_pTable-&gt;Type &lt;&lt; endl;

      m_pCnn-&gt;Close();

      // m_pTable is orphaned, will succeed if this was cached
      cout &lt;&lt; m_pTable-&gt;Type &lt;&lt; endl;

      cout &lt;&lt; m_pTable-&gt;Columns-&gt;GetItem(vIndex)-&gt;DefinedSize &lt;&lt; endl;
      // Previous line will fail if this info has not been cached
   }
   catch(_com_error &amp;e) {
      // Notify the user of errors if any.
      _bstr_t bstrSource(e.Source());
      _bstr_t bstrDescription(e.Description());

      printf("\nError\n\tSource :  %s \n\tdescription : %s \n", (LPCSTR)bstrSource, (LPCSTR)bstrDescription);
   }
   catch(...) {
      cout &lt;&lt; "Error occured in CloseConnectionX...." &lt;&lt; endl;
   }
}</code>
  </introduction>
  <relatedTopics>
<link xlink:href="25fff69b-7556-4a28-b6f5-600a4bb0f607">ActiveConnection Property</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>