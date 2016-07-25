---
title: "Customization File Logs Section"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a368e264-865c-41ee-be00-d9097255c2ea
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
# Customization File Logs Section
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The <legacyBold>logs</legacyBold> section contains a log file entry, which specifies the name of a file that records errors during the operation of the <legacyBold>DataFactory</legacyBold>.</para>
    <alert class="important">
      <para>Beginning with Windows 8 and Windows Server 2012, RDS server components are no longer included in the Windows operating system (see Windows 8 and <externalLink><linkText>Windows Server 2012 Compatibility Cookbook</linkText><linkUri>http://download.microsoft.com/download/2/C/9/2C9C7B01-A1FC-47B6-9166-2151FB6E007C/Windows 8 and Windows Server 2012 Compatibility Cookbook.docx</linkUri></externalLink> for more detail). RDS client components will be removed in a future version of Windows. Avoid using this feature in new development work, and plan to modify applications that currently use this feature. Applications that use RDS should migrate to <externalLink><linkText>WCF Data Service</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=199565</linkUri></externalLink>.</para>
    </alert>
  </introduction>
  <section>
    <title>Syntax</title>
    <content>
      <para>A log file entry is of the form:</para>
      <code>
        <codeFeaturedElement>err=</codeFeaturedElement>
        <legacyItalic>FileName</legacyItalic>
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
              <para>               <legacyBold>err</legacyBold>             </para>
            </TD>
            <TD>
              <para>A literal string that indicates this is a log file entry.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>               <legacyItalic>FileName</legacyItalic>             </para>
            </TD>
            <TD>
              <para>A complete path and file name. The typical file name is <legacyBold>c:\msdfmap.log</legacyBold>.</para>
            </TD>
          </tr>
        </tbody>
      </table>
      <para>The log file will contain the user name, HRESULT, date, and time of each error.</para>
    </content>
  </languageReferenceRemarks>
  <relatedTopics>
<link xlink:href="d50eb3cc-a822-486f-b80b-65bb50547ecd">Customization File Connect Section</link>
<link xlink:href="e65c2871-9986-44ff-b8b7-7f5eda91b3fa">Customization File SQL Section</link>
<link xlink:href="42e8ec20-eaac-4a95-8cb8-4bba93a75bcb">Customization File UserList Section</link>
<link xlink:href="86d77985-a0d0-405a-8587-c85a20540a0e">DataFactory Customization</link>
<link xlink:href="e776b4e3-fcc4-4bfb-a7e8-5ffae1d83833">Required Client Settings</link>
<link xlink:href="136f74bf-8d86-4a41-be66-c86cbcf81548">Understanding the Customization File</link>
<link xlink:href="d447712a-e123-47b5-a3a4-5d366cfe8d72">Writing Your Own Customized Handler</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>