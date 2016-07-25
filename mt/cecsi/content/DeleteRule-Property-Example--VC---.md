---
title: "DeleteRule Property Example (VC++)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - C++
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7a1def31-2b6f-4542-aac3-ec35b54c89ef
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
# DeleteRule Property Example (VC++)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This example demonstrates the <legacyLink xlink:href="87bd4c0a-cae3-4007-a939-4193acaa00ac">DeleteRule</legacyLink> property of a <legacyLink xlink:href="55f116fe-4d56-4892-bffe-0cdd6fc727c9">Key</legacyLink> object. The code appends a new <legacyLink xlink:href="a6d74000-0828-49ba-850a-63da865f8802">Table</legacyLink> and then defines a new primary key, setting <legacyBold>DeleteRule</legacyBold> to <legacyBold>adRICascade</legacyBold>.</para>
    <code>// BeginDeleteRuleCpp.cpp
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

   // Define ADOX object pointers, initialize pointers. These are in ADODB namespace.
   _KeyPtr m_pKeyPrimary = NULL;
   _CatalogPtr m_pCatalog = NULL;
   _TablePtr m_pTblNew = NULL;

   // Define string variables.
   _bstr_t strcnn("Provider='Microsoft.JET.OLEDB.4.0';Data source = 'c:\\Northwind.mdb';");
   try {
      TESTHR(hr = m_pKeyPrimary.CreateInstance(__uuidof(Key)));
      TESTHR(hr = m_pCatalog.CreateInstance(__uuidof (Catalog)));
      TESTHR(hr = m_pTblNew.CreateInstance(__uuidof(Table)));

      // Connect the catalog.
      m_pCatalog-&gt;PutActiveConnection(strcnn);

      // Name new table.
      m_pTblNew-&gt;Name = "NewTable";

      // Append a numeric and a text field to new table.
      m_pTblNew-&gt;Columns-&gt;Append("NumField", adInteger, 20);
      m_pTblNew-&gt;Columns-&gt;Append("TextField", adVarWChar, 20);

      // Append the new table.
      m_pCatalog-&gt;Tables-&gt;Append(_variant_t((IDispatch*)m_pTblNew));
      printf("Table 'NewTable' is added.\n");

      // Define the Primary key.
      m_pKeyPrimary-&gt;Name = "NumField";
      m_pKeyPrimary-&gt;Type = adKeyPrimary;
      m_pKeyPrimary-&gt;RelatedTable = "Customers";
      m_pKeyPrimary-&gt;Columns-&gt;Append("NumField", adInteger,20);
      m_pKeyPrimary-&gt;Columns-&gt;GetItem("NumField")-&gt;RelatedColumn = "CustomerId";
      m_pKeyPrimary-&gt;DeleteRule = adRICascade;

      // to pass an optional column parameter to Key's Apppend method
      _variant_t vOptional;
      vOptional.vt = VT_ERROR;
      vOptional.scode = DISP_E_PARAMNOTFOUND;

      // Append the primary key.
      m_pCatalog-&gt;Tables-&gt;GetItem("NewTable")-&gt;Keys-&gt;Append( _variant_t((IDispatch*)m_pKeyPrimary), 
         adKeyPrimary,vOptional, 
         L"", 
         L"");

      // Delete the table as this is a demonstration.
      m_pCatalog-&gt;Tables-&gt;Delete(m_pTblNew-&gt;Name);
      printf("Table 'NewTable' is deleted.\n");
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
<link xlink:href="87bd4c0a-cae3-4007-a939-4193acaa00ac">DeleteRule Property</link>
<link xlink:href="55f116fe-4d56-4892-bffe-0cdd6fc727c9">Key Object</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>