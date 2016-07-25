---
title: "Append Method (ADOX Keys)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: 215a5391-f422-42ec-99ea-4e6fbb5d3d64
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
# Append Method (ADOX Keys)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Adds a new <legacyLink xlink:href="55f116fe-4d56-4892-bffe-0cdd6fc727c9">Key</legacyLink> object to the <legacyLink xlink:href="cdb31c76-e559-475c-b33a-aac24f73e70e">Keys</legacyLink> collection.</para>
  </introduction>
  <syntaxSection>
    <legacySyntax>
<parameterReference>Keys</parameterReference><legacyBold>.Append </legacyBold><parameterReference>Key</parameterReference> [<legacyBold>,</legacyBold><parameterReference>KeyType</parameterReference>] [<legacyBold>,</legacyBold><parameterReference>Column</parameterReference>] [<legacyBold>,</legacyBold><parameterReference>RelatedTable</parameterReference>] [<legacyBold>,</legacyBold><parameterReference>RelatedColumn</parameterReference>]</legacySyntax>
  </syntaxSection>
  <parameters>
    <content>
      <definitionTable>
        <definedTerm> <legacyItalic>Key</legacyItalic> </definedTerm>
        <definition>
          <para>The <unmanagedCodeEntityReference>Key</unmanagedCodeEntityReference> object to append or the name of the key to create and append.</para>
        </definition>
        <definedTerm> <legacyItalic>KeyType</legacyItalic> </definedTerm>
        <definition>
          <para>Optional. A <languageKeyword>Long</languageKeyword> value that specifies the type of key. The <legacyItalic>Key </legacyItalic>parameter corresponds to the <legacyLink xlink:href="8ca2f1fd-eb1e-490c-a28b-67eda92e0fc7">Type</legacyLink> property of a <unmanagedCodeEntityReference>Key</unmanagedCodeEntityReference> object.</para>
        </definition>
        <definedTerm> <legacyItalic>Column</legacyItalic> </definedTerm>
        <definition>
          <para>Optional. A <languageKeyword>String</languageKeyword> value that specifies the name of the column to be indexed. The <legacyItalic>Columns </legacyItalic>parameter corresponds to the value of the <legacyLink xlink:href="81b92baf-b6b9-4f4e-9f33-4503795518cd">Name</legacyLink> property of a <legacyLink xlink:href="6e772783-1bc8-4ea7-94b2-7d7a52ea5c47">Column</legacyLink> object.</para>
        </definition>
        <definedTerm> <legacyItalic>RelatedTable</legacyItalic> </definedTerm>
        <definition>
          <para>Optional. A <languageKeyword>String</languageKeyword> value that specifies the name of the related table. The <legacyItalic>RelatedTable </legacyItalic>parameter corresponds to the value of the <unmanagedCodeEntityReference>Name</unmanagedCodeEntityReference> property of a <legacyLink xlink:href="a6d74000-0828-49ba-850a-63da865f8802">Table</legacyLink> object.</para>
        </definition>
        <definedTerm> <legacyItalic>RelatedColumn</legacyItalic> </definedTerm>
        <definition>
          <para>Optional. A <languageKeyword>String</languageKeyword> value that specifies the name of the related column for a foreign key. The <parameterReference>RelatedColumn</parameterReference> parameter corresponds to the value of the <unmanagedCodeEntityReference>Name</unmanagedCodeEntityReference> property of a <legacyLink xlink:href="6e772783-1bc8-4ea7-94b2-7d7a52ea5c47">Column</legacyLink> object.</para>
        </definition>
      </definitionTable>
    </content>
  </parameters>
  <languageReferenceRemarks>
    <content>
      <para>The <legacyItalic>Columns</legacyItalic> parameter can take either the name of a column or an array of column names.</para>
    </content>
  </languageReferenceRemarks>
  <section>
    <title>Applies To</title>
    <content>
      <para>
        <link xlink:href="cdb31c76-e559-475c-b33a-aac24f73e70e">Keys Collection (ADOX)</link>
      </para>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="13b5b1c3-6af6-439e-bb65-976578ba6bc2">Keys Append Method, Key Type, RelatedColumn, RelatedTable and UpdateRule Properties Example (VB)</link>
<link xlink:href="7a46d23c-efef-4ec7-815d-cd3ac86787dd">Append Method (Columns)</link>
<link xlink:href="56b94fc6-7ef0-4e4a-82a3-033b94c46036">Append Method (Groups)</link>
<link xlink:href="6695769f-275b-4b70-81bd-1a5f7d74926c">Append Method (Indexes)</link>
<link xlink:href="38e3492c-c1e1-42e3-a71a-befdc90204db">Append Method (Procedures)</link>
<link xlink:href="a362ed51-314c-4783-9598-538dbf755f3d">Append Method (Tables)</link>
<link xlink:href="b80bc5d5-78ca-4f75-956b-2ac658029cc7">Append Method (Users)</link>
<link xlink:href="6070fd58-3237-4c77-a966-5b39ce5d57e4">Append Method (Views)</link>
</relatedTopics>
</developerReferenceWithSyntaxDocument>