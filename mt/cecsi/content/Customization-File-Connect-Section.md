---
title: "Customization File Connect Section"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d50eb3cc-a822-486f-b80b-65bb50547ecd
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
# Customization File Connect Section
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The default behavior of the handler is to deny all connections. The <legacyBold>connect</legacyBold> section specifies exceptions to that behavior. For example, if all the <legacyBold>connect</legacyBold> sections were absent or empty, then by default no connections could be made.</para>
    <para>The <legacyBold>connect</legacyBold> section can contain:  </para>
    <list class="bullet">
      <listItem>
        <para>A default access entry that specifies the default read and write operations allowed on this connection. If there is no default access entry in the section, the section will be ignored.</para>
      </listItem>
      <listItem>
        <para>A new connection string that replaces the client connection string.</para>
      </listItem>
    </list>
    <alert class="important">
      <para>Beginning with Windows 8 and Windows Server 2012, RDS server components are no longer included in the Windows operating system (see Windows 8 and <externalLink><linkText>Windows Server 2012 Compatibility Cookbook</linkText><linkUri>http://download.microsoft.com/download/2/C/9/2C9C7B01-A1FC-47B6-9166-2151FB6E007C/Windows 8 and Windows Server 2012 Compatibility Cookbook.docx</linkUri></externalLink> for more detail). RDS client components will be removed in a future version of Windows. Avoid using this feature in new development work, and plan to modify applications that currently use this feature. Applications that use RDS should migrate to <externalLink><linkText>WCF Data Service</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=199565</linkUri></externalLink>.</para>
    </alert>
  </introduction>
  <section>
    <title>Syntax</title>
    <content>
      <para>A default access entry is of the form:</para>
      <code>
        <codeFeaturedElement>Access=</codeFeaturedElement>
        <legacyItalic>accessRight</legacyItalic>
      </code>
      <para>A replacement connection string entry is of the form:</para>
      <code>
        <codeFeaturedElement>Connect=</codeFeaturedElement>
        <legacyItalic>connectionString</legacyItalic>
      </code>
    </content>
  </section>
  <languageReferenceRemarks>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>Part</para>
            </TD>
            <TD>
              <para>Description</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>               <legacyBold>Connect</legacyBold>             </para>
            </TD>
            <TD>
              <para>A literal string that indicates this is a connection string entry.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>               <legacyBold>                 </legacyBold><legacyBold><legacyItalic>connectionString</legacyItalic></legacyBold><legacyBold>               </legacyBold>             </para>
            </TD>
            <TD>
              <para>A string that replaces the whole client connection string.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>               <legacyBold>Access</legacyBold>             </para>
            </TD>
            <TD>
              <para>A literal string that indicates this is an access entry.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>               <legacyBold>                 </legacyBold><legacyBold><legacyItalic>accessRight</legacyItalic></legacyBold><legacyBold>               </legacyBold>             </para>
            </TD>
            <TD>
              <para>One of the following access rights:</para>
              <list class="bullet">
                <listItem>
                  <para>                   <legacyBold>NoAccess </legacyBold>— User cannot access the data source.</para>
                </listItem>
                <listItem>
                  <para>                   <legacyBold>ReadOnly </legacyBold>— User can read the data source.</para>
                </listItem>
                <listItem>
                  <para>                   <legacyBold>ReadWrite </legacyBold>— User can read or write to the data source.</para>
                </listItem>
              </list>
            </TD>
          </tr>
        </tbody>
      </table>
      <para>If you want to allow any connection (in effect, disabling the default handler behavior), set the access entry in the <legacyBold>connect default </legacyBold>section to <codeInline>Access=ReadWrite</codeInline>, and delete or comment out any other <legacyBold>connect </legacyBold><legacyItalic>identifier </legacyItalic>section.</para>
    </content>
  </languageReferenceRemarks>
  <relatedTopics>
<link xlink:href="a368e264-865c-41ee-be00-d9097255c2ea">Customization File Logs Section</link>
<link xlink:href="e65c2871-9986-44ff-b8b7-7f5eda91b3fa">Customization File SQL Section</link>
<link xlink:href="42e8ec20-eaac-4a95-8cb8-4bba93a75bcb">Customization File UserList Section</link>
<link xlink:href="86d77985-a0d0-405a-8587-c85a20540a0e">DataFactory Customization</link>
<link xlink:href="e776b4e3-fcc4-4bfb-a7e8-5ffae1d83833">Required Client Settings</link>
<link xlink:href="136f74bf-8d86-4a41-be66-c86cbcf81548">Understanding the Customization File</link>
<link xlink:href="d447712a-e123-47b5-a3a4-5d366cfe8d72">Writing Your Own Customized Handler</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>