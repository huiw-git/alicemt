---
title: "Hierarchy Object (ADO MD)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: 034af340-ac79-494e-ba5e-2b57da1cb9de
caps.latest.revision: 10
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
# Hierarchy Object (ADO MD)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Represents one way in which the members of a <legacyLink xlink:href="66adbbd2-23a3-4c19-a91b-84c31309aa1b">dimension</legacyLink> can be aggregated or "rolled up." A dimension can be aggregated along one or more hierarchies.</para>
  </introduction>
  <languageReferenceRemarks>
    <content>
      <para>With the collections and properties of a <legacyBold>Hierarchy</legacyBold> object, you can do the following:  </para>
      <list class="bullet">
        <listItem>
          <para>Identify the <legacyBold>Hierarchy</legacyBold> with the <legacyLink xlink:href="4a04380b-51dc-4aaf-8d25-123cdd589641">Name</legacyLink> and <legacyLink xlink:href="5b977956-e252-4861-8425-f1aaf6b80130">UniqueName</legacyLink> properties.</para>
        </listItem>
        <listItem>
          <para>Return a meaningful string that describes the <legacyBold>Hierarchy</legacyBold> with the <legacyLink xlink:href="6d626d35-0bf3-4f24-9934-ad9c9c91273a">Description</legacyLink> property.</para>
        </listItem>
        <listItem>
          <para>Return the <legacyLink xlink:href="37815869-ed30-45fd-9aea-0a986c1b305c">Level</legacyLink> objects that make up the <legacyBold>Hierarchy</legacyBold> with the <legacyLink xlink:href="fed8684a-b428-4ee4-8f8d-928abe4ad9ad">Levels</legacyLink> collection.</para>
        </listItem>
        <listItem>
          <para>Use the standard ADO <legacyLink xlink:href="1d539aa8-ce0d-4418-ab03-8d0a3c1e9d82">Properties</legacyLink> collection to obtain additional information about the <legacyBold>Hierarchy</legacyBold> object.</para>
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
              <para>AllMember</para>
            </TD>
            <TD>
              <para>The member at the highest level of rollup in the hierarchy.</para>
            </TD>
          </tr>
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
              <para>DefaultMember</para>
            </TD>
            <TD>
              <para>The unique name of the default member for this hierarchy.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Description</para>
            </TD>
            <TD>
              <para>A meaningful description of the hierarchy.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>DimensionType</para>
            </TD>
            <TD>
              <para>The type of dimension to which this hierarchy belongs.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>DimensionUniqueName</para>
            </TD>
            <TD>
              <para>The unambiguous name of the dimension.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>HierarchyCaption</para>
            </TD>
            <TD>
              <para>A label or caption associated with the hierarchy.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>HierarchyCardinality</para>
            </TD>
            <TD>
              <para>The number of members in the hierarchy. </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>HierarchyGUID</para>
            </TD>
            <TD>
              <para>The GUID of the hierarchy.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>HierarchyName</para>
            </TD>
            <TD>
              <para>The name of the hierarchy.</para>
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
            <legacyLink xlink:href="8ec0b00e-0e18-4f1b-9bbf-42168670bf5f">Properties, Methods, and Events</legacyLink>           </para>
        </listItem>
      </list>
    </content>
  </languageReferenceRemarks>
  <relatedTopics>
<link xlink:href="4d72a912-ef53-4989-9fca-214937574116">VBScript Example</link>
<link xlink:href="66adbbd2-23a3-4c19-a91b-84c31309aa1b">Dimension Object</link>
<link xlink:href="bef0fcb1-8060-4faa-84f0-3d52e9c4526f">Hierarchies Collection</link>
<link xlink:href="fed8684a-b428-4ee4-8f8d-928abe4ad9ad">Levels Collection</link>
<link xlink:href="1d539aa8-ce0d-4418-ab03-8d0a3c1e9d82">Properties Collection</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>