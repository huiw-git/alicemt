---
title: "Level Object (ADO MD)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: 37815869-ed30-45fd-9aea-0a986c1b305c
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
# Level Object (ADO MD)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Contains a set of members, each of which has the same rank within a hierarchy.</para>
  </introduction>
  <languageReferenceRemarks>
    <content>
      <para>With the collections and properties of a <legacyBold>Level</legacyBold> object, you can do the following:  </para>
      <list class="bullet">
        <listItem>
          <para>Identify the <legacyBold>Level</legacyBold> with the <legacyLink xlink:href="4a04380b-51dc-4aaf-8d25-123cdd589641">Name</legacyLink> and <legacyLink xlink:href="5b977956-e252-4861-8425-f1aaf6b80130">UniqueName</legacyLink> properties.</para>
        </listItem>
        <listItem>
          <para>Return a string to use when displaying the <legacyBold>Level</legacyBold> with the <legacyLink xlink:href="d90763b8-ba3f-48f8-95b2-e6a0e52296e1">Caption</legacyLink> property.</para>
        </listItem>
        <listItem>
          <para>Return a meaningful string that describes the <legacyBold>Level</legacyBold> with the <legacyLink xlink:href="6d626d35-0bf3-4f24-9934-ad9c9c91273a">Description</legacyLink> property.</para>
        </listItem>
        <listItem>
          <para>Return the <legacyLink xlink:href="3dedf755-0741-4c3f-8b4e-bff8ff8809c8">Member</legacyLink> objects that make up the <legacyBold>Level</legacyBold> with the <legacyLink xlink:href="3a647cde-efdc-4394-b1b9-8cbb1b9d689f">Members</legacyLink> collection.</para>
        </listItem>
        <listItem>
          <para>Return the number of levels from the root of the <legacyBold>Level</legacyBold> with the <legacyLink xlink:href="e41f2644-617d-4c09-80a4-feb5cf736186">Depth</legacyLink> property.</para>
        </listItem>
        <listItem>
          <para>Use the standard ADO <legacyLink xlink:href="1d539aa8-ce0d-4418-ab03-8d0a3c1e9d82">Properties</legacyLink> collection to obtain additional information about the <legacyBold>Level</legacyBold> object.</para>
        </listItem>
      </list>
      <para>The <legacyBold>Properties</legacyBold> collection contains provider-supplied properties. The following table lists properties that might be available. The actual property list may differ depending upon the implementation of the provider. See the documentation for your provider for a more complete list of available properties.</para>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>Name</para>
            </TD>
            <TD>
              <para>Description</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>CatalogName</para>
            </TD>
            <TD>
              <para>The name of the catalog to which this cube belongs.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>CubeName</para>
            </TD>
            <TD>
              <para>The name of the cube.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Description</para>
            </TD>
            <TD>
              <para>A meaningful description of the level.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>DimensionUniqueName</para>
            </TD>
            <TD>
              <para>The unambiguous name of the <legacyLink xlink:href="66adbbd2-23a3-4c19-a91b-84c31309aa1b">dimension</legacyLink>.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>HierarchyUniqueName</para>
            </TD>
            <TD>
              <para>The unambiguous name of the hierarchy.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>LevelCaption</para>
            </TD>
            <TD>
              <para>A label or caption associated with the level.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>LevelCardinality</para>
            </TD>
            <TD>
              <para>The number of members in the level.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>LevelGUID</para>
            </TD>
            <TD>
              <para>The GUID of the level.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>LevelName</para>
            </TD>
            <TD>
              <para>Name of the level.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>LevelNumber</para>
            </TD>
            <TD>
              <para>The distance between the level and the root of the hierarchy.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>LevelType</para>
            </TD>
            <TD>
              <para>The type of level.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>LevelUniqueName</para>
            </TD>
            <TD>
              <para>The unambiguous name of the level.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SchemaName</para>
            </TD>
            <TD>
              <para>The name of the schema to which this cube belongs.</para>
            </TD>
          </tr>
        </tbody>
      </table>
      <para>This section contains the following topic.  </para>
      <list class="bullet">
        <listItem>
          <para>
            <legacyLink xlink:href="fdff70b0-95d0-447f-9359-97b8d159420d">Properties, Methods, and Events</legacyLink>           </para>
        </listItem>
      </list>
    </content>
  </languageReferenceRemarks>
  <relatedTopics>
<link xlink:href="4d72a912-ef53-4989-9fca-214937574116">VBScript Example</link>
<link xlink:href="034af340-ac79-494e-ba5e-2b57da1cb9de">Hierarchy Object</link>
<link xlink:href="fed8684a-b428-4ee4-8f8d-928abe4ad9ad">Levels Collection</link>
<link xlink:href="3a647cde-efdc-4394-b1b9-8cbb1b9d689f">Members Collection</link>
<link xlink:href="1d539aa8-ce0d-4418-ab03-8d0a3c1e9d82">Properties Collection</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>