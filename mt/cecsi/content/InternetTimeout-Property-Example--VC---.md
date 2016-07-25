---
title: "InternetTimeout Property Example (VC++)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - C++
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 88b6d05c-d4eb-4ab1-bbe2-95d146237f94
caps.latest.revision: 12
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
# InternetTimeout Property Example (VC++)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <alert class="important">
      <para>Beginning with Windows 8 and Windows Server 2012, RDS server components are no longer included in the Windows operating system (see Windows 8 and <externalLink><linkText>Windows Server 2012 Compatibility Cookbook</linkText><linkUri>http://download.microsoft.com/download/2/C/9/2C9C7B01-A1FC-47B6-9166-2151FB6E007C/Windows 8 and Windows Server 2012 Compatibility Cookbook.docx</linkUri></externalLink> for more detail). RDS client components will be removed in a future version of Windows. Avoid using this feature in new development work, and plan to modify applications that currently use this feature. Applications that use RDS should migrate to <externalLink><linkText>WCF Data Service</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=199565</linkUri></externalLink>.</para>
    </alert>
    <para>This example demonstrates the <legacyLink xlink:href="4d1c8892-4bbc-4e71-bf4b-ba52c0ea9549">InternetTimeout</legacyLink> property, which exists on the <legacyLink xlink:href="d85ea4fc-451c-436e-97b8-58f92b149dd0">DataControl</legacyLink> and <legacyLink xlink:href="9194bffa-5bdf-4dff-af86-f7158c23bfa7">DataSpace</legacyLink> objects. In this case, the <legacyBold>InternetTimeout</legacyBold> property is demonstrated on the <legacyBold>DataControl</legacyBold> object and the timeout is set to 20 seconds.</para>
    <code>// BeginInternetTimeoutCpp
#import "c:\Program Files\Common Files\System\ADO\msado15.dll" \
    no_namespace rename("EOF", "EndOfFile")
#import "C:\Program Files\Common Files\System\MSADC\msadco.dll"

#include &lt;ole2.h&gt;
#include &lt;stdio.h&gt;
#include &lt;conio.h&gt;

// Function declarations
inline void TESTHR(HRESULT x) {if FAILED(x) _com_issue_error(x);};
void InternetTimeOutX(void);
void PrintProviderError(_ConnectionPtr pConnection);
void PrintComError(_com_error &amp;e);

//////////////////////////////////////////////////////////
//                                                      //
//    Main Function                                     //
//                                                      //
//////////////////////////////////////////////////////////

void main()
{
    if(FAILED(::CoInitialize(NULL)))
        return;

    InternetTimeOutX();

    ::CoUninitialize();
}

//////////////////////////////////////////////////////////
//                                                      //
//         InternetTimeOutX Function                    //
//                                                      //
//////////////////////////////////////////////////////////

void InternetTimeOutX(void) 
{
    HRESULT hr = S_OK;

    // Define ADO object pointers.
    // Initialize pointers on define.
    // These are in the ADODB::  namespace.
    _RecordsetPtr  pRst = NULL;

    //Define RDS object pointers
    RDS::IBindMgrPtr dc ;

    try
    {
        TESTHR(dc.CreateInstance(__uuidof(RDS::DataControl)));
        dc-&gt;Server = "http://MyServer";
        dc-&gt;Connect = "Data Source='AuthorDatabase'";
        dc-&gt;SQL = "SELECT * FROM Authors";

        // Wait at least 20 seconds.
        dc-&gt;InternetTimeout = 20000;
        dc-&gt;Refresh();

        // Use another Recordset as a convenience
        pRst = dc-&gt;GetRecordset();
        while(!(pRst-&gt;EndOfFile))
        {
            printf("%s %s",(LPSTR) (_bstr_t) pRst-&gt;Fields-&gt;
                GetItem("au_fname")-&gt;Value,
               (LPSTR) (_bstr_t) pRst-&gt;Fields-&gt;
                GetItem("au_lname")-&gt;Value);

            pRst-&gt;MoveNext();
        }
        pRst-&gt;Close();
    }

    catch (_com_error &amp;e)
    {
        PrintProviderError(pRst-&gt;GetActiveConnection());
        PrintComError(e);
    }
}

//////////////////////////////////////////////////////////
//                                                      //
//     PrintProviderError Function                      //
//                                                      //
//////////////////////////////////////////////////////////

void PrintProviderError(_ConnectionPtr pConnection)
{
    // Print Provider Errors from Connection object.
    // pErr is a record object in the Connection's Error collection.
    ErrorPtr  pErr  = NULL;

    if( (pConnection-&gt;Errors-&gt;Count) &gt; 0)
    {
        long nCount = pConnection-&gt;Errors-&gt;Count;
        // Collection ranges from 0 to nCount -1.
        for(long i = 0; i &lt; nCount; i++)
        {
            pErr = pConnection-&gt;Errors-&gt;GetItem(i);
            printf("\t Error number: %x\t%s", pErr-&gt;Number, 
                pErr-&gt;Description);
        }
    }
}

//////////////////////////////////////////////////////////
//                                                      //
//     PrintComError Function                           //
//                                                      //
//////////////////////////////////////////////////////////

void PrintComError(_com_error &amp;e)
{
    _bstr_t bstrSource(e.Source());
    _bstr_t bstrDescription(e.Description());

    // Print Com errors.  
    printf("Error\n");
    printf("\tCode = %08lx\n", e.Error());
    printf("\tCode meaning = %s\n", e.ErrorMessage());
    printf("\tSource = %s\n", (LPCSTR) bstrSource);
    printf("\tDescription = %s\n", (LPCSTR) bstrDescription);
}
// EndInternetTimeoutCpp</code>
  </introduction>
  <relatedTopics>
<link xlink:href="4d1c8892-4bbc-4e71-bf4b-ba52c0ea9549">InternetTimeoutProperty (RDS)</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>