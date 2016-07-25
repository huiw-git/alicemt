---
title: "Key Object (ADOX)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: 55f116fe-4d56-4892-bffe-0cdd6fc727c9
caps.latest.revision: 8
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
# Key Object (ADOX)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Represents a primary, foreign, or unique key field from a database table.</para>
  </introduction>
  <languageReferenceRemarks>
    <content>
      <para>The following code creates a new <legacyBold>Key</legacyBold>:</para>
      <code>Dim obj As New Key</code>
      <para>With the properties and collections of a <legacyBold>Key</legacyBold> object, you can:

</para>
      <list class="bullet">
        <listItem>
          <para>Identify the key with the <legacyLink xlink:href="81b92baf-b6b9-4f4e-9f33-4503795518cd">Name</legacyLink> property.</para>
        </listItem>
        <listItem>
          <para>Determine whether the key is primary, foreign, or unique with the <legacyLink xlink:href="8ca2f1fd-eb1e-490c-a28b-67eda92e0fc7">Type</legacyLink> property.</para>
        </listItem>
        <listItem>
          <para>Access the database columns of the key with the <legacyLink xlink:href="23b9fea8-4f76-4a51-95ce-1a6ce4560b34">Columns</legacyLink> collection.</para>
        </listItem>
        <listItem>
          <para>Specify the name of the related table with the <legacyLink xlink:href="cb54c6bc-2be2-40b1-bc11-90c10651b878">RelatedTable</legacyLink> property.</para>
        </listItem>
        <listItem>
          <para>Determine the action performed on deletion or update of a primary key with the <legacyLink xlink:href="87bd4c0a-cae3-4007-a939-4193acaa00ac">DeleteRule</legacyLink> and <legacyLink xlink:href="f4e21060-40cb-4790-8611-4086a092dda2">UpdateRule</legacyLink> properties.</para>
        </listItem>
      </list>
      <para>This section contains the following topic.

</para>
      <list class="bullet">
        <listItem>
          <para>
            <legacyLink xlink:href="fba47748-53dd-4a5c-8c00-72e48bbc5bb0">Key Object Properties, Methods, and Events</legacyLink>
          </para>
        </listItem>
      </list>
    </content>
  </languageReferenceRemarks>
  <relatedTopics>
<link xlink:href="13b5b1c3-6af6-439e-bb65-976578ba6bc2">Keys Append Method, Key Type, RelatedColumn, RelatedTable and UpdateRule Properties Example (VB)</link>
<link xlink:href="23b9fea8-4f76-4a51-95ce-1a6ce4560b34">Columns Collection</link>
<link xlink:href="cdb31c76-e559-475c-b33a-aac24f73e70e">Keys Collection</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>