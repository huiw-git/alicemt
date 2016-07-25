---
title: "Seek Method"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: 129293d2-19d3-4940-bf64-483ee72fb4a1
caps.latest.revision: 11
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
# Seek Method
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Searches the index of a <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink> to quickly locate the row that matches the specified values, and changes the current row position to that row.</para>
  </introduction>
  <syntaxSection>
    <legacySyntax>
recordset.Seek KeyValues, SeekOption</legacySyntax>
  </syntaxSection>
  <parameters>
    <content>
      <definitionTable>
        <definedTerm> <legacyItalic>KeyValues</legacyItalic> </definedTerm>
        <definition>
          <para>An array of <languageKeyword>Variant</languageKeyword> values. An index consists of one or more columns and the array contains a value to compare against each corresponding column.</para>
        </definition>
        <definedTerm> <legacyItalic>SeekOption</legacyItalic> </definedTerm>
        <definition>
          <para>A <legacyLink xlink:href="f0ec0c92-8253-47c6-9a14-e5dbccbad219">SeekEnum</legacyLink> value that specifies the type of comparison to be made between the columns of the index and the corresponding <legacyItalic>KeyValues</legacyItalic>.</para>
        </definition>
      </definitionTable>
    </content>
  </parameters>
  <languageReferenceRemarks>
    <content>
      <para>Use the <unmanagedCodeEntityReference>Seek</unmanagedCodeEntityReference> method in conjunction with the <legacyLink xlink:href="1c79e271-21ec-41a8-8163-c5e89f0001a7">Index</legacyLink> property if the underlying provider supports indexes on the <unmanagedCodeEntityReference>Recordset</unmanagedCodeEntityReference> object. Use the <legacyLink xlink:href="298fc41c-0b55-42fc-b373-c5133b4da6a5">Supports</legacyLink><legacyBold>(adSeek)</legacyBold> method to determine whether the underlying provider supports <unmanagedCodeEntityReference>Seek</unmanagedCodeEntityReference>, and the <unmanagedCodeEntityReference>Supports</unmanagedCodeEntityReference><legacyBold>(adIndex)</legacyBold> method to determine whether the provider supports indexes. (For example, the <legacyLink xlink:href="fd956da1-5203-40af-aa7e-fc13a6c6581f">OLE DB Provider for Microsoft Jet</legacyLink> supports <unmanagedCodeEntityReference>Seek</unmanagedCodeEntityReference> and <unmanagedCodeEntityReference>Index</unmanagedCodeEntityReference>.)</para>
      <para>If <unmanagedCodeEntityReference>Seek</unmanagedCodeEntityReference> does not find the desired row, no error occurs, and the row is positioned at the end of the <unmanagedCodeEntityReference>Recordset</unmanagedCodeEntityReference>. Set the <unmanagedCodeEntityReference>Index</unmanagedCodeEntityReference> property to the desired index before executing this method.</para>
      <para>This method is supported only with server-side cursors. Seek is not supported when the <unmanagedCodeEntityReference>Recordset</unmanagedCodeEntityReference> object's <legacyLink xlink:href="39c8d86e-7ee9-4182-be5e-aad5ce952f84">CursorLocation</legacyLink> property value is <legacyBold>adUseClient</legacyBold>.</para>
      <para>This method can only be used when the <unmanagedCodeEntityReference>Recordset</unmanagedCodeEntityReference> object has been opened with a <legacyLink xlink:href="4b1feb9c-a855-40fe-a906-efe688687e9f">CommandTypeEnum</legacyLink> value of <legacyBold>adCmdTableDirect</legacyBold>.</para>
    </content>
  </languageReferenceRemarks>
  <section>
    <title>Applies To</title>
    <content>
      <para>
        <link xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset Object</link>
      </para>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="337c9eda-9ddf-49ac-94d3-b33114ba6224">Visual Basic Example</link>
<link xlink:href="57bda520-e98b-443c-a8bc-d8430e89a383">Visual C++ Example</link>
<link xlink:href="55c9810a-d8ca-46c2-a9dc-80e7ee7aa188">Find Method</link>
<link xlink:href="1c79e271-21ec-41a8-8163-c5e89f0001a7">Index Property</link>
</relatedTopics>
</developerReferenceWithSyntaxDocument>