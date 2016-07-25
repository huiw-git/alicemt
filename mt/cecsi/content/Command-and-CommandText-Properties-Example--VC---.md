---
title: "Command and CommandText Properties Example (VC++)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - C++
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 5a007b9a-be11-4fba-96db-6252993f97b8
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
# Command and CommandText Properties Example (VC++)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The following code demonstrates how to use the <legacyLink xlink:href="bcc9146f-586f-4e69-9c10-863440c9cffa">Command</legacyLink> property to update the text of a procedure.</para>
    <code>// BeginCommandTextCpp
// This sample runs correctly only if procedure 'CustomerById' exists.

#import "msado15.dll" rename("EOF", "EndOfFile")
#import "msadox.dll" no_namespace

#include "iostream"
using namespace std;

// Function declarations
inline void TESTHR(HRESULT x) {if FAILED(x) _com_issue_error(x);};
void ProcedureTextX();

int main() {
   if ( FAILED(::CoInitialize(NULL) ) )
      return -1;

   HRESULT hr = S_OK;

   // Define ADOX object pointers, initialize pointers. These are in ADOX namespace.
   _CatalogPtr m_pCatalog = NULL;

   // Define ADODB object pointers.
   ADODB::_ConnectionPtr m_pCnn = NULL;
   ADODB::_CommandPtr m_pCommand = NULL;

   try {
      // Open the Connection
      TESTHR(hr = m_pCnn.CreateInstance(__uuidof(ADODB::Connection)));
      TESTHR(hr = m_pCatalog.CreateInstance(__uuidof(Catalog)));
      TESTHR(hr = m_pCommand.CreateInstance(__uuidof(ADODB::Command)));
      m_pCnn-&gt;Open("Provider='Microsoft.JET.OLEDB.4.0';data source='c:\\Northwind.mdb';", "", "", NULL);

      // Open the catalog
      m_pCatalog-&gt;PutActiveConnection(_variant_t((IDispatch *)m_pCnn));

      // Get the Command
      m_pCommand = m_pCatalog-&gt;Procedures-&gt;GetItem("CustomerById")-&gt;GetCommand();

      // Update the CommandText
      m_pCommand-&gt;PutCommandText("PARAMETERS [CustId] Text;select "
         "CustomerId, CompanyName, ContactName "
         "from Customers where CustomerId = [CustId]");
      printf("CommandText is updated.\n");

      // Update the Procedure
      m_pCatalog-&gt;Procedures-&gt;GetItem("CustomerById")-&gt;PutCommand(_variant_t((IDispatch *)m_pCommand));
      printf("Procedure 'CustomerById' is updated.\n");
   }
   catch(_com_error &amp;e) {
      // Notify the user of errors if any.
      _bstr_t bstrSource(e.Source());
      _bstr_t bstrDescription(e.Description());

      printf("\n\tSource :  %s \n\tdescription : %s \n ", (LPCSTR)bstrSource, (LPCSTR)bstrDescription);
   }
   catch(...) {
      cout &lt;&lt; "Error occured in ProcedureTextX...."&lt;&lt; endl;
   }

   ::CoUninitialize();
}</code>
  </introduction>
  <relatedTopics>
<link xlink:href="bcc9146f-586f-4e69-9c10-863440c9cffa">Command Property</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>