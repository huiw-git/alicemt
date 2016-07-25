---
title: "CreateParameter Method (ADO)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: 9666fdcc-0544-4ed7-a97b-c415f2a56d7e
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
# CreateParameter Method (ADO)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Creates a new <legacyLink xlink:href="e010e794-7f0f-4026-8b5b-37328e437d63">Parameter</legacyLink> object with the specified properties.</para>
  </introduction>
  <syntaxSection>
    <legacySyntax>
<legacyBold>Set</legacyBold> <parameterReference>parameter</parameterReference> = <parameterReference>command</parameterReference>.<legacyBold>CreateParameter (</legacyBold><parameterReference>Name</parameterReference><legacyBold>, </legacyBold><parameterReference>Type</parameterReference><legacyBold>, </legacyBold><parameterReference>Direction</parameterReference><legacyBold>, </legacyBold><parameterReference>Size</parameterReference><legacyBold>, </legacyBold><parameterReference>Value</parameterReference><legacyBold>)</legacyBold></legacySyntax>
  </syntaxSection>
  <returnValue>
    <content>
      <para>Returns a <legacyBold>Parameter</legacyBold> object.</para>
    </content>
  </returnValue>
  <parameters>
    <content>
      <definitionTable>
        <definedTerm> <legacyItalic>Name</legacyItalic> </definedTerm>
        <definition>
          <para>Optional. A <legacyBold>String</legacyBold> value that contains the name of the <legacyBold>Parameter</legacyBold> object.</para>
        </definition>
        <definedTerm> <legacyItalic>Type</legacyItalic> </definedTerm>
        <definition>
          <para>Optional. A <legacyLink xlink:href="2c57eca6-9336-4b06-ba10-9fef5926b1d0">DataTypeEnum</legacyLink> value that specifies the data type of the <legacyBold>Parameter</legacyBold> object.</para>
        </definition>
        <definedTerm> <legacyItalic>Direction</legacyItalic> </definedTerm>
        <definition>
          <para>Optional. A <legacyLink xlink:href="c66aa6e6-d4f0-4f0f-9640-e08ae6cfdef3">ParameterDirectionEnum</legacyLink> value that specifies the type of <legacyBold>Parameter</legacyBold> object.</para>
        </definition>
        <definedTerm> <legacyItalic>Size</legacyItalic> </definedTerm>
        <definition>
          <para>Optional. A <legacyBold>Long</legacyBold> value that specifies the maximum length for the parameter value in characters or bytes.</para>
        </definition>
        <definedTerm> <legacyItalic>Value</legacyItalic> </definedTerm>
        <definition>
          <para>Optional. A <legacyBold>Variant</legacyBold> that specifies the value for the <legacyBold>Parameter</legacyBold> object.</para>
        </definition>
      </definitionTable>
    </content>
  </parameters>
  <languageReferenceRemarks>
    <content>
      <para>Use the <legacyBold>CreateParameter</legacyBold> method to create a new <legacyBold>Parameter</legacyBold> object with a specified name, type, direction, size, and value. Any values you pass in the arguments are written to the corresponding <legacyBold>Parameter</legacyBold> properties.</para>
      <para>This method does not automatically append the <legacyBold>Parameter</legacyBold> object to the <legacyBold>Parameters</legacyBold> collection of a <legacyLink xlink:href="a02c22fb-542d-465e-a629-30fd59dcbebf">Command</legacyLink> object. This lets you set additional properties whose values ADO will validate when you append the <legacyBold>Parameter</legacyBold> object to the collection.</para>
      <para>If you specify a variable-length data type in the <legacyItalic>Type</legacyItalic> argument, you must either pass a <legacyItalic>Size</legacyItalic> argument or set the <legacyLink xlink:href="e6bad449-ebdb-4dd3-886a-9e6f1e7ee5d2">Size</legacyLink> property of the <legacyBold>Parameter</legacyBold> object before appending it to the <legacyBold>Parameters</legacyBold> collection; otherwise, an error occurs.</para>
      <para>If you specify a numeric data type (<legacyBold>adNumeric</legacyBold> or <legacyBold>adDecimal</legacyBold>) in the <legacyItalic>Type</legacyItalic> argument, then you must also set the <legacyLink xlink:href="29a02992-64be-4fcd-be13-445cba205893">NumericScale</legacyLink> and <legacyLink xlink:href="1fa38e78-6b5b-414d-ba0a-3dd26b29b766">Precision</legacyLink> properties.</para>
    </content>
  </languageReferenceRemarks>
  <section>
    <title>Applies To</title>
    <content>
      <para>
        <link xlink:href="a02c22fb-542d-465e-a629-30fd59dcbebf">Command Object</link>
      </para>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="46908cbd-434f-43e7-a794-ed0be0e0c0a7">Visual Basic Example</link>
<link xlink:href="b57d144c-0a34-49c8-94cf-e5981edfcca6">Visual C++ Example</link>
<link xlink:href="9673f232-fa58-4439-995a-b4066db628aa">Visual J++ Example</link>
<link xlink:href="f8a9bbed-ba9c-4698-945d-317ad22d2e92">Append Method</link>
<link xlink:href="e010e794-7f0f-4026-8b5b-37328e437d63">Parameter Object</link>
<link xlink:href="497cae10-3913-422a-9753-dcbb0a639b1b">Parameters Collection</link>
</relatedTopics>
</developerReferenceWithSyntaxDocument>