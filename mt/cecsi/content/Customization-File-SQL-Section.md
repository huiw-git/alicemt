---
title: "Customization File SQL Section"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e65c2871-9986-44ff-b8b7-7f5eda91b3fa
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
# Customization File SQL Section
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The <legacyBold>sql</legacyBold> section can contain a new SQL string that replaces the client command string. If there is no SQL string in the section, the section will be ignored.</para>
    <alert class="important">
      <para>Beginning with Windows 8 and Windows Server 2012, RDS server components are no longer included in the Windows operating system (see Windows 8 and <externalLink><linkText>Windows Server 2012 Compatibility Cookbook</linkText><linkUri>http://download.microsoft.com/download/2/C/9/2C9C7B01-A1FC-47B6-9166-2151FB6E007C/Windows 8 and Windows Server 2012 Compatibility Cookbook.docx</linkUri></externalLink> for more detail). RDS client components will be removed in a future version of Windows. Avoid using this feature in new development work, and plan to modify applications that currently use this feature. Applications that use RDS should migrate to <externalLink><linkText>WCF Data Service</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=199565</linkUri></externalLink>.</para>
    </alert>
    <para>The new SQL string may be <legacyItalic>parameterized</legacyItalic>. That is, parameters in the <legacyBold>sql</legacyBold> section SQL string (designated by the '?' character) can be replaced by corresponding arguments in an <legacyItalic>identifier</legacyItalic> in the client command string (designated by a comma-delimited list in parentheses). The identifier and argument list behave like a function call.</para>
    <para>For example, assume the client command string is <codeInline>"CustomerByID(4)"</codeInline>, the SQL section header is <codeInline>[SQL CustomerByID]</codeInline>, and the new SQL section string is <codeInline>"SELECT * FROM Customers WHERE CustomerID = ?". </codeInline>The Handler will generate <codeInline>"SELECT * FROM Customers WHERE CustomerID = 4"</codeInline> and use that string to query the data source.</para>
    <para>If the new SQL statement is the null string (""), then the section is ignored.</para>
    <para>If the new SQL statement string is not valid, then the execution of the statement will fail. The client parameter is effectively ignored. You can do this intentionally to "turn off" all client SQL commands by specifying:</para>
    <code>[SQL default] 
SQL = " "</code>
  </introduction>
  <section>
    <title>Syntax</title>
    <content>
      <para>A replacement SQL string entry is of the form:</para>
      <para>         <legacyBold>SQL=</legacyBold><legacyBold><legacyItalic>sqlString</legacyItalic></legacyBold>       </para>
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
              <para>               <legacyBold>SQL</legacyBold>             </para>
            </TD>
            <TD>
              <para>A literal string that indicates this is an SQL section entry.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>               <legacyBold>                 </legacyBold><legacyBold><legacyItalic>sqlString</legacyItalic></legacyBold><legacyBold>               </legacyBold>             </para>
            </TD>
            <TD>
              <para>An SQL string that replaces the client string.</para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="d50eb3cc-a822-486f-b80b-65bb50547ecd">Customization File Connect Section</link>
<link xlink:href="a368e264-865c-41ee-be00-d9097255c2ea">Customization File Logs Section</link>
<link xlink:href="42e8ec20-eaac-4a95-8cb8-4bba93a75bcb">Customization File UserList Section</link>
<link xlink:href="86d77985-a0d0-405a-8587-c85a20540a0e">DataFactory Customization</link>
<link xlink:href="e776b4e3-fcc4-4bfb-a7e8-5ffae1d83833">Required Client Settings</link>
<link xlink:href="136f74bf-8d86-4a41-be66-c86cbcf81548">Understanding the Customization File</link>
<link xlink:href="d447712a-e123-47b5-a3a4-5d366cfe8d72">Writing Your Own Customized Handler</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>