---
title: "ReadText Method"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: be5a409e-cf87-4859-9ea5-713401755a77
caps.latest.revision: 15
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
# ReadText Method
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Reads specified number of characters from a text <legacyLink xlink:href="0514531f-009d-4519-abc3-d727014a39f1">Stream</legacyLink> object.</para>
  </introduction>
  <syntaxSection>
    <legacySyntax>
<parameterReference>String = Stream</parameterReference><legacyBold>.ReadText ( </legacyBold><parameterReference>NumChars</parameterReference><legacyBold>)</legacyBold></legacySyntax>
  </syntaxSection>
  <parameters>
    <content>
      <definitionTable>
        <definedTerm>
          <legacyItalic>NumChars</legacyItalic>
        </definedTerm>
        <definition>
          <para>Optional. A <languageKeyword>Long</languageKeyword> value that specifies the number of characters to read from the file, or a <legacyLink xlink:href="cfa1b416-003a-436f-a21b-bd2397e54db3">StreamReadEnum</legacyLink> value. The default value is <legacyBold>adReadAll</legacyBold>.</para>
        </definition>
      </definitionTable>
    </content>
  </parameters>
  <returnValue>
    <content>
      <para>The <legacyBold>ReadText </legacyBold>method reads a specified number of characters, an entire line, or the entire stream from a <legacyBold>Stream</legacyBold> object and returns the resulting string.</para>
    </content>
  </returnValue>
  <languageReferenceRemarks>
    <content>
      <para>If <legacyItalic>NumChar</legacyItalic> is more than the number of characters left in the stream, only the characters remaining are returned. The string read is not padded to match the length specified by <legacyItalic>NumChar</legacyItalic>. If there are no characters left to read, a variant whose value is null is returned. <legacyBold>ReadText</legacyBold> cannot be used to read backwards.</para>
      <alert class="note">
        <para>The <legacyBold>ReadText</legacyBold> method is used with text streams (<legacyLink xlink:href="f6a17e8c-7a28-48d0-bded-76b9e0cf7639">Type</legacyLink> is <legacyBold>adTypeText</legacyBold>). For binary streams (<legacyBold>Type</legacyBold> is <legacyBold>adTypeBinary</legacyBold>), use <legacyLink xlink:href="838502de-80f1-4eeb-8838-dd3d9403e567">Read</legacyLink>.</para>
      </alert>
      <para>Queries that result in a large amount of XML data being returned through the <legacyBold>ReadText</legacyBold> method of the ActiveX Data Object (ADO) Stream object may take a great deal of time to execute; if this is done in a COM+ component that is invoked from an ASP page, the user's session may time out. ADO converts Stream object data from UTF-8 encoding to Unicode; the frequent memory reallocation involved in conversion of such a large quantity of data at once is quite time-consuming. To resolve, make repeated calls to the <legacyBold>ReadText</legacyBold> method of the ADO command object, and specify a smaller number of characters. Tests have shown that a value equivalent to 128K (131,072) is optimal. Response time decreases as this value is decreased. For more information, see Knowledge Base article 280067, "PRB: Retrieving very large XML Documents from SQL Server 2000 by using ReadText method of ADO stream object may be slow", in the Microsoft Knowledge Base at http://support.microsoft.com.</para>
    </content>
  </languageReferenceRemarks>
  <section>
    <title>Applies To</title>
    <content>
      <para>
        <link xlink:href="0514531f-009d-4519-abc3-d727014a39f1">Stream</link>
      </para>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="838502de-80f1-4eeb-8838-dd3d9403e567">Read Method</link>
</relatedTopics>
</developerReferenceWithSyntaxDocument>