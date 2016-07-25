---
title: "Open Method (ADO Stream)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: d26f48fb-904e-4932-a245-3b4332ca1600
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
# Open Method (ADO Stream)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Opens a <legacyLink xlink:href="0514531f-009d-4519-abc3-d727014a39f1">Stream</legacyLink> object to manipulate streams of binary or text data.</para>
  </introduction>
  <syntaxSection>
    <legacySyntax>
<parameterReference>Stream</parameterReference><legacyBold>.Open</legacyBold> <parameterReference>Source</parameterReference><legacyBold>,</legacyBold> <parameterReference>Mode</parameterReference> <legacyBold>,</legacyBold> <parameterReference>OpenOptions</parameterReference><legacyBold>,</legacyBold> <parameterReference>UserName</parameterReference><legacyBold>,</legacyBold> <parameterReference>Password</parameterReference></legacySyntax>
  </syntaxSection>
  <parameters>
    <content>
      <definitionTable>
        <definedTerm> <legacyItalic>Source</legacyItalic> </definedTerm>
        <definition>
          <para>Optional. A <languageKeyword>Variant</languageKeyword> value that specifies the source of data for the <legacyBold>Stream</legacyBold>. <legacyItalic>Source</legacyItalic> may contain an absolute URL string that points to an existing node in a well-known tree structure, such as an e-mail or file system. A URL should be specified by using the URL keyword ("URL=<legacyItalic>scheme</legacyItalic>://<legacyItalic>server</legacyItalic>/<legacyItalic>folder</legacyItalic>"). Alternatively, <legacyItalic>Source</legacyItalic> may contain a reference to an already open <legacyLink xlink:href="db83ed2c-a8e3-460c-8682-64667e4d5d01">Record</legacyLink> object, which opens the default stream associated with the <legacyBold>Record</legacyBold>. If <legacyItalic>Source</legacyItalic> is not specified, a <legacyBold>Stream</legacyBold> is instantiated and opened, associated with no underlying source by default. For more information about URL schemes and their associated providers, see <legacyLink xlink:href="6a34a7ef-50cc-4c3d-82f7-106b9a8f3caf">Absolute and Relative URLs</legacyLink>.</para>
        </definition>
        <definedTerm> <legacyItalic>Mode</legacyItalic> </definedTerm>
        <definition>
          <para>Optional. A <legacyLink xlink:href="3792c294-5161-4538-a908-22a5fc50b85f">ConnectModeEnum</legacyLink> value that specifies the access mode for the resultant <legacyBold>Stream</legacyBold> (for example, read/write or read-only). Default value is <legacyBold>adModeUnknown</legacyBold>. See the <legacyLink xlink:href="808661eb-0d7c-4e6d-8e40-9dc3bef3d77a">Mode</legacyLink> property for more information about access modes. If <legacyItalic>Mode</legacyItalic> is not specified, it is inherited by the source object. For example, if the source <legacyBold>Record</legacyBold> is opened in read-only mode, the <legacyBold>Stream</legacyBold> will also be opened in read-only mode by default.</para>
        </definition>
        <definedTerm> <legacyItalic>OpenOptions</legacyItalic> </definedTerm>
        <definition>
          <para>Optional. A <legacyLink xlink:href="85b6c57f-47ed-46ba-bd92-07882ae9e9d2">StreamOpenOptionsEnum</legacyLink> value. Default value is <legacyBold>adOpenStreamUnspecified</legacyBold>.</para>
        </definition>
        <definedTerm> <legacyItalic>UserName</legacyItalic> </definedTerm>
        <definition>
          <para>Optional. A <legacyBold>String</legacyBold> value that contains the user identification that, if it is needed, accesses the <legacyBold>Stream</legacyBold> object.</para>
        </definition>
        <definedTerm> <legacyItalic>Password</legacyItalic> </definedTerm>
        <definition>
          <para>Optional. A <legacyBold>String</legacyBold> value that contains the password that, if it is needed, accesses the <legacyBold>Stream</legacyBold> object.</para>
        </definition>
      </definitionTable>
    </content>
  </parameters>
  <languageReferenceRemarks>
    <content>
      <para>When a <legacyBold>Record</legacyBold> object is passed in as the source parameter, the <legacyItalic>UserID</legacyItalic> and <legacyItalic>Password</legacyItalic> parameters are not used because access to the <legacyBold>Record</legacyBold> object is already available. Similarly, the <legacyLink xlink:href="808661eb-0d7c-4e6d-8e40-9dc3bef3d77a">Mode</legacyLink> of the <legacyBold>Record</legacyBold> object is transferred to the <legacyBold>Stream</legacyBold> object. When <legacyItalic>Source</legacyItalic> is not specified, the <legacyBold>Stream</legacyBold> opened contains no data and has a <legacyLink xlink:href="a487c241-d953-4c31-ae7e-6358d5cf6733">Size</legacyLink> of zero (0). To avoid losing any data that is written to this <legacyBold>Stream</legacyBold> when the <legacyBold>Stream</legacyBold> is closed, save the <legacyBold>Stream</legacyBold> with the <legacyLink xlink:href="b4aa5714-916b-48b8-8b09-cc2708379602">CopyTo</legacyLink> or <legacyLink xlink:href="8a8594f2-422b-4d2e-94f8-7fe337445900">SaveToFile</legacyLink> methods, or save it to another memory location.</para>
      <para>An <legacyItalic>OpenOptions</legacyItalic> value of <legacyBold>adOpenStreamFromRecord</legacyBold> identifies the contents of the <legacyItalic>Source</legacyItalic> parameter to be an already open <legacyBold>Record</legacyBold> object. The default behavior is to treat <legacyItalic>Source</legacyItalic> as a URL that points directly to a node in a tree structure, such as a file. The default stream associated with that node is opened.</para>
      <para>While the <legacyBold>Stream</legacyBold> is not open, it is possible to read all the read-only properties of the <legacyBold>Stream</legacyBold>. If a <legacyBold>Stream</legacyBold> is opened asynchronously, all subsequent operations (other than checking the <legacyLink xlink:href="0b993bac-2653-40b1-bcbb-5b57b6aae2bf">State</legacyLink> and other read-only properties) are blocked until the <legacyBold>Open</legacyBold> operation is completed.</para>
      <para>In addition to the options that were discussed earlier, by not specifying <legacyItalic>Source</legacyItalic>, you can create an instance of a <legacyBold>Stream</legacyBold> object in memory without associating it with an underlying source. You can dynamically add data to the stream by writing binary or text data to the <legacyBold>Stream</legacyBold> with <legacyLink xlink:href="02982e6a-ac5f-4af2-b82e-ce12534b84b2">Write</legacyLink> or <legacyLink xlink:href="7a669048-13f4-4574-a2b1-985e089729d5">WriteText</legacyLink>, or by loading data from a file with <legacyLink xlink:href="b18d8d38-7354-4a94-b637-6ac035faa433">LoadFromFile</legacyLink>.</para>
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
<link xlink:href="663defab-5545-4973-9036-24d5882c9737">Open Method (ADO Connection)</link>
<link xlink:href="ab79a623-88a9-40b6-a017-a658bf19b778">Open Method (ADO Record)</link>
<link xlink:href="3236749c-4b71-4235-89e2-ccdfaaa9319d">Open Method (ADO Recordset)</link>
<link xlink:href="850cf3ce-f18f-4e7c-8597-96c1dc504866">OpenSchema Method</link>
<link xlink:href="8a8594f2-422b-4d2e-94f8-7fe337445900">SaveToFile Method</link>
</relatedTopics>
</developerReferenceWithSyntaxDocument>