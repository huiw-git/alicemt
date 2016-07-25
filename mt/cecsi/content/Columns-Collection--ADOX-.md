---
title: "Columns Collection (ADOX)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: 23b9fea8-4f76-4a51-95ce-1a6ce4560b34
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
# Columns Collection (ADOX)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Contains all <legacyLink xlink:href="6e772783-1bc8-4ea7-94b2-7d7a52ea5c47">Column</legacyLink> objects of a table, index, or key.</para>
  </introduction>
  <languageReferenceRemarks>
    <content>
      <para>The <legacyLink xlink:href="7a46d23c-efef-4ec7-815d-cd3ac86787dd">Append</legacyLink> method for a <legacyBold>Columns</legacyBold> collection is unique for ADOX. You can:

</para>
      <list class="bullet">
        <listItem>
          <para>Add a new column to the collection with the <legacyBold>Append</legacyBold> method.</para>
        </listItem>
      </list>
      <para>The remaining properties and methods are standard to ADO collections. You can:

</para>
      <list class="bullet">
        <listItem>
          <para>Access a column in the collection with the <legacyLink xlink:href="e11484bb-c5c7-42d8-9bb8-21572125d727">Item</legacyLink> property.</para>
        </listItem>
        <listItem>
          <para>Return the number of columns contained in the collection with the <legacyLink xlink:href="da9ccd1f-d402-41a2-940c-45556fc5340d">Count</legacyLink> property.</para>
        </listItem>
        <listItem>
          <para>Remove a column from the collection with the <legacyLink xlink:href="e6b6e3a4-8952-4d79-81f4-51019c338374">Delete</legacyLink> method.</para>
        </listItem>
        <listItem>
          <para>Update the objects in the collection to reflect the current database's schema with the <legacyLink xlink:href="089b7ca7-684f-4259-8032-5bd1ecc54426">Refresh</legacyLink> method.</para>
        </listItem>
      </list>
      <alert class="note">
        <para>An error will occur when appending a <legacyBold>Column</legacyBold> to the <legacyBold>Columns</legacyBold> collection of an <legacyLink xlink:href="6b9578c0-bc94-46b9-b801-c18e14b04b31">Index</legacyLink> if the <legacyBold>Column</legacyBold> does not exist in a <legacyLink xlink:href="a6d74000-0828-49ba-850a-63da865f8802">Table</legacyLink> that is already appended to the <legacyLink xlink:href="38d750e7-f3fb-426e-b4b4-55eea4f1a654">Tables</legacyLink> collection.</para>
      </alert>
      <para>This section contains the following topic.

</para>
      <list class="bullet">
        <listItem>
          <para>
            <legacyLink xlink:href="3d9ec89a-cc85-4091-b6f0-2bb6a6826d5e">Columns Collection Properties, Methods, and Events</legacyLink>
          </para>
        </listItem>
      </list>
    </content>
  </languageReferenceRemarks>
  <relatedTopics>
<link xlink:href="678e5546-df5d-4cd0-bfe9-6cf13cb385c0">Columns and Tables Append Methods, Name Property Example (VB)</link>
<link xlink:href="f88e7a3b-19ed-46e2-b2ce-3b611d9b8166">Connection Close Method, Table Type Property Example (VB)</link>
<link xlink:href="13b5b1c3-6af6-439e-bb65-976578ba6bc2">Keys Append Method, Key Type, RelatedColumn, RelatedTable and UpdateRule Properties Example (VB)</link>
<link xlink:href="448bc850-7584-4c5f-89f3-5f4fee88b259">ParentCatalog Property Example (VB)</link>
<link xlink:href="d9502254-d89b-4bcb-94f1-6418f89e7f30">SortOrder Property Example (VB)</link>
<link xlink:href="6e772783-1bc8-4ea7-94b2-7d7a52ea5c47">Column Object</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>