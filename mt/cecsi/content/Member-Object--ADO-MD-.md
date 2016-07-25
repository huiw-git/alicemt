---
title: "Member Object (ADO MD)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: 3dedf755-0741-4c3f-8b4e-bff8ff8809c8
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
# Member Object (ADO MD)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Represents a member of a level in a cube, the children of a member of a level, or a member of a position along an axis of a cellset.</para>
  </introduction>
  <languageReferenceRemarks>
    <content>
      <para>The properties of a <legacyBold>Member</legacyBold> differ depending on the context in which it is used. A <legacyBold>Member</legacyBold> of a <legacyLink xlink:href="37815869-ed30-45fd-9aea-0a986c1b305c">Level</legacyLink> in a <legacyLink xlink:href="feb2581c-fc41-471c-bb69-29f8a55fda70">CubeDef</legacyLink> has a <legacyLink xlink:href="61d36468-1ccd-467a-9cb5-17d0bfacc766">Children</legacyLink> property that returns the <legacyBold>Members</legacyBold> on the next lower level in the hierarchy from the current <legacyBold>Member</legacyBold>. For a <legacyBold>Member</legacyBold> of a <legacyLink xlink:href="91eab784-3ce9-41d6-a840-9b0939ca0608">Position</legacyLink>, the <legacyBold>Children</legacyBold> collection is always empty. Also, the <legacyLink xlink:href="34698910-64b9-41d8-8531-9de12f2b1e32">Type</legacyLink> property applies only to <legacyBold>Members</legacyBold> of a <legacyBold>Level</legacyBold>.</para>
      <para>A <legacyBold>Member</legacyBold> of <legacyBold>Position</legacyBold> has two properties that are useful when displaying the <legacyLink xlink:href="5e2452c0-cac0-49b2-8099-836c35794d50">Cellset</legacyLink>: <legacyLink xlink:href="bf39dd36-fc7a-4f6e-86c0-fa71430c0d86">DrilledDown</legacyLink> and <legacyLink xlink:href="510842e0-e8dc-4b33-9517-bd1c6df0cf3c">ParentSameAsPrev</legacyLink>. An error will occur if these properties are accessed on a <legacyBold>Member</legacyBold> of a <legacyBold>Level</legacyBold>.</para>
      <para>With the collections and properties of a <legacyBold>Member</legacyBold> object of a <legacyBold>Level</legacyBold>, you can do the following:  </para>
      <list class="bullet">
        <listItem>
          <para>Identify the <legacyBold>Member</legacyBold> with the <legacyLink xlink:href="4a04380b-51dc-4aaf-8d25-123cdd589641">Name</legacyLink> and <legacyLink xlink:href="5b977956-e252-4861-8425-f1aaf6b80130">UniqueName</legacyLink> properties.</para>
        </listItem>
        <listItem>
          <para>Return a string to use when displaying the <legacyBold>Member</legacyBold> with the <legacyLink xlink:href="d90763b8-ba3f-48f8-95b2-e6a0e52296e1">Caption</legacyLink> property.</para>
        </listItem>
        <listItem>
          <para>Return a meaningful string that describes a measure or formula <legacyBold>Member</legacyBold> with the <legacyLink xlink:href="6d626d35-0bf3-4f24-9934-ad9c9c91273a">Description</legacyLink> property.</para>
        </listItem>
        <listItem>
          <para>Determine the nature of the <legacyBold>Member</legacyBold> with the <legacyLink xlink:href="34698910-64b9-41d8-8531-9de12f2b1e32">Type</legacyLink> property.</para>
        </listItem>
        <listItem>
          <para>Obtain information about the <legacyBold>Level</legacyBold> of the <legacyBold>Member</legacyBold> with the <legacyLink xlink:href="8a1cfe2c-f207-4445-b152-ade090f64608">LevelDepth</legacyLink> and <legacyLink xlink:href="bf3b4466-9a0b-446e-9e04-fed944e3a493">LevelName</legacyLink> properties.</para>
        </listItem>
        <listItem>
          <para>Obtain related <legacyBold>Members</legacyBold> in a <legacyLink xlink:href="034af340-ac79-494e-ba5e-2b57da1cb9de">Hierarchy</legacyLink> with the <legacyLink xlink:href="32c278c1-d8e1-4bb7-9ecd-2fbfdffee34b">Parent</legacyLink> and <legacyLink xlink:href="61d36468-1ccd-467a-9cb5-17d0bfacc766">Children</legacyLink> properties.</para>
        </listItem>
        <listItem>
          <para>Count the children of a <legacyBold>Member</legacyBold> with the <legacyLink xlink:href="5463be22-ca50-43ea-9c92-468fc8eda280">ChildCount</legacyLink> property.</para>
        </listItem>
        <listItem>
          <para>Use the standard ADO <legacyLink xlink:href="1d539aa8-ce0d-4418-ab03-8d0a3c1e9d82">Properties</legacyLink> collection to obtain additional information about the <legacyBold>Level</legacyBold> object.</para>
        </listItem>
      </list>
      <para>With the collections and properties of a <legacyBold>Member</legacyBold> of a <legacyBold>Position</legacyBold> along an <legacyLink xlink:href="5f498c9a-b1e7-4e6e-9ae6-71eadaf9aada">Axis</legacyLink>, you can do the following:  </para>
      <list class="bullet">
        <listItem>
          <para>Identify the <legacyBold>Member</legacyBold> with the <legacyLink xlink:href="4a04380b-51dc-4aaf-8d25-123cdd589641">Name</legacyLink> and <legacyLink xlink:href="5b977956-e252-4861-8425-f1aaf6b80130">UniqueName</legacyLink> properties.</para>
        </listItem>
        <listItem>
          <para>Return a string to use when displaying the <legacyBold>Member</legacyBold> with the <legacyLink xlink:href="d90763b8-ba3f-48f8-95b2-e6a0e52296e1">Caption</legacyLink> property.</para>
        </listItem>
        <listItem>
          <para>Return a meaningful string that describes a measure or formula <legacyBold>Member</legacyBold> with the <legacyLink xlink:href="6d626d35-0bf3-4f24-9934-ad9c9c91273a">Description</legacyLink> property.</para>
        </listItem>
        <listItem>
          <para>Obtain information about the <legacyBold>Level</legacyBold> of the <legacyBold>Member</legacyBold> with the <legacyLink xlink:href="8a1cfe2c-f207-4445-b152-ade090f64608">LevelDepth</legacyLink> and <legacyLink xlink:href="bf3b4466-9a0b-446e-9e04-fed944e3a493">LevelName</legacyLink> properties.</para>
        </listItem>
        <listItem>
          <para>Count the children of a <legacyBold>Member</legacyBold> with the <legacyLink xlink:href="5463be22-ca50-43ea-9c92-468fc8eda280">ChildCount</legacyLink> property.</para>
        </listItem>
        <listItem>
          <para>Use the <legacyLink xlink:href="bf39dd36-fc7a-4f6e-86c0-fa71430c0d86">DrilledDown</legacyLink> property to determine whether there is at least one child on the <legacyBold>Axis</legacyBold> immediately following this <legacyBold>Member</legacyBold>.</para>
        </listItem>
        <listItem>
          <para>Use the <legacyLink xlink:href="510842e0-e8dc-4b33-9517-bd1c6df0cf3c">ParentSameAsPrev</legacyLink> property to determine whether the parent of this <legacyBold>Member</legacyBold> is the same as the parent of the immediately preceding <legacyBold>Member</legacyBold>.</para>
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
              <para>ChildrenCardinality</para>
            </TD>
            <TD>
              <para>The number of children that the member has.</para>
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
              <para>A meaningful description of the member.</para>
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
              <para>LevelNumber</para>
            </TD>
            <TD>
              <para>The distance between the level and the root of the hierarchy.</para>
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
              <para>MemberCaption</para>
            </TD>
            <TD>
              <para>A label or caption associated with the member.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>MemberGUID</para>
            </TD>
            <TD>
              <para>The GUID of the member.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>MemberName</para>
            </TD>
            <TD>
              <para>The name of the member.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>MemberOrdinal</para>
            </TD>
            <TD>
              <para>The ordinal number of the member.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>MemberType</para>
            </TD>
            <TD>
              <para>The type of the member.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>MemberUniqueName</para>
            </TD>
            <TD>
              <para>The unambiguous name of the member.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>ParentCount</para>
            </TD>
            <TD>
              <para>The count of the number of parents that this member has.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>ParentLevel</para>
            </TD>
            <TD>
              <para>The level number of the member's parent.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>ParentUniqueName</para>
            </TD>
            <TD>
              <para>The unambiguous name of the member's parent.</para>
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
            <legacyLink xlink:href="dadd6e7e-b5b4-4ede-8747-ae67ec917d90">Properties, Methods, and Events</legacyLink>           </para>
        </listItem>
      </list>
    </content>
  </languageReferenceRemarks>
  <relatedTopics>
<link xlink:href="3aae1107-2f81-413c-8eda-ef96c3df1b8a">Visual Basic Example</link>
<link xlink:href="3a647cde-efdc-4394-b1b9-8cbb1b9d689f">Members Collection</link>
<link xlink:href="1d539aa8-ce0d-4418-ab03-8d0a3c1e9d82">Properties Collection</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>