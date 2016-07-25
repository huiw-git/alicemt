---
title: "Parameters Collection, Command Property Example (VC++)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - C++
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 8636fa08-b3db-4e9a-a918-585e76dd59c8
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
# Parameters Collection, Command Property Example (VC++)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The following code demonstrates how to use the <legacyLink xlink:href="bcc9146f-586f-4e69-9c10-863440c9cffa">Command</legacyLink> property with the <legacyLink xlink:href="a02c22fb-542d-465e-a629-30fd59dcbebf">Command</legacyLink> object to retrieve parameter information for the procedure.</para>
    <code>// BeginProcedureParametersCpp.cpp
// compile with: /EHsc
#import "msado15.dll" rename("EOF", "EndOfFile")
#import "msadox.dll" no_namespace

#include "iostream"
using namespace std;

// Function declarations
inline void TESTHR(HRESULT x) {if FAILED(x) _com_issue_error(x);};
void ProcedureParametersX(void);

int main() {
    if ( FAILED(::CoInitialize(NULL)) )
        return -1;

    ProcedureParametersX();

    ::CoUninitialize();
}

void ProcedureParametersX() {
    HRESULT hr = S_OK;

    // Define and initialize ADOX object pointers. These are in ADODB namespace.
    _CatalogPtr m_pCatalog = NULL;

    //Define ADODB object pointers.
    ADODB::_ConnectionPtr m_pCnn = NULL;
    ADODB::_CommandPtr m_pCommand = NULL;
    ADODB::_ParameterPtr m_pParameter = NULL;

    try {
        TESTHR(hr = m_pCnn.CreateInstance(__uuidof(ADODB::Connection)));

        // Open the Connection
        m_pCnn-&gt;Open("Provider='Microsoft.JET.OLEDB.4.0';Data Source='c:\\Northwind.mdb';", "", "", NULL);

        TESTHR(hr = m_pCatalog.CreateInstance(__uuidof(Catalog)));

        // Open the catalog
        m_pCatalog-&gt;PutActiveConnection(_variant_t((IDispatch *)m_pCnn));

        // Get the command object
        m_pCommand = m_pCatalog-&gt;Procedures-&gt;GetItem("CustomerById")-&gt;GetCommand();

        _variant_t vIndex;

        // Retrieve Parameter information
        m_pCommand-&gt;Parameters-&gt;Refresh();
        for ( long lIndex = 0 ; lIndex &lt; m_pCommand-&gt;Parameters-&gt;Count ; lIndex ++ ) {
            vIndex = lIndex;
            m_pParameter = m_pCommand-&gt;Parameters-&gt;GetItem(vIndex);
            cout &lt;&lt; m_pParameter-&gt;Name &lt;&lt; ":" &lt;&lt; m_pParameter-&gt;Type &lt;&lt; "\n" &lt;&lt; endl;
        }
    }
    catch(_com_error &amp;e) {
        // Notify the user of errors if any.
        _bstr_t bstrSource(e.Source());
        _bstr_t bstrDescription(e.Description());
          
        printf("\n\tSource :  %s \n\tdescription : %s \n ", (LPCSTR)bstrSource, (LPCSTR)bstrDescription);
    }
    catch(...) {
        cout &lt;&lt; "Error occured in ProcedureParametersX...." &lt;&lt; endl;
    }
}</code>
  </introduction>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>