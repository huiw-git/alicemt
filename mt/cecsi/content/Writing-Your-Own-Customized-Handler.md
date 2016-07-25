---
title: "Writing Your Own Customized Handler"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d447712a-e123-47b5-a3a4-5d366cfe8d72
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
# Writing Your Own Customized Handler
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>You may want to write your own handler if you are an IIS server administrator who wants the default RDS support, but more control over user requests and access rights.</para>
    <para>The MSDFMAP.Handler implements the <legacyBold>IDataFactoryHandler</legacyBold> interface.</para>
    <alert class="important">
      <para>Beginning with Windows 8 and Windows Server 2012, RDS server components are no longer included in the Windows operating system (see Windows 8 and <externalLink><linkText>Windows Server 2012 Compatibility Cookbook</linkText><linkUri>http://download.microsoft.com/download/2/C/9/2C9C7B01-A1FC-47B6-9166-2151FB6E007C/Windows 8 and Windows Server 2012 Compatibility Cookbook.docx</linkUri></externalLink> for more detail). RDS client components will be removed in a future version of Windows. Avoid using this feature in new development work, and plan to modify applications that currently use this feature. Applications that use RDS should migrate to <externalLink><linkText>WCF Data Service</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=199565</linkUri></externalLink>.</para>
    </alert>
  </introduction>
  <section>
    <title>IDataFactoryHandler Interface</title>
    <content>
      <para>This interface has two methods, <legacyBold>GetRecordset</legacyBold> and <legacyBold>Reconnect</legacyBold>. Both methods require that the <legacyLink xlink:href="39c8d86e-7ee9-4182-be5e-aad5ce952f84">CursorLocation</legacyLink> property be set to <legacyBold>adUseClient</legacyBold>.</para>
      <para>Both methods take arguments that appear after the first comma in the "<legacyBold>Handler=</legacyBold>" keyword. For example, <codeInline>"Handler=progid,arg1,arg2;"</codeInline> will pass an argument string of <codeInline>"arg1,arg2"</codeInline>, and <codeInline>"Handler=progid"</codeInline> will pass a null argument.</para>
    </content>
  </section>
  <section>
    <title>GetRecordset Method</title>
    <content>
      <para>This method queries the data source and creates a new <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink> object using the arguments provided. The <legacyBold>Recordset</legacyBold> must be opened with <legacyBold>adLockBatchOptimistic</legacyBold> and must not be opened asynchronously.</para>
    </content>
    <sections>
      <section>
        <title>Arguments</title>
        <content>
          <para>         <legacyBold><legacyItalic>conn</legacyItalic></legacyBold>   The connection string.</para>
          <para>         <legacyBold><legacyItalic>args</legacyItalic></legacyBold>   The arguments for the handler.</para>
          <para>         <legacyBold><legacyItalic>query</legacyItalic></legacyBold>   The command text for making a query.</para>
          <para>         <legacyBold><legacyItalic>ppRS</legacyItalic></legacyBold>   The pointer where the <legacyBold>Recordset</legacyBold> should be returned.</para>
        </content>
      </section>
    </sections>
  </section>
  <section>
    <title>Reconnect Method</title>
    <content>
      <para>This method updates the data source. It creates a new <legacyLink xlink:href="ef6b1824-5b12-43db-89d7-8f3d13896d4d">Connection</legacyLink> object and attaches the given <legacyBold>Recordset</legacyBold>.</para>
    </content>
    <sections>
      <section>
        <title>Arguments</title>
        <content>
          <para>         <legacyBold>           </legacyBold><legacyBold><legacyItalic>conn</legacyItalic></legacyBold><legacyBold>         </legacyBold>   The connection string.</para>
          <para>         <legacyBold>           </legacyBold><legacyBold><legacyItalic>args</legacyItalic></legacyBold><legacyBold>         </legacyBold>   The arguments for the handler.</para>
          <para>         <legacyBold>           </legacyBold><legacyBold><legacyItalic>pRS</legacyItalic></legacyBold><legacyBold>         </legacyBold>   A <legacyBold>Recordset</legacyBold> object.</para>
        </content>
      </section>
    </sections>
  </section>
  <section>
    <title>msdfhdl.idl</title>
    <content>
      <para>This is the interface definition for <legacyBold>IDataFactoryHandler</legacyBold> that appears in the <legacyBold>msdfhdl.idl</legacyBold> file.</para>
      <code>[
  uuid(D80DE8B3-0001-11d1-91E6-00C04FBBBFB3),
  version(1.0)
]
library MSDFHDL
{
    importlib("stdole32.tlb");
    importlib("stdole2.tlb");

    // TLib : Microsoft ActiveX Data Objects 2.0 Library
    // {00000200-0000-0010-8000-00AA006D2EA4}
    #ifdef IMPLIB
    importlib("implib\\x86\\release\\ado\\msado15.dll");
    #else
    importlib("msado20.dll");
    #endif

    [
      odl,
      uuid(D80DE8B5-0001-11d1-91E6-00C04FBBBFB3),
      version(1.0)
    ]
    interface IDataFactoryHandler : IUnknown
    {
HRESULT _stdcall GetRecordset(
      [in] BSTR conn,
      [in] BSTR args,
      [in] BSTR query,
      [out, retval] _Recordset **ppRS);

// DataFactory will use the ActiveConnection property
// on the Recordset after calling Reconnect.
   HRESULT _stdcall Reconnect(
      [in] BSTR conn,
      [in] BSTR args,
      [in] _Recordset *pRS);
    };
};</code>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="d50eb3cc-a822-486f-b80b-65bb50547ecd">Customization File Connect Section</link>
<link xlink:href="a368e264-865c-41ee-be00-d9097255c2ea">Customization File Logs Section</link>
<link xlink:href="e65c2871-9986-44ff-b8b7-7f5eda91b3fa">Customization File SQL Section</link>
<link xlink:href="42e8ec20-eaac-4a95-8cb8-4bba93a75bcb">Customization File UserList Section</link>
<link xlink:href="86d77985-a0d0-405a-8587-c85a20540a0e">DataFactory Customization</link>
<link xlink:href="e776b4e3-fcc4-4bfb-a7e8-5ffae1d83833">Required Client Settings</link>
<link xlink:href="136f74bf-8d86-4a41-be66-c86cbcf81548">Understanding the Customization File</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>