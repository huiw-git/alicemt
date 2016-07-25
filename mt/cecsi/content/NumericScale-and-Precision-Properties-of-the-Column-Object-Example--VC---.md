---
title: "NumericScale and Precision Properties of the Column Object Example (VC++)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - C++
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 69653366-ebd7-4ff6-a654-761772223b0c
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
# NumericScale and Precision Properties of the Column Object Example (VC++)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This example demonstrates the <legacyLink xlink:href="573ee5d1-57c7-4a27-be79-a0e12944ad9b">NumericScale</legacyLink> and <legacyLink xlink:href="0e0ecbbf-d7de-49d4-a128-5a519ecd54ba">Precision</legacyLink> properties of the <legacyLink xlink:href="6e772783-1bc8-4ea7-94b2-7d7a52ea5c47">Column</legacyLink> object. This code displays their value for the <legacyBold>Order Details</legacyBold> table of the <legacyItalic>Northwind</legacyItalic> database.</para>
    <code>// BeginNumericScalePrecCpp.cpp
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
   _ColumnPtr m_pColumn = NULL;

   // Define ADODB object pointers
   ADODB::_ConnectionPtr m_pCnn = NULL;

   // Declare string variables
   _bstr_t strCnn("Provider='Microsoft.JET.OLEDB.4.0';Data Source='c:\\Northwind.mdb';");

   try {
      TESTHR(hr = m_pCnn.CreateInstance(__uuidof(ADODB::Connection)));

      TESTHR(hr = m_pCatalog.CreateInstance(__uuidof (Catalog)));

      // Connect the catalog.
      m_pCnn-&gt;Open (strCnn, "", "", NULL);

      m_pCatalog-&gt;PutActiveConnection(variant_t((IDispatch *)m_pCnn));

      // Retrieve the Order Details table
      m_pTable = m_pCatalog-&gt;Tables-&gt;GetItem("Order Details");

      // Display numeric scale and precision of small integer fields.
      _variant_t vIndex;
      for ( long lIndex = 0 ; lIndex &lt; m_pTable-&gt;Columns-&gt;Count ; lIndex++ ) {
         vIndex = lIndex ;
         m_pColumn = m_pTable-&gt;Columns-&gt;GetItem(vIndex);
         if (m_pColumn-&gt;Type == adSmallInt) {
            cout &lt;&lt; "Column: " &lt;&lt; m_pColumn-&gt;GetName() &lt;&lt; endl;
            cout &lt;&lt; "Numeric scale: " &lt;&lt; (_bstr_t) m_pColumn-&gt;GetNumericScale() &lt;&lt; endl;
            cout &lt;&lt; "Precision: " &lt;&lt; m_pColumn-&gt;GetPrecision() &lt;&lt; endl;
         }
      }
   }
   catch(_com_error &amp;e) {
      // Notify the user of errors if any.
      _bstr_t bstrSource(e.Source());
      _bstr_t bstrDescription(e.Description());

      printf("\n\tSource :  %s \n\tdescription : %s \n ", (LPCSTR)bstrSource, (LPCSTR)bstrDescription);
   }
   catch(...) {
      cout &lt;&lt; "Error occured in NumericScalePrecX...." &lt;&lt; endl;
   }
   ::CoUninitialize();
}</code>
  </introduction>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>