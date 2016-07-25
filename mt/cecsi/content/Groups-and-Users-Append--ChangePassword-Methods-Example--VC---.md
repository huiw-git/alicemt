---
title: "Groups and Users Append, ChangePassword Methods Example (VC++)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - C++
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7e7067d0-6405-4c09-bff3-b1c2f2d783e0
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
# Groups and Users Append, ChangePassword Methods Example (VC++)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This example demonstrates the <legacyLink xlink:href="56b94fc6-7ef0-4e4a-82a3-033b94c46036">Append</legacyLink> method of <legacyLink xlink:href="09aa7b0a-69d5-4564-80a7-20ad8189670f">Groups</legacyLink>, as well as the <legacyLink xlink:href="b80bc5d5-78ca-4f75-956b-2ac658029cc7">Append</legacyLink> method of <legacyLink xlink:href="0a30fa74-6f10-4410-bd70-882e7c43cd46">Users</legacyLink> by adding a new <legacyLink xlink:href="55ef0ade-68ea-4da5-8aa5-4cd27d1f6d1e">Group</legacyLink> and a new <legacyLink xlink:href="f68e32ce-ef7c-407d-bdb5-d280947ae0e2">User</legacyLink> to the system. The new <legacyBold>Group</legacyBold> is appended to the <legacyBold>Groups</legacyBold> collection of the new <legacyBold>User</legacyBold>. Consequently, the new <legacyBold>User</legacyBold> is added to the <legacyBold>Group</legacyBold>. Also, the <legacyLink xlink:href="d187fbc6-5fac-4abb-803d-bf344dcf0302">ChangePassword</legacyLink> method is used to specify the <legacyBold>User</legacyBold> password.</para>
    <alert class="note">
      <para>If you are connecting to a data source provider that supports Windows authentication, you should specify <languageKeyword>Trusted_Connection=yes</languageKeyword> or <languageKeyword>Integrated Security = SSPI</languageKeyword> instead of user ID and password information in the connection string.</para>
    </alert>
    <code>// BeginGroupCpp.cpp
// compile with: /EHsc
#import "msadox.dll" no_namespace

#include "iostream"
using namespace std;

inline void TESTHR(HRESULT x) {if FAILED(x) _com_issue_error(x);};

int main() {
   if (FAILED(::CoInitialize(NULL)) )
      return -1;

   HRESULT hr = S_OK;

   // Define and initialize ADOX object pointers. These are in ADODB namespace.
   _CatalogPtr m_pCatalog = NULL;
   _UserPtr m_pUserNew = NULL;
   _UserPtr m_pUser = NULL;
   _GroupPtr m_pGroup = NULL;

   // Define String Variables.
   _bstr_t strCnn("Provider='Microsoft.JET.OLEDB.4.0';Data source = 'c:\\Northwind.mdb';jet oledb:system database='c:\\system.mdw'");

   try {
      TESTHR(hr = m_pCatalog.CreateInstance(__uuidof (Catalog)));
      m_pCatalog-&gt;PutActiveConnection(strCnn);

      // Create and append new group with a string.
      m_pCatalog-&gt;Groups-&gt;Append("Accounting");

      // Create and append new user with an object.
      TESTHR(hr = m_pUserNew.CreateInstance(__uuidof(User)));
      m_pUserNew-&gt;PutName("Pat Smith");
      m_pUserNew-&gt;ChangePassword("", "Password1");
      m_pCatalog-&gt;Users-&gt;Append(_variant_t((IDispatch *)m_pUserNew), "");

      // Make the user Pat Smith a member of the Accounting group by creating and adding the
      // appropriate Group object to the user's Groups collection. The same is accomplished if a User
      // object representing Pat Smith is created and appended to the Accounting group Users collection
      m_pUserNew-&gt;Groups-&gt;Append("Accounting");

      // Enumerate all User objects in the catalog's Users collection.
      long lUsrIndex;
      long lGrpIndex;
      _variant_t vIndex;
      for ( lUsrIndex = 0 ; lUsrIndex &lt; m_pCatalog-&gt;Users-&gt;Count ; lUsrIndex++ ) {
         vIndex = lUsrIndex;
         m_pUser = m_pCatalog-&gt;Users-&gt;GetItem(vIndex);
         cout &lt;&lt; "  " &lt;&lt; m_pUser-&gt;Name &lt;&lt; endl;
         cout &lt;&lt; "   Belongs to these groups:" &lt;&lt; endl;

         // Enumerate all Group objects in each User object's Groups collection.
         if (m_pUser-&gt;Groups-&gt;Count != 0)
            for ( lGrpIndex = 0 ; lGrpIndex &lt; m_pUser-&gt;Groups-&gt;Count ; lGrpIndex++ ) {
               vIndex = lGrpIndex;
               m_pGroup = m_pUser-&gt;Groups-&gt;GetItem(vIndex);
               cout &lt;&lt; "     " &lt;&lt; m_pGroup-&gt;Name &lt;&lt; endl;
            }
         else
            cout &lt;&lt; "       [None]" &lt;&lt; endl;
      }

      // Enumerate all Group objects in the default workspace's Groups collection.
      for ( lGrpIndex = 0 ; lGrpIndex &lt; m_pCatalog-&gt;Groups-&gt;Count ; lGrpIndex++ ) {
         vIndex = lGrpIndex;
         m_pGroup = m_pCatalog-&gt;Groups-&gt;GetItem(vIndex);
         cout &lt;&lt; "   " &lt;&lt; m_pGroup-&gt;Name &lt;&lt; endl;
         cout &lt;&lt; "    Has as its members:" &lt;&lt; endl;

         // Enumerate all User objects in each Group object's Users Collection.
         if ( m_pGroup-&gt;Users-&gt;Count != 0)
            for ( lUsrIndex = 0 ; lUsrIndex &lt; m_pGroup-&gt;Users-&gt;Count ; lUsrIndex++ ) {
               vIndex = lUsrIndex;
               m_pUser = m_pGroup-&gt;Users-&gt;GetItem(vIndex);
               cout &lt;&lt; "    " &lt;&lt; m_pUser-&gt;Name &lt;&lt; endl;
            }
         else
            cout &lt;&lt; "      [None]" &lt;&lt; endl;
      }

      // Delete new User and Group object because this is only a demonstration.
      m_pCatalog-&gt;Users-&gt;Delete("Pat Smith");
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