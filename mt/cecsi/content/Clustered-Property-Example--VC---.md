---
title: "Clustered Property Example (VC++)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - C++
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b993e357-3e2e-48a7-a627-76909160c97f
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
# Clustered Property Example (VC++)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This example demonstrates the <legacyLink xlink:href="9b62fb35-de43-425a-83ca-77af4e33fea9">Clustered</legacyLink> property of an <legacyLink xlink:href="6b9578c0-bc94-46b9-b801-c18e14b04b31">Index</legacyLink>. Note that Microsoft Jet databases do not support clustered indexes, so this example will return <legacyBold>False</legacyBold> for the <legacyBold>Clustered</legacyBold> property of all indexes in the <legacyItalic>Northwind</legacyItalic> database.</para>
    <code>// BeginClusteredCpp.cpp
// compile with: /EHsc
#import "msadox.dll" no_namespace

#include "iostream"
using namespace std;

// Function declarations
inline void TESTHR(HRESULT x) {if FAILED(x) _com_issue_error(x);};
void ClusteredX();

int main() {
   if ( FAILED(::CoInitialize(NULL) ) )
      return -1;

   ClusteredX();
   ::CoUninitialize();
}

void ClusteredX() {
   HRESULT hr = S_OK;

   // Define ADOX object pointers, initialize pointers. These are in ADODB namespace.
   _CatalogPtr m_pCatalog = NULL;
   _TablePtr m_pTable = NULL;
   _IndexPtr m_pIndex = NULL;

   // Define other variables here
   _variant_t vIndex;
   try {
      TESTHR(hr = m_pCatalog.CreateInstance(__uuidof(Catalog)));

      // Connect to the catalog.
      m_pCatalog-&gt;PutActiveConnection("Provider='Microsoft.JET.OLEDB.4.0';data source='c:\\Northwind.mdb';");

      // Enumerate Tables.
      for (short iTable = 0 ; iTable &lt; m_pCatalog-&gt;Tables-&gt;Count ; iTable++ ) {
         vIndex = iTable;
         m_pTable = m_pCatalog-&gt;Tables-&gt;GetItem(vIndex);

         // Enumerate Indexes.
         for (short iIndex = 0 ; iIndex &lt; m_pTable-&gt;Indexes-&gt;Count ; iIndex++) {
            vIndex = iIndex;
            m_pIndex = m_pTable-&gt;Indexes-&gt;GetItem(vIndex);
            cout &lt;&lt; m_pTable-&gt;Name &lt;&lt; "   " ;
            cout &lt;&lt; m_pIndex-&gt;Name &lt;&lt; "   " &lt;&lt; (m_pIndex-&gt;GetClustered() ? "True" : "False") &lt;&lt; endl;
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
      cout &lt;&lt; "Error occured in ClusteredX...."&lt;&lt; endl;
   }
}</code>
  </introduction>
  <relatedTopics>
<link xlink:href="9b62fb35-de43-425a-83ca-77af4e33fea9">Clustered Property</link>
<link xlink:href="6b9578c0-bc94-46b9-b801-c18e14b04b31">Index Object</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>