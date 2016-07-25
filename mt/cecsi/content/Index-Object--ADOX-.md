---
title: "Index Object (ADOX)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: 6b9578c0-bc94-46b9-b801-c18e14b04b31
caps.latest.revision: 9
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
# Index Object (ADOX)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Represents an index from a database table.</para>
  </introduction>
  <languageReferenceRemarks>
    <content>
      <para>The following code creates a new <legacyBold>Index</legacyBold>:</para>
      <code>Dim obj As New Index</code>
      <para>With the properties and collections of an <legacyBold>Index</legacyBold> object, you can:  </para>
      <list class="bullet">
        <listItem>
          <para>Identify the index with the <legacyLink xlink:href="81b92baf-b6b9-4f4e-9f33-4503795518cd">Name</legacyLink> property.</para>
        </listItem>
        <listItem>
          <para>Access the database columns of the index with the <legacyLink xlink:href="23b9fea8-4f76-4a51-95ce-1a6ce4560b34">Columns</legacyLink> collection.</para>
        </listItem>
        <listItem>
          <para>Specify whether the index keys must be unique with the <legacyLink xlink:href="85fd4bd0-393b-4dc1-9d73-80dced4f2fbe">Unique</legacyLink> property.</para>
        </listItem>
        <listItem>
          <para>Specify whether the index is the primary key for a table with the <legacyLink xlink:href="30185312-5e09-4804-852d-e505d660113a">PrimaryKey</legacyLink> property.</para>
        </listItem>
        <listItem>
          <para>Specify whether records that have null values in their index fields have index entries with the <legacyLink xlink:href="313b0bf7-3f37-4823-8fca-bd9c80e078a7">IndexNulls</legacyLink> property.</para>
        </listItem>
        <listItem>
          <para>Specify whether the index is clustered with the <legacyLink xlink:href="9b62fb35-de43-425a-83ca-77af4e33fea9">Clustered</legacyLink> property.</para>
        </listItem>
        <listItem>
          <para>Access provider-specific index properties with the <legacyLink xlink:href="1d539aa8-ce0d-4418-ab03-8d0a3c1e9d82">Properties</legacyLink> collection.</para>
        </listItem>
      </list>
      <alert class="note">
        <para>An error will occur when appending a <legacyLink xlink:href="6e772783-1bc8-4ea7-94b2-7d7a52ea5c47">Column</legacyLink> to the <legacyBold>Columns</legacyBold> collection of an <legacyBold>Index</legacyBold> if the <legacyBold>Column</legacyBold> does not exist in a <legacyLink xlink:href="a6d74000-0828-49ba-850a-63da865f8802">Table</legacyLink> object already appended to the <legacyLink xlink:href="38d750e7-f3fb-426e-b4b4-55eea4f1a654">Tables</legacyLink> collection.</para>
      </alert>
      <alert class="note">
        <para>Your data provider may not support all properties of <legacyBold>Index</legacyBold> objects. An error will occur if you have set a value for a property that is not supported by the provider. For new <legacyBold>Index</legacyBold> objects, the error will occur when the object is appended to the collection. For existing objects, the error will occur when setting the property.</para>
      </alert>
      <alert class="note">
        <para>When creating <legacyBold>Index</legacyBold> objects, the existence of an appropriate default value for an optional property does not guarantee that your provider supports the property. For more information about which properties your provider supports, see your provider documentation.</para>
      </alert>
      <para>This section contains the following topic.  </para>
      <list class="bullet">
        <listItem>
          <para>
            <legacyLink xlink:href="6f4e92e1-e7cb-45d8-aa86-cd749474f825">Index Object Properties, Methods, and Events</legacyLink>           </para>
        </listItem>
      </list>
    </content>
  </languageReferenceRemarks>
  <relatedTopics>
<link xlink:href="50f87e27-1bf9-427c-9b1d-704a672434d2">Indexes Append Method Example (VB)</link>
<link xlink:href="45204669-32c0-4690-aab9-ddf0fd71ae48">IndexNulls Property Example (VB)</link>
<link xlink:href="f536acac-06ea-4b39-bfba-ee9902b01615">PrimaryKey and Unique Properties Example (VB)</link>
<link xlink:href="d9502254-d89b-4bcb-94f1-6418f89e7f30">SortOrder Property Example (VB)</link>
<link xlink:href="23b9fea8-4f76-4a51-95ce-1a6ce4560b34">Columns Collection</link>
<link xlink:href="184cf536-455c-42be-bf1c-a5c25bade961">Indexes Collection</link>
<link xlink:href="1d539aa8-ce0d-4418-ab03-8d0a3c1e9d82">Properties Collection</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>