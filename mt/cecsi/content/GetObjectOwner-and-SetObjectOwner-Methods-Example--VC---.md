---
title: "GetObjectOwner and SetObjectOwner Methods Example (VC++)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - C++
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f5f2aa4b-d790-458f-9e70-1643e3e203b2
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
# GetObjectOwner and SetObjectOwner Methods Example (VC++)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This example demonstrates the <legacyLink xlink:href="8965adf0-9075-4125-8142-73eb700029c3">GetObjectOwner</legacyLink> and <legacyLink xlink:href="e5170a37-9d6e-43db-bfb6-9b6631fa3048">SetObjectOwner</legacyLink> methods. This code assumes the existence of the group Accounting (see the <legacyLink xlink:href="7e7067d0-6405-4c09-bff3-b1c2f2d783e0">Groups and Users Append, ChangePassword Methods Example (VC++)</legacyLink> to see how to add this group to the system). The owner of the Categories table is set to Accounting.</para>
    <code>// BeginOwnersCpp.cpp
// compile with: /EHsc
#import "msadox.dll" no_namespace

#include "iostream"
using namespace std;

inline void TESTHR(HRESULT x) {if FAILED(x) _com_issue_error(x);};

int main() {
   if ( FAILED(::CoInitialize(NULL)) )
      return -1;

   HRESULT hr = S_OK;

   // Define and initialize ADOX object pointers. These are in the ADODB namespace.
   _TablePtr m_pTable = NULL;
   _CatalogPtr m_pCatalog = NULL;

   try {
      TESTHR(hr = m_pCatalog.CreateInstance(__uuidof(Catalog)));
      TESTHR(hr = m_pTable.CreateInstance(__uuidof(Table)));

      // Open the Catalog.
      m_pCatalog-&gt;PutActiveConnection("Provider='Microsoft.JET.OLEDB.4.0';data source='c:\\Northwind.mdb';jet oledb:system database='c:\\system.mdw'");

      // Print the original owner of Categories
      _bstr_t strOwner = m_pCatalog-&gt;GetObjectOwner("Categories", adPermObjTable);
      cout &lt;&lt; "Owner of Categories: " &lt;&lt; strOwner &lt;&lt; "\n" &lt;&lt; endl;

      //Create and append new group with a string.
      m_pCatalog-&gt;Groups-&gt;Append("Accounting");

      //Set the owner of Categories to Accounting.
      m_pCatalog-&gt;SetObjectOwner("Categories", adPermObjTable, "Accounting");

      _variant_t vIndex;
      // List the owners of all tables and columns in the catalog.
      for ( long iIndex = 0 ; iIndex &lt; m_pCatalog-&gt;Tables-&gt;Count ; iIndex++ ) {
         vIndex = iIndex;
         m_pTable = m_pCatalog-&gt;Tables-&gt;GetItem(vIndex);
         cout &lt;&lt; "Table: " &lt;&lt; m_pTable-&gt;Name &lt;&lt; endl;
         cout &lt;&lt; "   Owner: " &lt;&lt; m_pCatalog-&gt;GetObjectOwner(m_pTable-&gt;Name, adPermObjTable) &lt;&lt; endl;
      }

      // Restore the original owner of Categories
      m_pCatalog-&gt;SetObjectOwner("Categories", adPermObjTable, strOwner);

      // Delete Accounting
      m_pCatalog-&gt;Groups-&gt;Delete("Accounting");
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