---
title: "Handler Property (RDS)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: fdc34362-6d47-4727-b171-8d033159408e
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
# Handler Property (RDS)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Indicates the name of a server-side customization program (handler) that extends the functionality of the <legacyLink xlink:href="e75240c2-b749-471e-b6ea-98cae232efbe">RDSServer.DataFactory</legacyLink>, and any parameters used by the <legacyItalic>handler</legacyItalic>.</para>
    <para>
      <embeddedLabel>Applies To:</embeddedLabel> <link xlink:href="d85ea4fc-451c-436e-97b8-58f92b149dd0">DataControl Object (RDS)</link></para>
    <alert class="important">
      <para>Beginning with Windows 8 and Windows Server 2012, RDS server components are no longer included in the Windows operating system (see Windows 8 and <externalLink><linkText>Windows Server 2012 Compatibility Cookbook</linkText><linkUri>http://download.microsoft.com/download/2/C/9/2C9C7B01-A1FC-47B6-9166-2151FB6E007C/Windows 8 and Windows Server 2012 Compatibility Cookbook.docx</linkUri></externalLink> for more detail). RDS client components will be removed in a future version of Windows. Avoid using this feature in new development work, and plan to modify applications that currently use this feature. Applications that use RDS should migrate to <externalLink><linkText>WCF Data Service</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=199565</linkUri></externalLink>.</para>
    </alert>
  </introduction>
  <syntaxSection>
    <legacySyntax>
<parameterReference>DataControl</parameterReference>.<legacyBold>Handler = </legacyBold><parameterReference>String</parameterReference></legacySyntax>
  </syntaxSection>
  <parameters>
    <content>
      <definitionTable>
        <definedTerm>
          <legacyItalic>DataControl</legacyItalic>
        </definedTerm>
        <definition>
          <para>An object variable that represents an <legacyLink xlink:href="d85ea4fc-451c-436e-97b8-58f92b149dd0">RDS.DataControl</legacyLink> object.</para>
        </definition>
        <definedTerm>
          <legacyItalic>String</legacyItalic>
        </definedTerm>
        <definition>
          <para>A <languageKeyword>String</languageKeyword> value that contains the name of the handler and any parameters, all separated by commas (for example, <codeInline>"handlerName,parm1,parm2,...,parm</codeInline><legacyItalic>N</legacyItalic><codeInline>"</codeInline>).</para>
        </definition>
      </definitionTable>
    </content>
  </parameters>
  <languageReferenceRemarks>
    <content>
      <para>This property supports <legacyLink xlink:href="86d77985-a0d0-405a-8587-c85a20540a0e">customization</legacyLink>, a functionality that requires setting the <legacyLink xlink:href="39c8d86e-7ee9-4182-be5e-aad5ce952f84">CursorLocation</legacyLink> property to <legacyBold>adUseClient</legacyBold>.</para>
      <para>The name of the handler and its parameters, if any, are separated by commas (","). Unpredictable behavior will result if a semicolon (";") appears anywhere within <legacyItalic>String</legacyItalic>. You can write your own handler, provided it supports the <legacyBold>IDataFactoryHandler</legacyBold> interface.</para>
      <para>The name of the default handler is <legacyBold>MSDFMAP.Handler</legacyBold>, and its default parameter is a customization file named <legacyBold>MSDFMAP.INI</legacyBold>. Use this property to invoke alternate customization files created by your server administrator.</para>
      <para>The alternative to setting the <legacyBold>Handler </legacyBold>property is to specify a handler and parameters in the <legacyLink xlink:href="3be75b75-4d36-4479-ab64-9a456869252a">ConnectionString</legacyLink> property; that is, "<legacyBold>Handler=</legacyBold><legacyItalic>handlerName,parameter1,parameter2,...;</legacyItalic>".</para>
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
<link xlink:href="9664f9a6-65fc-4e7f-be3d-3e4b501b558a">Visual Basic Example</link>
<link xlink:href="86d77985-a0d0-405a-8587-c85a20540a0e">DataFactory Customization</link>
<link xlink:href="e75240c2-b749-471e-b6ea-98cae232efbe">DataFactory Object (RDSServer)</link>
</relatedTopics>
</developerReferenceWithSyntaxDocument>