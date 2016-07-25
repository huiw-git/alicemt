---
title: "Recordset, SourceRecordset Properties (RDS)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: a29e3fb9-306d-497a-9a59-1856a914e5e9
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
# Recordset, SourceRecordset Properties (RDS)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Indicates the <legacyBold>Recordset</legacyBold> object returned from a custom business object.</para>
    <para>
      <embeddedLabel>Applies To:</embeddedLabel> <link xlink:href="d85ea4fc-451c-436e-97b8-58f92b149dd0">DataControl Object (RDS)</link></para>
    <alert class="important">
      <para>Beginning with Windows 8 and Windows Server 2012, RDS server components are no longer included in the Windows operating system (see Windows 8 and <externalLink><linkText>Windows Server 2012 Compatibility Cookbook</linkText><linkUri>http://download.microsoft.com/download/2/C/9/2C9C7B01-A1FC-47B6-9166-2151FB6E007C/Windows 8 and Windows Server 2012 Compatibility Cookbook.docx</linkUri></externalLink> for more detail). RDS client components will be removed in a future version of Windows. Avoid using this feature in new development work, and plan to modify applications that currently use this feature. Applications that use RDS should migrate to <externalLink><linkText>WCF Data Service</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=199565</linkUri></externalLink>.</para>
    </alert>
  </introduction>
  <syntaxSection>
    <legacySyntax>
<parameterReference>DataControl</parameterReference>.<legacyBold>SourceRecordset </legacyBold>= <parameterReference>Recordset</parameterReference>
<parameterReference>Recordset = DataControl</parameterReference>.<legacyBold>Recordset </legacyBold></legacySyntax>
  </syntaxSection>
  <parameters>
    <content>
      <definitionTable>
        <definedTerm> <legacyItalic>DataControl</legacyItalic> </definedTerm>
        <definition>
          <para>An object variable that represents an <legacyLink xlink:href="d85ea4fc-451c-436e-97b8-58f92b149dd0">RDS.DataControl</legacyLink> object.</para>
        </definition>
        <definedTerm> <legacyItalic>Recordset</legacyItalic> </definedTerm>
        <definition>
          <para>An object variable that represents a <legacyBold>Recordset</legacyBold> object.</para>
        </definition>
      </definitionTable>
    </content>
  </parameters>
  <languageReferenceRemarks>
    <content>
      <para>You can set the <legacyBold>SourceRecordset</legacyBold> property to a <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink> returned from a custom business object.</para>
      <para>These properties allow an application to handle the binding process by means of a custom process. They receive a rowset wrapped in a <legacyBold>Recordset</legacyBold> so that you can interact directly with the <legacyBold>Recordset</legacyBold>, performing actions such as setting properties or iterating through the <legacyBold>Recordset</legacyBold>.</para>
      <para>You can set the <legacyBold>SourceRecordset</legacyBold> property or read the <legacyBold>Recordset</legacyBold> property at run time in scripting code.</para>
      <para>
        <legacyBold>SourceRecordset</legacyBold> is a write-only property, in contrast to the <legacyBold>Recordset</legacyBold> property, which is a read-only property.</para>
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
<link xlink:href="95175316-cd10-4cf7-96ba-2a226fd97701">VBScript Example</link>
<link xlink:href="6840b1e5-c04d-4d3e-9dcc-42128c83492f">CreateRecordset Method (RDS)</link>
<link xlink:href="20f2480f-3758-405d-a379-05a0dce74796">Query Method (RDS)</link>
</relatedTopics>
</developerReferenceWithSyntaxDocument>