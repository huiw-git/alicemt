---
title: "Append Method (ADOX Columns)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: 7a46d23c-efef-4ec7-815d-cd3ac86787dd
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
# Append Method (ADOX Columns)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Adds a new <legacyLink xlink:href="6e772783-1bc8-4ea7-94b2-7d7a52ea5c47">Column</legacyLink> object to the <legacyLink xlink:href="23b9fea8-4f76-4a51-95ce-1a6ce4560b34">Columns</legacyLink> collection.</para>
  </introduction>
  <syntaxSection>
    <legacySyntax>
<parameterReference>Columns</parameterReference><legacyBold>.Append </legacyBold><parameterReference>Column</parameterReference> [<legacyBold>,</legacyBold><parameterReference>Type</parameterReference>] [<legacyBold>,</legacyBold><parameterReference>DefinedSize</parameterReference>]</legacySyntax>
  </syntaxSection>
  <parameters>
    <content>
      <definitionTable>
        <definedTerm> <legacyItalic>Column</legacyItalic> </definedTerm>
        <definition>
          <para>The <legacyBold>Column</legacyBold> object to append or the name of the column to create and append.</para>
        </definition>
        <definedTerm> <legacyItalic>Type</legacyItalic> </definedTerm>
        <definition>
          <para>Optional. A <legacyBold>Long</legacyBold> value that specifies the data type of the column. The <legacyItalic>Type </legacyItalic>parameter corresponds to the <legacyLink xlink:href="5c6718b6-f728-478a-8afb-5d17b0a91d1f">Type</legacyLink> property of a <legacyBold>Column</legacyBold> object.</para>
        </definition>
        <definedTerm> <legacyItalic>DefinedSize</legacyItalic> </definedTerm>
        <definition>
          <para>Optional. A <legacyBold>Long</legacyBold> value that specifies the size of the column. The <legacyItalic>DefinedSize</legacyItalic> parameter corresponds to the <legacyLink xlink:href="762b8937-c31c-4e90-bb85-506d991e8280">DefinedSize</legacyLink> property of a <legacyBold>Column</legacyBold> object.</para>
        </definition>
      </definitionTable>
      <alert class="note">
        <para>An error will occur when appending a <legacyBold>Column</legacyBold> to the <legacyBold>Columns</legacyBold> collection of an <legacyLink xlink:href="6b9578c0-bc94-46b9-b801-c18e14b04b31">Index</legacyLink> if the <legacyBold>Column</legacyBold> does not exist in a <legacyLink xlink:href="a6d74000-0828-49ba-850a-63da865f8802">Table</legacyLink> that is already appended to the <legacyLink xlink:href="38d750e7-f3fb-426e-b4b4-55eea4f1a654">Tables</legacyLink> collection.</para>
      </alert>
    </content>
  </parameters>
  <section>
    <title>Applies To</title>
    <content>
      <para>
        <link xlink:href="23b9fea8-4f76-4a51-95ce-1a6ce4560b34">Columns Collection (ADOX)</link>
      </para>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="678e5546-df5d-4cd0-bfe9-6cf13cb385c0">Columns and Tables Append Methods, Name Property Example (VB)</link>
<link xlink:href="13b5b1c3-6af6-439e-bb65-976578ba6bc2">Keys Append Method, Key Type, RelatedColumn, RelatedTable and UpdateRule Properties Example (VB)</link>
<link xlink:href="448bc850-7584-4c5f-89f3-5f4fee88b259">ParentCatalog Property Example (VB)</link>
<link xlink:href="56b94fc6-7ef0-4e4a-82a3-033b94c46036">Append Method (Groups)</link>
<link xlink:href="6695769f-275b-4b70-81bd-1a5f7d74926c">Append Method (Indexes)</link>
<link xlink:href="215a5391-f422-42ec-99ea-4e6fbb5d3d64">Append Method (Keys)</link>
<link xlink:href="38e3492c-c1e1-42e3-a71a-befdc90204db">Append Method (Procedures)</link>
<link xlink:href="a362ed51-314c-4783-9598-538dbf755f3d">Append Method (Tables)</link>
<link xlink:href="b80bc5d5-78ca-4f75-956b-2ac658029cc7">Append Method (Users)</link>
<link xlink:href="6070fd58-3237-4c77-a966-5b39ce5d57e4">Append Method (Views)</link>
</relatedTopics>
</developerReferenceWithSyntaxDocument>