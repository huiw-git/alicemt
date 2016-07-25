---
title: "GetString Method (ADO)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: 92452940-b2a7-456e-94fc-3780c71da33c
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
# GetString Method (ADO)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Returns the <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink> as a string.</para>
  </introduction>
  <syntaxSection>
    <legacySyntax>
<parameterReference>Variant</parameterReference> = <parameterReference>recordset.</parameterReference><legacyBold>GetString</legacyBold><parameterReference>(StringFormat, NumRows, ColumnDelimiter, RowDelimiter, NullExpr)</parameterReference></legacySyntax>
  </syntaxSection>
  <returnValue>
    <content>
      <para>Returns the <legacyBold>Recordset</legacyBold> as a string-valued <languageKeyword>Variant</languageKeyword> (BSTR).</para>
    </content>
  </returnValue>
  <parameters>
    <content>
      <definitionTable>
        <definedTerm> <legacyItalic>StringFormat</legacyItalic> </definedTerm>
        <definition>
          <para>A <legacyLink xlink:href="28f7d1ec-092b-4323-a39d-d3f882c6c81a">StringFormatEnum</legacyLink> value that specifies how the <legacyBold>Recordset</legacyBold> should be converted to a string. The <legacyItalic>RowDelimiter</legacyItalic>, <legacyItalic>ColumnDelimiter</legacyItalic>, and <legacyItalic>NullExpr</legacyItalic> parameters are used only with a <legacyItalic>StringFormat</legacyItalic> of <legacyBold>adClipString</legacyBold>.</para>
        </definition>
        <definedTerm> <legacyItalic>NumRows</legacyItalic> </definedTerm>
        <definition>
          <para>Optional. The number of rows to be converted in the <legacyBold>Recordset</legacyBold>. If <legacyItalic>NumRows </legacyItalic>is not specified, or if it is greater than the total number of rows in the <legacyBold>Recordset</legacyBold>, then all the rows in the <legacyBold>Recordset</legacyBold> are converted.</para>
        </definition>
        <definedTerm> <legacyItalic>ColumnDelimiter</legacyItalic> </definedTerm>
        <definition>
          <para>Optional. A delimiter used between columns, if specified, otherwise the TAB character.</para>
        </definition>
        <definedTerm> <legacyItalic>RowDelimiter</legacyItalic> </definedTerm>
        <definition>
          <para>Optional. A delimiter used between rows, if specified, otherwise the CARRIAGE RETURN character.</para>
        </definition>
        <definedTerm> <legacyItalic>NullExpr</legacyItalic> </definedTerm>
        <definition>
          <para>Optional. An expression used in place of a null value, if specified, otherwise the empty string.</para>
        </definition>
      </definitionTable>
    </content>
  </parameters>
  <languageReferenceRemarks>
    <content>
      <para>Row data, but no schema data, is saved to the string. Therefore, a <legacyBold>Recordset</legacyBold> cannot be reopened using this string.</para>
      <para>This method is equivalent to the RDO <legacyBold>GetClipString</legacyBold> method.</para>
    </content>
  </languageReferenceRemarks>
  <section>
    <title>Applies To</title>
    <content>
      <para>
        <link xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</link>
      </para>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="14c96d71-46a8-4782-b474-80ce348e8bff">Visual Basic Example</link>
</relatedTopics>
</developerReferenceWithSyntaxDocument>