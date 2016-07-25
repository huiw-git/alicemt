---
title: "DateCreated and DateModified Properties Example (VC++)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - C++
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b964beee-83c7-4f91-8255-3ba864c9adfd
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
# DateCreated and DateModified Properties Example (VC++)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This example demonstrates the <legacyLink xlink:href="2bf4b00d-045c-444e-8af7-8af6297ed418">DateCreated</legacyLink> and <legacyLink xlink:href="fed09266-1547-4bda-9088-c254d81cc738">DateModified</legacyLink> properties by adding a new <legacyLink xlink:href="6e772783-1bc8-4ea7-94b2-7d7a52ea5c47">Column</legacyLink> to an existing <legacyLink xlink:href="a6d74000-0828-49ba-850a-63da865f8802">Table</legacyLink> and by creating a new <legacyBold>Table</legacyBold>. The DateOutput procedure is required for this example to run.</para>
    <code>// BeginDateCreatedCpp.cpp
// compile with: /EHsc
#import "msado15.dll" rename("EOF", "EndOfFile")
#import "msadox.dll" no_namespace

#include "iostream"
using namespace std;

// Function declarations
inline void TESTHR(HRESULT x) {if FAILED(x) _com_issue_error(x);};
void DateCreatedX();
void DateOutPut(_bstr_t strTemp, _TablePtr tblTemp);

int main() {
    if ( FAILED(::CoInitialize(NULL) ) )
        return -1;
    DateCreatedX();
    ::CoUninitialize();
}

void DateCreatedX() {
    HRESULT hr = S_OK;

    // Define ADOX object pointers, initialize pointers. These are in ADODB  namespace.
    _CatalogPtr m_pCatalog = NULL;
    _TablePtr m_pTblEmployees = NULL;
    _TablePtr m_pTblNew = NULL;

    // Set ActiveConnection of Catalog to this string
    _bstr_t strCnn("Provider='Microsoft.JET.OLEDB.4.0';Data Source= 'c:\\Northwind.mdb';");

    try {
        TESTHR(hr = m_pCatalog.CreateInstance(__uuidof (Catalog)));

        // Connect the catalog.
        m_pCatalog-&gt;PutActiveConnection(strCnn);
        m_pTblEmployees = m_pCatalog-&gt;Tables-&gt;GetItem("Employees");

        // Print current information about the Employees table.
        DateOutPut((_bstr_t)"Current properties", m_pTblEmployees);

        // Create and append column to the Employees table.
        m_pTblEmployees-&gt;Columns-&gt;Append("NewColumn", adInteger,0);
        m_pCatalog-&gt;Tables-&gt;Refresh();

        // Print new information about the Employees table.
        DateOutPut((_bstr_t)"After creating a new column", m_pTblEmployees);

        // Delete new column because this is a demonstration.
        m_pTblEmployees-&gt;Columns-&gt;Delete("NewColumn");

        // Create and append new Table object to the Northwind database.
        TESTHR(hr = m_pTblNew.CreateInstance(__uuidof(Table)));

        m_pTblNew-&gt;Name = "NewTable";
        m_pTblNew-&gt;Columns-&gt;Append("NewColumn", adInteger,0);
        m_pCatalog-&gt;Tables-&gt;Append(_variant_t((IDispatch*)m_pTblNew));
        m_pCatalog-&gt;Tables-&gt;Refresh();

        // Print information about the new Table object.
        DateOutPut((_bstr_t)"After creating a new table", m_pCatalog-&gt;Tables-&gt;GetItem("NewTable"));

        // Delete new Table object because this is a demonstration.
        m_pCatalog-&gt;Tables-&gt;Delete(m_pTblNew-&gt;Name);
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
}

void DateOutPut(_bstr_t strTemp , _TablePtr tblTemp) {
    // Print DateCreated and DateModified information about specified Table object.
    cout &lt;&lt; strTemp &lt;&lt; endl;
    cout &lt;&lt; "    Table: " &lt;&lt; tblTemp-&gt;GetName() &lt;&lt; endl;
    cout &lt;&lt; "        DateCreated = " &lt;&lt; (_bstr_t)tblTemp-&gt;GetDateCreated() &lt;&lt; endl;
    cout &lt;&lt; "        DateModified = " &lt;&lt; (_bstr_t)tblTemp-&gt;GetDateModified() &lt;&lt; endl;
}</code>
  </introduction>
  <relatedTopics>
<link xlink:href="6e772783-1bc8-4ea7-94b2-7d7a52ea5c47">Column Object</link>
<link xlink:href="2bf4b00d-045c-444e-8af7-8af6297ed418">DateCreated Property</link>
<link xlink:href="fed09266-1547-4bda-9088-c254d81cc738">DateModified Property</link>
<link xlink:href="a6d74000-0828-49ba-850a-63da865f8802">Table Object</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>