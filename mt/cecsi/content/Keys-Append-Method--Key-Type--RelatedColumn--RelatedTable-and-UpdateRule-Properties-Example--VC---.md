---
title: "Keys Append Method, Key Type, RelatedColumn, RelatedTable and UpdateRule Properties Example (VC++)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - C++
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 28495b8f-18dc-482c-995d-a120f6ae2006
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
# Keys Append Method, Key Type, RelatedColumn, RelatedTable and UpdateRule Properties Example (VC++)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The following code demonstrates how to create a new foreign key. It assumes two tables (Customers and Orders) exist.</para>
    <code>// BeginCreateKeyCpp.cpp
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

   // Define and initialize ADOX object pointers.  These are in ADODB namespace.
   _KeyPtr m_pKeyForeign = NULL; 
   _CatalogPtr m_pCatalog = NULL;

   // Define other variables
   _bstr_t strcnn("Provider='Microsoft.JET.OLEDB.4.0';Data source = 'c:\\Northwind.mdb';");

   try {
      TESTHR(hr = m_pKeyForeign.CreateInstance(__uuidof(Key)));
      TESTHR(hr = m_pCatalog.CreateInstance(__uuidof (Catalog)));
      m_pCatalog-&gt;PutActiveConnection(strcnn);

      // Define the foreign key.
      m_pKeyForeign-&gt;Name = "CustOrder";
      m_pKeyForeign-&gt;Type = adKeyForeign;
      m_pKeyForeign-&gt;RelatedTable = "Customers";
      m_pKeyForeign-&gt;Columns-&gt;Append("CustomerId",adVarWChar,0);
      m_pKeyForeign-&gt;Columns-&gt;GetItem("CustomerId")-&gt;RelatedColumn = "CustomerId";
      m_pKeyForeign-&gt;UpdateRule = adRICascade;

      // To pass as column parameter to Key's Apppend method
      _variant_t vOptional;
      vOptional.vt = VT_ERROR;
      vOptional.scode = DISP_E_PARAMNOTFOUND;

      // Append the foreign key.
      m_pCatalog-&gt;Tables-&gt;GetItem("Orders")-&gt;Keys-&gt;Append(_variant_t((IDispatch *)m_pKeyForeign),
         adKeyPrimary,
         vOptional,
         L"",
         L"");
      printf("Foreign key 'CustOrder' is added.\n");

      // Delete the key as this is a demonstration.
      m_pCatalog-&gt;Tables-&gt;GetItem("Orders")-&gt;Keys-&gt;Delete(m_pKeyForeign-&gt;Name);
      printf("Foreign key 'CustOrder' is deleted.\n");
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
   ::CoUninitialize();
}</code>
  </introduction>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>