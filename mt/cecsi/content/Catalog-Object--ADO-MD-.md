---
title: "Catalog Object (ADO MD)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: 11f6f896-d69c-44a4-94cd-d54c93140e4a
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
# Catalog Object (ADO MD)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Contains multidimensional schema information (that is, cubes and underlying dimensions, hierarchies, levels, and members) specific to a multidimensional data provider (MDP).</para>
  </introduction>
  <languageReferenceRemarks>
    <content>
      <para>With the collections and properties of a <legacyBold>Catalog</legacyBold> object, you can do the following:  </para>
      <list class="bullet">
        <listItem>
          <para>Open the catalog by setting the <legacyLink xlink:href="2509b32c-a995-4364-9152-d8c83129bdd8">ActiveConnection</legacyLink> property to a standard ADO <legacyLink xlink:href="ef6b1824-5b12-43db-89d7-8f3d13896d4d">Connection</legacyLink> object or to a valid connection string.</para>
        </listItem>
        <listItem>
          <para>Identify the <legacyBold>Catalog</legacyBold> with the <legacyLink xlink:href="4a04380b-51dc-4aaf-8d25-123cdd589641">Name</legacyLink> property.</para>
        </listItem>
        <listItem>
          <para>Iterate through the cubes in a catalog using the <legacyLink xlink:href="c79a5e36-71fd-44c4-948d-d6a7a89bb3b5">CubeDefs</legacyLink> collection.</para>
        </listItem>
      </list>
      <para>This section contains the following topic.  </para>
      <list class="bullet">
        <listItem>
          <para>
            <legacyLink xlink:href="e9566718-9122-490d-8a8e-da8f605246f2">Properties, Methods, and Events</legacyLink>           </para>
        </listItem>
      </list>
    </content>
  </languageReferenceRemarks>
  <relatedTopics>
<link xlink:href="3aae1107-2f81-413c-8eda-ef96c3df1b8a">Visual Basic Example</link>
<link xlink:href="ef6b1824-5b12-43db-89d7-8f3d13896d4d">Connection Object</link>
<link xlink:href="c79a5e36-71fd-44c4-948d-d6a7a89bb3b5">CubeDefs Collection</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>