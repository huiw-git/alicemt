---
title: "onError Event (RDS)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: b01cbc62-fbd7-4068-b16c-8b0f80a05887
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
# onError Event (RDS)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The <legacyBold>onError</legacyBold> event is called whenever an error occurs during an operation.</para>
    <alert class="important">
      <para>Beginning with Windows 8 and Windows Server 2012, RDS server components are no longer included in the Windows operating system (see Windows 8 and <externalLink><linkText>Windows Server 2012 Compatibility Cookbook</linkText><linkUri>http://download.microsoft.com/download/2/C/9/2C9C7B01-A1FC-47B6-9166-2151FB6E007C/Windows 8 and Windows Server 2012 Compatibility Cookbook.docx</linkUri></externalLink> for more detail). RDS client components will be removed in a future version of Windows. Avoid using this feature in new development work, and plan to modify applications that currently use this feature. Applications that use RDS should migrate to <externalLink><linkText>WCF Data Service</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=199565</linkUri></externalLink>.</para>
    </alert>
  </introduction>
  <syntaxSection>
    <legacySyntax>
<legacyBold>onError</legacyBold> <parameterReference>SCode,</parameterReference> <parameterReference>Description,</parameterReference> <parameterReference>Source,</parameterReference> <parameterReference>CancelDisplay</parameterReference></legacySyntax>
  </syntaxSection>
  <parameters>
    <content>
      <definitionTable>
        <definedTerm> <legacyItalic>SCode</legacyItalic> </definedTerm>
        <definition>
          <para>An integer that indicates the status code of the error.</para>
        </definition>
        <definedTerm> <legacyItalic>Description</legacyItalic> </definedTerm>
        <definition>
          <para>A <legacyBold>String</legacyBold> that indicates a description of the error.</para>
        </definition>
        <definedTerm> <legacyItalic>Source</legacyItalic> </definedTerm>
        <definition>
          <para>A <legacyBold>String</legacyBold> that indicates the query or command that caused the error.</para>
        </definition>
        <definedTerm> <legacyItalic>CancelDisplay</legacyItalic> </definedTerm>
        <definition>
          <para>A <legacyBold>Boolean</legacyBold> value, which if set to <languageKeyword>True</languageKeyword>, that prevents the error from being displayed in a dialog box.</para>
        </definition>
      </definitionTable>
    </content>
  </parameters>
  <section>
    <title>Applies To</title>
    <content>
      <para>
        <link xlink:href="d85ea4fc-451c-436e-97b8-58f92b149dd0">DataControl Object (RDS)</link>
      </para>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="29530153-b963-4a7c-8665-2335f1d604a8">Visual C++ Example</link>
<link xlink:href="b34f4472-5e04-4a2c-ab64-38d6eca31a69">ADO Event Handler Summary</link>
</relatedTopics>
</developerReferenceWithSyntaxDocument>