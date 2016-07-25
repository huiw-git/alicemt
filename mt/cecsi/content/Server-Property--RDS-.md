---
title: "Server Property (RDS)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: d2727ce7-da9f-4271-ae3c-9334ef477c14
caps.latest.revision: 15
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
# Server Property (RDS)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Indicates the Internet Information Services (IIS) name and communication protocol.</para>
    <para>You can set the <unmanagedCodeEntityReference>Server</unmanagedCodeEntityReference> property at design time in the OBJECT tags of the<legacyLink xlink:href="d85ea4fc-451c-436e-97b8-58f92b149dd0"> RDS.DataControl</legacyLink> object, or at run time in scripting code.</para>
    <alert class="important">
      <para>Beginning with Windows 8 and Windows Server 2012, RDS server components are no longer included in the Windows operating system (see Windows 8 and <externalLink><linkText>Windows Server 2012 Compatibility Cookbook</linkText><linkUri>http://download.microsoft.com/download/2/C/9/2C9C7B01-A1FC-47B6-9166-2151FB6E007C/Windows 8 and Windows Server 2012 Compatibility Cookbook.docx</linkUri></externalLink> for more detail). RDS client components will be removed in a future version of Windows. Avoid using this feature in new development work, and plan to modify applications that currently use this feature. Applications that use RDS should migrate to <externalLink><linkText>WCF Data Service</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=199565</linkUri></externalLink>.</para>
    </alert>
  </introduction>
  <section>
    <title>Syntax</title>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>Protocol</para>
            </TD>
            <TD>
              <para>Design-time syntax</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>HTTP</para>
            </TD>
            <TD>
              <code>
                <codeFeaturedElement>&lt;PARAM NAME="Server" VALUE="http:</codeFeaturedElement>
                <legacyItalic>//awebsrvr:port</legacyItalic>
                <codeFeaturedElement>"&gt;</codeFeaturedElement> </code>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>HTTPS</para>
            </TD>
            <TD>
              <code>
                <codeFeaturedElement>&lt;PARAM NAME="Server" VALUE="https:</codeFeaturedElement>//<legacyItalic>awebsrvr:port</legacyItalic><codeFeaturedElement>"&gt;</codeFeaturedElement></code>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>DCOM</para>
            </TD>
            <TD>
              <code>
                <codeFeaturedElement>&lt;PARAM NAME="Server" VALUE="</codeFeaturedElement>
                <legacyItalic>computername</legacyItalic>
                <codeFeaturedElement>"&gt;</codeFeaturedElement> </code>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>In-process</para>
            </TD>
            <TD>
              <code>
                <codeFeaturedElement>&lt;PARAM NAME="Server" VALUE=""&gt;</codeFeaturedElement> </code>
            </TD>
          </tr>
        </tbody>
      </table>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>Protocol</para>
            </TD>
            <TD>
              <para>Run-time syntax</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>HTTP</para>
            </TD>
            <TD>
              <code>
                <legacyItalic>DataControl</legacyItalic>
                <codeFeaturedElement>.Server="http://</codeFeaturedElement> <legacyItalic>awebsrvr:port</legacyItalic><codeFeaturedElement>"</codeFeaturedElement> </code>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>HTTPS</para>
            </TD>
            <TD>
              <code>
                <legacyItalic>DataControl</legacyItalic>.<codeFeaturedElement>Server="https://</codeFeaturedElement><legacyItalic>awebsrvr:port</legacyItalic><codeFeaturedElement>"</codeFeaturedElement></code>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>DCOM</para>
            </TD>
            <TD>
              <code>
                <legacyItalic>DataControl</legacyItalic>.<codeFeaturedElement>Server="</codeFeaturedElement><legacyItalic>computername</legacyItalic><codeFeaturedElement>"</codeFeaturedElement></code>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>In-process</para>
            </TD>
            <TD>
              <code>
                <legacyItalic>DataControl</legacyItalic>.<codeFeaturedElement>Server=""</codeFeaturedElement></code>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <section>
    <title>Parameters</title>
    <content>
      <definitionTable>
        <definedTerm>
          <legacyItalic>awebsrvr</legacyItalic>or <legacyItalic>computername</legacyItalic></definedTerm>
        <definition>
          <para>A <languageKeyword>String</languageKeyword> value that contains an Internet or intranet path, or computer name, if the server is on a remote computer; or, an empty string if the server is on the local computer.</para>
        </definition>
        <definedTerm>
          <legacyItalic>port</legacyItalic>
        </definedTerm>
        <definition>
          <para>Optional. A port that is used to connect to a server running IIS. The port number is set in Internet Explorer (on the <legacyBold>View</legacyBold> menu, click <legacyBold>Options</legacyBold>, and then select the <legacyBold>Connection</legacyBold> tab) or in IIS.</para>
        </definition>
        <definedTerm>
          <legacyItalic>DataControl</legacyItalic>
        </definedTerm>
        <definition>
          <para>An object variable that represents an <legacyBold>RDS.DataControl</legacyBold> object.</para>
        </definition>
      </definitionTable>
    </content>
  </section>
  <languageReferenceRemarks>
    <content>
      <para>The server is the location where the <legacyBold>RDS.DataControl</legacyBold> request (that is, a query or update) is processed. By default, all requests are processed by the <legacyLink xlink:href="e75240c2-b749-471e-b6ea-98cae232efbe">RDSServer.DataFactory</legacyLink> object, <legacyLink xlink:href="86d77985-a0d0-405a-8587-c85a20540a0e">MSDFMAP.Handler</legacyLink> component, and <legacyLink xlink:href="136f74bf-8d86-4a41-be66-c86cbcf81548">MSDFMAP.INI</legacyLink> file on the specified server. Remember that when changing servers to reconcile settings in the old and new <legacyBold>MSDFMAP.INI</legacyBold> files. Incompatibilities may cause requests that succeed on one server to fail on another. If the Server property is set to the empty string "", these objects will be used on the local computer.</para>
    </content>
  </languageReferenceRemarks>
  <section>
    <title>Applies To</title>
    <content>
      <para>
        <link xlink:href="d85ea4fc-451c-436e-97b8-58f92b149dd0">DataControl Object (RDS)</link>
      </para>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="0fe57af9-a4d0-4986-a2e3-beaa4d26ed58">VBScript Example</link>
<link xlink:href="dbad5e77-b213-4eb8-aecf-d60f203fdb59">Connect Property (RDS)</link>
<link xlink:href="e0dabf23-a159-4fe5-a962-3df544a21f5c">SQL Property (RDS)</link>
<link xlink:href="250062a4-13c4-4bed-807d-8b9ad81536d4">SubmitChanges Method (RDS)</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>