---
title: "Append Method (ADOX Views)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: 6070fd58-3237-4c77-a966-5b39ce5d57e4
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
# Append Method (ADOX Views)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Creates a new <legacyLink xlink:href="653421ce-7b94-43d0-9bc6-4900f8f2af45">View</legacyLink> object and appends it to the <legacyLink xlink:href="a55d380c-2b7b-4b57-af74-8ba0b3de0db9">Views</legacyLink> collection.</para>
  </introduction>
  <syntaxSection>
    <legacySyntax>
<parameterReference>Views</parameterReference><legacyBold>.Append </legacyBold><parameterReference>Name</parameterReference><legacyBold>,</legacyBold> <parameterReference>Command</parameterReference></legacySyntax>
  </syntaxSection>
  <parameters>
    <content>
      <definitionTable>
        <definedTerm> <parameterReference>Name </parameterReference></definedTerm>
        <definition>
          <para>A <languageKeyword>String</languageKeyword> value that specifies the name of the view to create.</para>
        </definition>
        <definedTerm> <parameterReference>Command </parameterReference></definedTerm>
        <definition>
          <para>An ADO <legacyLink xlink:href="a02c22fb-542d-465e-a629-30fd59dcbebf">Command</legacyLink> object that represents the view to create.</para>
        </definition>
      </definitionTable>
    </content>
  </parameters>
  <languageReferenceRemarks>
    <content>
      <para>Creates a new view in the data source with the name and attributes specified in the <legacyBold>Command</legacyBold> object.</para>
      <para>If the command text that the user specifies represents a procedure rather than a view, the behavior is dependent upon the provider. <legacyBold>Append</legacyBold> will fail if the provider does not support persisting commands.</para>
      <alert class="note">
        <para>When using the OLE DB Provider for Microsoft Jet, the <legacyBold>Views</legacyBold> collection <legacyBold>Append</legacyBold> method will allow you to specify a <legacyBold>Procedure</legacyBold> rather than a <legacyBold>View</legacyBold> in the <legacyItalic>Command</legacyItalic> parameter. The <legacyBold>Procedure</legacyBold> will be added to the data source and will be added to the <legacyBold>Views</legacyBold> collection. After the <legacyBold>Append</legacyBold>, if the <legacyBold>Procedures</legacyBold> and <legacyBold>Views</legacyBold> collections are refreshed, the <legacyBold>Procedure</legacyBold> will no longer be in the <legacyBold>Views</legacyBold> collection and will appear in the <legacyBold>Procedures</legacyBold> collection.</para>
      </alert>
    </content>
  </languageReferenceRemarks>
  <section>
    <title>Applies To</title>
    <content>
      <para>
        <link xlink:href="a55d380c-2b7b-4b57-af74-8ba0b3de0db9">Views Collection (ADOX)</link>
      </para>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="b5b4c082-ac29-4f49-a8b8-e21b554c9b0d">Views Append Method Example (VB)</link>
<link xlink:href="7a46d23c-efef-4ec7-815d-cd3ac86787dd">Append Method (Columns)</link>
<link xlink:href="56b94fc6-7ef0-4e4a-82a3-033b94c46036">Append Method (Groups)</link>
<link xlink:href="6695769f-275b-4b70-81bd-1a5f7d74926c">Append Method (Indexes)</link>
<link xlink:href="215a5391-f422-42ec-99ea-4e6fbb5d3d64">Append Method (Keys)</link>
<link xlink:href="38e3492c-c1e1-42e3-a71a-befdc90204db">Append Method (Procedures)</link>
<link xlink:href="a362ed51-314c-4783-9598-538dbf755f3d">Append Method (Tables)</link>
<link xlink:href="b80bc5d5-78ca-4f75-956b-2ac658029cc7">Append Method (Users)</link>
</relatedTopics>
</developerReferenceWithSyntaxDocument>