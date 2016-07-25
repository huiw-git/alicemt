---
title: "GetPermissions and SetPermissions Methods Example (VC++)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - C++
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 8c75d547-d3d7-44c4-b7de-eead5d11b92e
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
# GetPermissions and SetPermissions Methods Example (VC++)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This example demonstrates the <legacyLink xlink:href="df201c1f-c76a-465d-98f0-83b7fc36e6e3">GetPermissions</legacyLink> and <legacyLink xlink:href="b7f925d7-b05c-4376-bb49-f8d2c17b8b24">SetPermissions</legacyLink> methods. The following code gives full access to the Orders table to the Admin user.</para>
    <code>// BeginGrantPermissionCpp.cpp
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

   // Define and initialize ADOX object pointers. These are in ADODB  namespace.
   _CatalogPtr m_pCatalog = NULL;

   // Define ADODB object pointers;
   ADODB::_ConnectionPtr m_pCnn = NULL;

   // Define other variables here.
   try {
      TESTHR(hr = m_pCnn.CreateInstance(__uuidof(ADODB::Connection)));

      // Opens a connection to the northwind database using the Microsoft Jet 4.0 provider
      m_pCnn-&gt;PutProvider("Microsoft.Jet.OLEDB.4.0");
      m_pCnn-&gt;Open("data source='c:\\Northwind.mdb';jet oledb:system database='c:\\system.mdw'", "", "", NULL);

      TESTHR(hr = m_pCatalog.CreateInstance(__uuidof(Catalog)));

      m_pCatalog-&gt;PutActiveConnection(_variant_t((IDispatch *)m_pCnn));

      // Retrieve original permissions
      long lngPerm = m_pCatalog-&gt;Users-&gt;GetItem("admin")-&gt;GetPermissions("Orders",adPermObjTable);
      long lngOrgPerm = lngPerm;
      cout &lt;&lt; "Original Permissions: " &lt;&lt; lngPerm &lt;&lt; "\n" &lt;&lt; endl;

      // Revoke all permissions
      m_pCatalog-&gt;Users-&gt;GetItem("admin")-&gt;SetPermissions("Orders", 
                                          adPermObjTable, adAccessRevoke, adRightFull, adInheritNone);

      // Display permissions
      lngPerm = m_pCatalog-&gt;Users-&gt;GetItem("admin")-&gt;GetPermissions("Orders", adPermObjTable);
      cout &lt;&lt; "Revoked permissions: " &lt;&lt; lngPerm &lt;&lt; "\n" &lt;&lt; endl;

      // Give the Admin user full rights on the orders object
      m_pCatalog-&gt;Users-&gt;GetItem("admin")-&gt;SetPermissions("Orders", 
                                            adPermObjTable, adAccessSet, adRightFull, adInheritNone);

      // Display permissions
      lngPerm = m_pCatalog-&gt;Users-&gt;GetItem("admin")-&gt;GetPermissions("Orders", adPermObjTable);
      cout &lt;&lt; "Full permissions: " &lt;&lt; lngPerm &lt;&lt; "\n" &lt;&lt; endl;

      // Restore original permissions
      m_pCatalog-&gt;Users-&gt;GetItem("admin")-&gt;SetPermissions("Orders", adPermObjTable,
                                                 adAccessSet, (RightsEnum) lngOrgPerm, adInheritNone);

      // Display permissions
      lngPerm = m_pCatalog-&gt;Users-&gt;GetItem("admin")-&gt;GetPermissions("Orders",adPermObjTable);
      cout &lt;&lt; "Final permissions: " &lt;&lt; lngPerm &lt;&lt; "\n" &lt;&lt; endl;
   }
   catch(_com_error &amp;e) {
      // Notify the user of errors if any.
      _bstr_t bstrSource(e.Source());
      _bstr_t bstrDescription(e.Description());

      printf("\n\tSource :  %s \n\tdescription : %s \n ", (LPCSTR)bstrSource, (LPCSTR)bstrDescription);
   }
   catch(...) {
      cout &lt;&lt; "Error occured in GrantPermissionsX...."&lt;&lt; endl;
   }
   ::CoUninitialize();
}</code>
  </introduction>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>