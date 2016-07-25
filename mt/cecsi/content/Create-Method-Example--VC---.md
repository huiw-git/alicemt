---
title: "Create Method Example (VC++)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - C++
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 57fcb0eb-5d40-4ad4-996d-380732de8a3d
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
# Create Method Example (VC++)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The following code shows how to create a new Microsoft Jet database with the <legacyLink xlink:href="64f5c21c-b581-42d8-bdc7-c4f1bebaf105">Create</legacyLink> method.</para>
    <code>// BeginCreateDatabaseCpp.cpp
// compile with: /EHsc
#import "msado15.dll" rename("EOF", "EndOfFile")
#import "msadox.dll" no_namespace

#define TESTHR(x) if FAILED(x) _com_issue_error(x);

#include "iostream"
using namespace std;

// Function declarations
void CreateDatabaseX(void);

int main() {
   HRESULT hr = S_OK;

   hr = ::CoInitialize(NULL);
   if (SUCCEEDED(hr)) {
      CreateDatabaseX();
      ::CoUninitialize();
   }
}

// Create a new Jet database with the Create method
void CreateDatabaseX() {
   HRESULT hr = S_OK;

   // Define ADOX object pointers, initialize pointers. These are in ADODB namespace.
   _CatalogPtr m_pCatalog = NULL;


   // Set ActiveConnection of Catalog to this string
   _bstr_t strcnn("Provider='Microsoft.JET.OLEDB.4.0';Data source = c:\\new.mdb");
   try {
      TESTHR(hr = m_pCatalog.CreateInstance(__uuidof (Catalog)));
      m_pCatalog-&gt;Create(strcnn);
      printf("Database 'c:\\new.mdb' is created.\n");
   }
   catch(_com_error &amp;e) {
      // Notify the user of errors if any.
      _bstr_t bstrSource(e.Source());
      _bstr_t bstrDescription(e.Description());

      printf("\n\tSource :  %s \n\tdescription : %s \n ", (LPCSTR)bstrSource, (LPCSTR)bstrDescription);
   }
   catch(...) {
      cout &lt;&lt; "Error occured in CreateDatabaseX...." &lt;&lt; endl;
   }
}</code>
  </introduction>
  <relatedTopics>
<link xlink:href="64f5c21c-b581-42d8-bdc7-c4f1bebaf105">Create Method</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>