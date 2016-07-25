---
title: "RDS Objects"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f2ac8b3b-f968-41c4-a504-7aee3538b7c7
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
# RDS Objects
<?xml version="1.0" encoding="utf-8"?>
<developerOrientationDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <alert class="important">
      <para>Beginning with Windows 8 and Windows Server 2012, RDS server components are no longer included in the Windows operating system (see Windows 8 and <externalLink><linkText>Windows Server 2012 Compatibility Cookbook</linkText><linkUri>http://download.microsoft.com/download/2/C/9/2C9C7B01-A1FC-47B6-9166-2151FB6E007C/Windows 8 and Windows Server 2012 Compatibility Cookbook.docx</linkUri></externalLink> for more detail). RDS client components will be removed in a future version of Windows. Avoid using this feature in new development work, and plan to modify applications that currently use this feature. Applications that use RDS should migrate to <externalLink><linkText>WCF Data Service</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=199565</linkUri></externalLink>.</para>
    </alert>
    <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
      <tbody>
        <tr>
          <TD>
            <para>
              <legacyLink xlink:href="d85ea4fc-451c-436e-97b8-58f92b149dd0">DataControl (RDS)</legacyLink>
            </para>
          </TD>
          <TD>
            <para>Binds a data query <legacyBold>Recordset</legacyBold> to one or more controls (for example, a text box, grid control, or combo box) to display the <legacyBold>Recordset</legacyBold> data on a Web page.</para>
            <para>The <legacyBold>DataControl</legacyBold> object is safe for scripting.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyLink xlink:href="e75240c2-b749-471e-b6ea-98cae232efbe">DataFactory (RDSServer)</legacyLink>
            </para>
          </TD>
          <TD>
            <para>Implements methods that provide read/write data access to specified data sources for client-side applications.</para>
            <para>The <legacyBold>DataFactory</legacyBold> object is not safe for scripting.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyLink xlink:href="9194bffa-5bdf-4dff-af86-f7158c23bfa7">DataSpace (RDS)</legacyLink>
            </para>
          </TD>
          <TD>
            <para>Creates client-side proxies to custom business objects located on the middle tier.</para>
            <para>The <legacyBold>DataSpace</legacyBold> object is safe for scripting.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <link xlink:href="01044c3a-ed38-4144-bc43-fe38a6d22d04">IRDSService Interface (RDS)</link>
            </para>
          </TD>
          <TD>
            <para>Exposes the <link xlink:href="ad45c676-ec7e-4a3a-9a6b-a54f75eb3012">InvokeService (RDS)</link> method, which is used to return a pointer to the requested interface on a more capable version of the object.</para>
          </TD>
        </tr>
      </tbody>
    </table>
  </introduction>
  <relatedTopics>
<link xlink:href="ca9fa99e-1a9f-4deb-80d4-6942555fb22a">RDS API Reference</link>
</relatedTopics>
</developerOrientationDocument>