---
title: "Open Method (ADO MD)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: a87d8080-a238-45e5-bc80-9a8625b3810f
caps.latest.revision: 13
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
# Open Method (ADO MD)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Retrieves the results of a multidimensional query and returns the results to a <legacyLink xlink:href="5e2452c0-cac0-49b2-8099-836c35794d50">Cellset</legacyLink>.</para>
  </introduction>
  <syntaxSection>
    <legacySyntax>
<parameterReference>Cellset</parameterReference>.<legacyBold>Open </legacyBold><parameterReference>Source</parameterReference><legacyBold>, </legacyBold><parameterReference>ActiveConnection</parameterReference></legacySyntax>
  </syntaxSection>
  <parameters>
    <content>
      <definitionTable>
        <definedTerm> <legacyItalic>Source</legacyItalic> </definedTerm>
        <definition>
          <para>Optional. A <languageKeyword>Variant</languageKeyword> that evaluates to a valid multidimensional query, such as a Multidimensional Expression (MDX) query. The <legacyItalic>Source </legacyItalic>argument corresponds to the <legacyLink xlink:href="875a99ea-7f1a-4570-87b1-5ecbebbcf845">Source</legacyLink> property. For more information about MDX, see the <legacyLink xlink:href="8a7673c6-3ca1-4411-9f1e-adf1e47df4f3">OLE DB for Online Analytical Processing (OLAP)</legacyLink> documentation in the Microsoft Data Access Components SDK.</para>
        </definition>
        <definedTerm> <legacyItalic>ActiveConnection</legacyItalic> </definedTerm>
        <definition>
          <para>Optional. A <languageKeyword>Variant</languageKeyword> that evaluates to a string specifying either a valid ADO <legacyLink xlink:href="ef6b1824-5b12-43db-89d7-8f3d13896d4d">Connection</legacyLink> object variable name or a definition for a connection. The <legacyItalic>ActiveConnection </legacyItalic>argument specifies the connection in which to open the <legacyLink xlink:href="5e2452c0-cac0-49b2-8099-836c35794d50">Cellset</legacyLink> object. If you pass a connection definition for this argument, ADO opens a new connection using the specified parameters. The <legacyItalic>ActiveConnection </legacyItalic>argument corresponds to the <legacyLink xlink:href="2509b32c-a995-4364-9152-d8c83129bdd8">ActiveConnection</legacyLink> property.</para>
        </definition>
      </definitionTable>
    </content>
  </parameters>
  <languageReferenceRemarks>
    <content>
      <para>The <unmanagedCodeEntityReference>Open</unmanagedCodeEntityReference> method generates an error if either of its parameters is omitted and its corresponding property value has not been set prior to attempting to open the <unmanagedCodeEntityReference>Cellset</unmanagedCodeEntityReference>.</para>
    </content>
  </languageReferenceRemarks>
  <section>
    <title>Applies To</title>
    <content>
      <para>
        <link xlink:href="5e2452c0-cac0-49b2-8099-836c35794d50">Cellset Object (ADO MD)</link>
      </para>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="2666ad1c-b48e-4b2c-b269-5a9f4e4a7810">Visual Basic Example</link>
<link xlink:href="2509b32c-a995-4364-9152-d8c83129bdd8">ActiveConnection Property</link>
<link xlink:href="a3aa594d-f9d4-4654-8625-ec20153ff5d9">Close Method</link>
<link xlink:href="ef6b1824-5b12-43db-89d7-8f3d13896d4d">Connection Object</link>
<link xlink:href="875a99ea-7f1a-4570-87b1-5ecbebbcf845">Source Property</link>
<link xlink:href="06d480ca-9eb6-4570-a45d-a73539bddd32">State Property</link>
</relatedTopics>
</developerReferenceWithSyntaxDocument>