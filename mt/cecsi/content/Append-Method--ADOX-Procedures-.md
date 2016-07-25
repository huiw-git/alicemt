---
title: "Append Method (ADOX Procedures)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: 38e3492c-c1e1-42e3-a71a-befdc90204db
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
# Append Method (ADOX Procedures)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Adds a new <legacyLink xlink:href="927bcf3e-32f5-4a80-98d3-600779f0732e">Procedure</legacyLink> object to the <legacyLink xlink:href="dc7a38e1-93b9-4034-9af2-ff419e8fb2a3">Procedures</legacyLink> collection.</para>
  </introduction>
  <syntaxSection>
    <legacySyntax>
<parameterReference>Procedures</parameterReference><legacyBold>.Append </legacyBold><parameterReference>Name</parameterReference><legacyBold>,</legacyBold> <parameterReference>Command</parameterReference></legacySyntax>
  </syntaxSection>
  <parameters>
    <content>
      <definitionTable>
        <definedTerm> <legacyItalic>Name</legacyItalic> </definedTerm>
        <definition>
          <para>A <legacyBold>String</legacyBold> value that specifies the name of the procedure to create and append.</para>
        </definition>
        <definedTerm> <legacyItalic>Command</legacyItalic> </definedTerm>
        <definition>
          <para>An ADO <legacyLink xlink:href="a02c22fb-542d-465e-a629-30fd59dcbebf">Command</legacyLink> object that represents the procedure to create and append.</para>
        </definition>
      </definitionTable>
    </content>
  </parameters>
  <languageReferenceRemarks>
    <content>
      <para>Creates a new procedure in the data source with the name and attributes specified in the <legacyBold>Command</legacyBold> object.</para>
      <para>If the command text that the user specifies represents a view rather than a procedure, the behavior is dependent upon the provider being used. <legacyBold>Append</legacyBold> will fail if the provider does not support persisting commands.</para>
      <alert class="note">
        <para>When using the OLE DB Provider for Microsoft Jet, the <legacyBold>Procedures</legacyBold> collection <legacyBold>Append</legacyBold> method will allow you to specify a <legacyBold>View</legacyBold> rather than a <legacyBold>Procedure</legacyBold> in the <legacyItalic>Command</legacyItalic> parameter. The <legacyBold>View</legacyBold> will be added to the data source and will be added to the <legacyBold>Procedures</legacyBold> collection. After the <legacyBold>Append</legacyBold>, if the <legacyBold>Procedures</legacyBold> and <legacyBold>Views</legacyBold> collections are refreshed, the <legacyBold>View</legacyBold> will no longer be in the <legacyBold>Procedures</legacyBold> collection and will appear in the <legacyBold>Views</legacyBold> collection.</para>
      </alert>
    </content>
  </languageReferenceRemarks>
  <section>
    <title>Applies To</title>
    <content>
      <para>
        <link xlink:href="dc7a38e1-93b9-4034-9af2-ff419e8fb2a3">Procedures Collection (ADOX)</link>
      </para>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="ce83b966-474b-4f57-8eb9-370996dfc5c0">Procedures Append Method Example (VB)</link>
<link xlink:href="7a46d23c-efef-4ec7-815d-cd3ac86787dd">Append Method (Columns)</link>
<link xlink:href="56b94fc6-7ef0-4e4a-82a3-033b94c46036">Append Method (Groups)</link>
<link xlink:href="6695769f-275b-4b70-81bd-1a5f7d74926c">Append Method (Indexes)</link>
<link xlink:href="215a5391-f422-42ec-99ea-4e6fbb5d3d64">Append Method (Keys)</link>
<link xlink:href="a362ed51-314c-4783-9598-538dbf755f3d">Append Method (Tables)</link>
<link xlink:href="b80bc5d5-78ca-4f75-956b-2ac658029cc7">Append Method (Users)</link>
<link xlink:href="6070fd58-3237-4c77-a966-5b39ce5d57e4">Append Method (Views)</link>
</relatedTopics>
</developerReferenceWithSyntaxDocument>