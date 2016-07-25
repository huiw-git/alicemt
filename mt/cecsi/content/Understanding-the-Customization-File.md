---
title: "Understanding the Customization File"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 136f74bf-8d86-4a41-be66-c86cbcf81548
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
# Understanding the Customization File
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Each section header in the customization file consists of square brackets (<legacyBold>[]</legacyBold>) containing a type and parameter. The four section types are indicated by the literal strings <legacyBold>connect</legacyBold>, <legacyBold>sql</legacyBold>, <legacyBold>userlist</legacyBold>, or <legacyBold>logs</legacyBold>. The parameter is the literal string, the default, a user-specified identifier, or nothing.</para>
    <alert class="important">
      <para>Beginning with Windows 8 and Windows Server 2012, RDS server components are no longer included in the Windows operating system (see Windows 8 and <externalLink><linkText>Windows Server 2012 Compatibility Cookbook</linkText><linkUri>http://download.microsoft.com/download/2/C/9/2C9C7B01-A1FC-47B6-9166-2151FB6E007C/Windows 8 and Windows Server 2012 Compatibility Cookbook.docx</linkUri></externalLink> for more detail). RDS client components will be removed in a future version of Windows. Avoid using this feature in new development work, and plan to modify applications that currently use this feature. Applications that use RDS should migrate to <externalLink><linkText>WCF Data Service</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=199565</linkUri></externalLink>.</para>
    </alert>
    <para>Therefore, each section is marked with one of the following section headers: </para>
    <code>
<codeFeaturedElement>[ connect</codeFeaturedElement>  <codeFeaturedElement>default ]</codeFeaturedElement>
<codeFeaturedElement>[ connect  </codeFeaturedElement><legacyItalic>identifier </legacyItalic><codeFeaturedElement>]</codeFeaturedElement>
<codeFeaturedElement>[ sql  default ]</codeFeaturedElement>
<codeFeaturedElement>[ sql  </codeFeaturedElement><legacyItalic>identifier </legacyItalic><codeFeaturedElement>]</codeFeaturedElement>
<codeFeaturedElement>[ userlist  </codeFeaturedElement><legacyItalic>identifier </legacyItalic><codeFeaturedElement>]</codeFeaturedElement>
<codeFeaturedElement>[ logs ]</codeFeaturedElement>
</code>
    <para>The section headers have the following parts.</para>
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
            <para>               <legacyBold>connect</legacyBold>             </para>
          </TD>
          <TD>
            <para>A literal string that modifies a connection string.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyBold>sql</legacyBold>             </para>
          </TD>
          <TD>
            <para>A literal string that modifies a command string.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyBold>userlist</legacyBold>             </para>
          </TD>
          <TD>
            <para>A literal string that modifies the access rights of a specific user.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyBold>logs</legacyBold>             </para>
          </TD>
          <TD>
            <para>A literal string that specifies a log file recording operational errors.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyBold>default</legacyBold>             </para>
          </TD>
          <TD>
            <para>A literal string that is used if no identifier is specified or found.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyItalic>identifier</legacyItalic>             </para>
          </TD>
          <TD>
            <para>A string that matches a string in the <legacyBold>connect</legacyBold> or <legacyBold>command</legacyBold> string.</para>
            <list class="bullet">
              <listItem>
                <para>Use this section if the section header contains <legacyBold>connect</legacyBold> and the identifier string is found in the connection string.</para>
              </listItem>
              <listItem>
                <para>Use this section if the section header contains <legacyBold>sql</legacyBold> and the identifier string is found in the command string.</para>
              </listItem>
              <listItem>
                <para>Use this section if the section header contains <legacyBold>userlist</legacyBold> and the identifier string matches a <legacyBold>connect</legacyBold> section identifier. </para>
              </listItem>
            </list>
          </TD>
        </tr>
      </tbody>
    </table>
    <para>The <legacyBold>DataFactory</legacyBold> calls the handler, passing client parameters. The handler searches for whole strings in the client parameters that match identifiers in the appropriate section headers. If a match is found, the contents of that section are applied to the client parameter.</para>
    <para>A particular section is used under the following circumstances:  </para>
    <list class="bullet">
      <listItem>
        <para>A <legacyBold>connect</legacyBold> section is used if the value part of the client connect string keyword, "<legacyBold>Data Source=</legacyBold><legacyItalic>value</legacyItalic>", matches a <legacyBold>connect</legacyBold> section identifier<legacyItalic>.</legacyItalic></para>
      </listItem>
      <listItem>
        <para>An <legacyBold>sql</legacyBold> section is used if the client command string contains a string that matches an <legacyBold>sql</legacyBold> section identifier.</para>
      </listItem>
      <listItem>
        <para>A <legacyBold>connect</legacyBold> or <legacyBold>sql</legacyBold> section with a default parameter is used if there is no matching identifier.</para>
      </listItem>
      <listItem>
        <para>A <legacyBold>userlist</legacyBold> section is used if the <legacyBold>userlist</legacyBold> section identifier matches a <legacyBold>connect</legacyBold> section identifier. If there is a match, the contents of the <legacyBold>userlist</legacyBold> section are applied to the connection governed by the <legacyBold>connect</legacyBold> section.</para>
      </listItem>
      <listItem>
        <para>If the string in a connection or command string does not match the identifier in any <legacyBold>connect</legacyBold> or <legacyBold>sql</legacyBold> section header, and there is no <legacyBold>connect</legacyBold> or <legacyBold>sql</legacyBold> section header with a default parameter, then the client string is used without modification.</para>
      </listItem>
      <listItem>
        <para>The <legacyBold>logs</legacyBold> section is used whenever the <legacyBold>DataFactory</legacyBold> is in operation.</para>
      </listItem>
    </list>
  </introduction>
  <relatedTopics>
<link xlink:href="d50eb3cc-a822-486f-b80b-65bb50547ecd">Customization File Connect Section</link>
<link xlink:href="a368e264-865c-41ee-be00-d9097255c2ea">Customization File Logs Section</link>
<link xlink:href="e65c2871-9986-44ff-b8b7-7f5eda91b3fa">Customization File SQL Section</link>
<link xlink:href="42e8ec20-eaac-4a95-8cb8-4bba93a75bcb">Customization File UserList Section</link>
<link xlink:href="86d77985-a0d0-405a-8587-c85a20540a0e">DataFactory Customization</link>
<link xlink:href="e776b4e3-fcc4-4bfb-a7e8-5ffae1d83833">Required Client Settings</link>
<link xlink:href="d447712a-e123-47b5-a3a4-5d366cfe8d72">Writing Your Own Customized Handler</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>