---
title: "Query Method (RDS)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: 20f2480f-3758-405d-a379-05a0dce74796
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
# Query Method (RDS)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Uses a valid SQL query string to return a <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink>.</para>
    <alert class="important">
      <para>Beginning with Windows 8 and Windows Server 2012, RDS server components are no longer included in the Windows operating system (see Windows 8 and <externalLink><linkText>Windows Server 2012 Compatibility Cookbook</linkText><linkUri>http://download.microsoft.com/download/2/C/9/2C9C7B01-A1FC-47B6-9166-2151FB6E007C/Windows 8 and Windows Server 2012 Compatibility Cookbook.docx</linkUri></externalLink> for more detail). RDS client components will be removed in a future version of Windows. Avoid using this feature in new development work, and plan to modify applications that currently use this feature. Applications that use RDS should migrate to <externalLink><linkText>WCF Data Service</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=199565</linkUri></externalLink>.</para>
    </alert>
  </introduction>
  <syntaxSection>
    <legacySyntax>
<legacyBold>Set </legacyBold><parameterReference>Recordset = DataFactory</parameterReference>.<legacyBold>Query</legacyBold>(<parameterReference>Connection, Query)</parameterReference></legacySyntax>
  </syntaxSection>
  <parameters>
    <content>
      <definitionTable>
        <definedTerm> <legacyItalic>Recordset</legacyItalic> </definedTerm>
        <definition>
          <para>An object variable that represents a <unmanagedCodeEntityReference>Recordset</unmanagedCodeEntityReference> object.</para>
        </definition>
        <definedTerm> <legacyItalic>DataFactory</legacyItalic> </definedTerm>
        <definition>
          <para>An object variable that represents an <legacyLink xlink:href="e75240c2-b749-471e-b6ea-98cae232efbe">RDSServer.DataFactory</legacyLink> object.</para>
        </definition>
        <definedTerm> <legacyItalic>Connection</legacyItalic> </definedTerm>
        <definition>
          <para>A <languageKeyword>String</languageKeyword> value that contains the server connection information. This is similar to the <legacyLink xlink:href="dbad5e77-b213-4eb8-aecf-d60f203fdb59">Connect</legacyLink> property.</para>
        </definition>
        <definedTerm> <legacyItalic>Query</legacyItalic> </definedTerm>
        <definition>
          <para>A <languageKeyword>String</languageKeyword> that contains the SQL query.</para>
        </definition>
      </definitionTable>
    </content>
  </parameters>
  <languageReferenceRemarks>
    <content>
      <para>The query should use the SQL dialect of the database server. A result status is returned if there is an error with the query that was executed. The <unmanagedCodeEntityReference>Query</unmanagedCodeEntityReference> method does not perform any syntax checking on the <unmanagedCodeEntityReference>Query</unmanagedCodeEntityReference> string.</para>
    </content>
  </languageReferenceRemarks>
  <section>
    <title>Applies To</title>
    <content>
      <para>
        <link xlink:href="e75240c2-b749-471e-b6ea-98cae232efbe">DataFactory Object (RDSServer)</link>
      </para>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="b4e2844a-120a-4513-860b-f1b6e4b5dda4">VBScript Example</link>
</relatedTopics>
</developerReferenceWithSyntaxDocument>