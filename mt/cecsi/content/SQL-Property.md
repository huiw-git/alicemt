---
title: "SQL Property"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: e0dabf23-a159-4fe5-a962-3df544a21f5c
caps.latest.revision: 14
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
# SQL Property
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Indicates the query string used to retrieve the <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink>.</para>
    <para>You can set the <legacyBold>SQL</legacyBold> property at design time in the <legacyLink xlink:href="d85ea4fc-451c-436e-97b8-58f92b149dd0">RDS.DataControl</legacyLink> object's OBJECT tags, or at run time in scripting code.</para>
    <alert class="important">
      <para>Beginning with Windows 8 and Windows Server 2012, RDS server components are no longer included in the Windows operating system (see Windows 8 and <externalLink><linkText>Windows Server 2012 Compatibility Cookbook</linkText><linkUri>http://download.microsoft.com/download/2/C/9/2C9C7B01-A1FC-47B6-9166-2151FB6E007C/Windows 8 and Windows Server 2012 Compatibility Cookbook.docx</linkUri></externalLink> for more detail). RDS client components will be removed in a future version of Windows. Avoid using this feature in new development work, and plan to modify applications that currently use this feature. Applications that use RDS should migrate to <externalLink><linkText>WCF Data Service</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=199565</linkUri></externalLink>.</para>
    </alert>
  </introduction>
  <syntaxSection>
    <legacySyntax>
Design time: <legacyBold>&lt;PARAM NAME="SQL" VALUE="</legacyBold><parameterReference>QueryString</parameterReference><legacyBold>"&gt;</legacyBold>
Run time: <parameterReference>DataControl</parameterReference>.<legacyBold>SQL</legacyBold> = "<parameterReference>QueryString</parameterReference>"</legacySyntax>
  </syntaxSection>
  <parameters>
    <content>
      <definitionTable>
        <definedTerm> <legacyItalic>QueryString</legacyItalic> </definedTerm>
        <definition>
          <para>A <languageKeyword>String</languageKeyword> value that contains a valid SQL data request.</para>
        </definition>
        <definedTerm> <legacyItalic>DataControl</legacyItalic> </definedTerm>
        <definition>
          <para>An object variable that represents an <legacyBold>RDS.DataControl</legacyBold> object.</para>
        </definition>
      </definitionTable>
    </content>
  </parameters>
  <languageReferenceRemarks>
    <content>
      <para>In general, this is an SQL statement (using the dialect of the database server), such as <codeInline>"Select * from NewTitles"</codeInline>. To ensure that records are matched and updated accurately, an updatable query must contain a field other than a Long Binary field or a computed field.</para>
      <para>The <legacyBold>SQL</legacyBold> property is optional if a custom server-side business object retrieves the data for the client.</para>
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
<link xlink:href="32c33bcf-3320-4836-9e2e-99c8978ce581">VBScript Example</link>
<link xlink:href="dbad5e77-b213-4eb8-aecf-d60f203fdb59">Connect Property (RDS)</link>
<link xlink:href="20f2480f-3758-405d-a379-05a0dce74796">Query Method (RDS)</link>
<link xlink:href="c90a8050-0ff4-4c83-9925-261f2f2ccfe9">Refresh Method (RDS)</link>
<link xlink:href="250062a4-13c4-4bed-807d-8b9ad81536d4">SubmitChanges Method (RDS)</link>
</relatedTopics>
</developerReferenceWithSyntaxDocument>