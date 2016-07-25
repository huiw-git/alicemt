---
title: "MoveFirst, MoveLast, MoveNext, and MovePrevious Methods (RDS)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: 45c80bb5-136f-4204-9df2-78740fa55574
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
# MoveFirst, MoveLast, MoveNext, and MovePrevious Methods (RDS)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Moves to the first, last, next, or previous record in a specified <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink> object.</para>
    <alert class="important">
      <para>Beginning with Windows 8 and Windows Server 2012, RDS server components are no longer included in the Windows operating system (see Windows 8 and <externalLink><linkText>Windows Server 2012 Compatibility Cookbook</linkText><linkUri>http://download.microsoft.com/download/2/C/9/2C9C7B01-A1FC-47B6-9166-2151FB6E007C/Windows 8 and Windows Server 2012 Compatibility Cookbook.docx</linkUri></externalLink> for more detail). RDS client components will be removed in a future version of Windows. Avoid using this feature in new development work, and plan to modify applications that currently use this feature. Applications that use RDS should migrate to <externalLink><linkText>WCF Data Service</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=199565</linkUri></externalLink>.</para>
    </alert>
  </introduction>
  <syntaxSection>
    <legacySyntax>
<parameterReference>DataControl</parameterReference><legacyBold>.Recordset.</legacyBold>{<legacyBold>MoveFirst</legacyBold> | <legacyBold>MoveLast</legacyBold> | <legacyBold>MoveNext</legacyBold> | <legacyBold>MovePrevious</legacyBold>}</legacySyntax>
  </syntaxSection>
  <parameters>
    <content>
      <definitionTable>
        <definedTerm> <legacyItalic>DataControl</legacyItalic> </definedTerm>
        <definition>
          <para>An object variable that represents an <legacyLink xlink:href="d85ea4fc-451c-436e-97b8-58f92b149dd0">RDS.DataControl</legacyLink> object.</para>
        </definition>
      </definitionTable>
    </content>
  </parameters>
  <languageReferenceRemarks>
    <content>
      <para>You can use the <legacyBold>Move</legacyBold> methods with the <legacyBold>RDS.DataControl</legacyBold> object to navigate through the data records in the data-bound controls on a Web page. For example, suppose you display a <legacyBold>Recordset</legacyBold> in a grid by binding to an <legacyBold>RDS.DataControl</legacyBold> object. You can then include First, Last, Next, and Previous buttons that users can click to move to the first, last, next, or previous record in the displayed <legacyBold>Recordset</legacyBold>. You do this by calling the <legacyBold>MoveFirst</legacyBold>, <legacyBold>MoveLast</legacyBold>, <legacyBold>MoveNext</legacyBold>, and <legacyBold>MovePrevious</legacyBold> methods of the <legacyBold>RDS.DataControl</legacyBold> object in the onClick procedures for the First, Last, Next, and Previous buttons, respectively. The <legacyLink xlink:href="f0dd84c6-5c33-4ab9-82b4-4c42dfdd2277">Address Book example</legacyLink> shows how to do this.</para>
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
<link xlink:href="13fe9381-d00b-4f4a-9162-83c3f21b3837">Move Method</link>
<link xlink:href="a61a01a7-5b33-4150-9126-21dfa63654cb">MoveFirst, MoveLast, MoveNext, and MovePrevious Methods</link>
<link xlink:href="6d2807b0-b861-4583-bcaf-fb0b82e0f2d0">MoveRecord Method</link>
</relatedTopics>
</developerReferenceWithSyntaxDocument>