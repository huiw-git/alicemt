---
title: "Handler Property Example (VC++)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - C++
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d046d89c-622b-48bc-9d30-f454c3e13595
caps.latest.revision: 16
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
# Handler Property Example (VC++)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <alert class="important">
      <para>Beginning with Windows 8 and Windows Server 2012, RDS server components are no longer included in the Windows operating system (see Windows 8 and <externalLink><linkText>Windows Server 2012 Compatibility Cookbook</linkText><linkUri>http://download.microsoft.com/download/2/C/9/2C9C7B01-A1FC-47B6-9166-2151FB6E007C/Windows 8 and Windows Server 2012 Compatibility Cookbook.docx</linkUri></externalLink> for more detail). RDS client components will be removed in a future version of Windows. Avoid using this feature in new development work, and plan to modify applications that currently use this feature. Applications that use RDS should migrate to <externalLink><linkText>WCF Data Service</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=199565</linkUri></externalLink>.</para>
    </alert>
    <para>This example demonstrates the <legacyLink xlink:href="d85ea4fc-451c-436e-97b8-58f92b149dd0">RDS DataControl</legacyLink> object <legacyLink xlink:href="fdc34362-6d47-4727-b171-8d033159408e">Handler</legacyLink> property. (See <legacyLink xlink:href="86d77985-a0d0-405a-8587-c85a20540a0e">DataFactory Customization</legacyLink> for more details.)</para>
    <para>Assume the following sections in the parameter file, Msdfmap.ini, located on the server:</para>
    <code>[connect AuthorDataBase]
Access=ReadWrite
Connect="DSN=Pubs"
[sql AuthorById]
SQL="SELECT * FROM Authors WHERE au_id = ?"</code>
    <para>Your code looks like the following. The command assigned to the <legacyLink xlink:href="e0dabf23-a159-4fe5-a962-3df544a21f5c">SQL</legacyLink> property will match the <legacyBold><legacyItalic>AuthorById</legacyItalic></legacyBold> identifier and will retrieve a row for author Michael O'Leary. Although the <legacyLink xlink:href="dbad5e77-b213-4eb8-aecf-d60f203fdb59">Connect</legacyLink> property in your code specifies the Northwind data source, that data source will be overwritten by the Msdfmap.ini <legacyItalic>connect</legacyItalic> section. The <legacyBold>DataControl</legacyBold> object <legacyLink xlink:href="a29e3fb9-306d-497a-9a59-1856a914e5e9">Recordset</legacyLink> property is assigned to a disconnected <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink> object purely as a coding convenience.</para>
    <code>// BeginHandlerCpp.cpp
// compile with: /EHsc
#import "msado15.dll" no_namespace rename("EOF", "EndOfFile")
#import "msadco.dll"

#include &lt;ole2.h&gt;
#include &lt;stdio.h&gt;
#include &lt;conio.h&gt;

// Function declarations
inline void TESTHR(HRESULT x) {if FAILED(x) _com_issue_error(x);};
void HandlerX();
void PrintProviderError(_ConnectionPtr pConnection);
void PrintComError(_com_error &amp;e);

int main() {
   HRESULT hr = S_OK;
   hr = ::CoInitialize(NULL);
   if (SUCCEEDED(hr)) {
      HandlerX();
      ::CoUninitialize();
   }
}

void HandlerX() {
   HRESULT  hr = S_OK;
   // Define and initialize ADO object pointers, in the ADODB namespace.   
   _RecordsetPtr pRst = NULL;

   // Define RDS object pointers.
   RDS::IBindMgrPtr dc;

   try {
      TESTHR(hr = dc.CreateInstance(__uuidof(RDS::DataControl)));
      dc-&gt;Handler = "MSDFMAP.Handler";
      dc-&gt;ExecuteOptions = 1;
      dc-&gt;FetchOptions = 1;
      dc-&gt;Server = "http://MyServer";
      dc-&gt;Connect = "Data Source=AuthorDatabase";
      dc-&gt;SQL = "AuthorById('267-41-2394')";

      // Retrieve the record.
      dc-&gt;Refresh();

      // Use another Recordset as a convenience.
      pRst = dc-&gt;GetRecordset();
      printf("Author is %s %s", 
         (LPSTR)(_bstr_t) pRst-&gt;Fields-&gt;GetItem("au_fname")-&gt;Value, 
         (LPSTR)(_bstr_t) pRst-&gt;Fields-&gt;GetItem("au_lname")-&gt;Value);
      pRst-&gt;Close();

   }  // End Try statement.
   catch (_com_error &amp;e) {
      PrintProviderError(pRst-&gt;GetActiveConnection());
      PrintComError(e);
   }
}

void PrintProviderError(_ConnectionPtr pConnection) {
   // Print Provider Errors from Connection object.
   // pErr is a record object in the Connection's Error collection.
   ErrorPtr pErr = NULL;
   long nCount = 0;
   long i = 0;

   if ( (pConnection-&gt;Errors-&gt;Count) &gt; 0) {
      nCount = pConnection-&gt;Errors-&gt;Count;
      // Collection ranges from 0 to nCount -1.
      for ( i = 0 ; i &lt; nCount ; i++ ) {
         pErr = pConnection-&gt;Errors-&gt;GetItem(i);
         printf("\t Error number: %x\t%s", pErr-&gt;Number, pErr-&gt;Description);
      }
   }
}

void PrintComError(_com_error &amp;e) {
   _bstr_t bstrSource(e.Source());
   _bstr_t bstrDescription(e.Description());

   // Print Com errors.  
   printf("Error\n");
   printf("\tCode = %08lx\n", e.Error());
   printf("\tCode meaning = %s\n", e.ErrorMessage());
   printf("\tSource = %s\n", (LPCSTR) bstrSource);
   printf("\tDescription = %s\n", (LPCSTR) bstrDescription);
}</code>
  </introduction>
  <relatedTopics>
<link xlink:href="d85ea4fc-451c-436e-97b8-58f92b149dd0">DataControl Object (RDS)</link>
<link xlink:href="fdc34362-6d47-4727-b171-8d033159408e">Handler Property (RDS)</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>