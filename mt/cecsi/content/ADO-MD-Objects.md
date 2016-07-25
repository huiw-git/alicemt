---
title: "ADO MD Objects"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2a32e873-3282-4520-a7ed-89493f1da80e
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
# ADO MD Objects
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
      <tbody>
        <tr>
          <TD>
            <para>
              <legacyLink xlink:href="5f498c9a-b1e7-4e6e-9ae6-71eadaf9aada">Axis</legacyLink>             </para>
          </TD>
          <TD>
            <para>Represents a positional or filter axis of a cellset, containing selected members of one or more dimensions.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyLink xlink:href="11f6f896-d69c-44a4-94cd-d54c93140e4a">Catalog</legacyLink>             </para>
          </TD>
          <TD>
            <para>Contains multidimensional schema information (that is, cubes and underlying dimensions, hierarchies, levels, and members) specific to a multidimensional data provider (MDP).</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyLink xlink:href="dcc2f044-b785-4a29-9bc5-b673f66eedf9">Cell</legacyLink>             </para>
          </TD>
          <TD>
            <para>Represents the data at the intersection of axis coordinates, contained in a cellset.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyLink xlink:href="5e2452c0-cac0-49b2-8099-836c35794d50">Cellset</legacyLink>             </para>
          </TD>
          <TD>
            <para>Represents the results of a multidimensional query. It is a collection of cells selected from cubes or other cellsets.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyLink xlink:href="feb2581c-fc41-471c-bb69-29f8a55fda70">CubeDef</legacyLink>             </para>
          </TD>
          <TD>
            <para>Represents a cube from a multidimensional schema, containing a set of related dimensions.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyLink xlink:href="66adbbd2-23a3-4c19-a91b-84c31309aa1b">Dimension</legacyLink>             </para>
          </TD>
          <TD>
            <para>Represents one of the dimensions of a multidimensional cube, containing one or more hierarchies of members.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyLink xlink:href="034af340-ac79-494e-ba5e-2b57da1cb9de">Hierarchy</legacyLink>             </para>
          </TD>
          <TD>
            <para>Represents one way in which the members of a dimension can be aggregated or "rolled up." A dimension can be aggregated along one or more hierarchies.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyLink xlink:href="37815869-ed30-45fd-9aea-0a986c1b305c">Level</legacyLink>             </para>
          </TD>
          <TD>
            <para>Contains a set of members, each of which has the same rank within a hierarchy.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyLink xlink:href="3dedf755-0741-4c3f-8b4e-bff8ff8809c8">Member</legacyLink>             </para>
          </TD>
          <TD>
            <para>Represents a member of a level in a cube, the children of a member of a level, or a member of a position along an axis of a cellset.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyLink xlink:href="91eab784-3ce9-41d6-a840-9b0939ca0608">Position</legacyLink>             </para>
          </TD>
          <TD>
            <para>Represents a set of one or more members of different dimensions that defines a point along an axis.</para>
          </TD>
        </tr>
      </tbody>
    </table>
    <para>Also, the <legacyBold>Catalog</legacyBold> object is connected to an ADO <legacyBold>Connection</legacyBold> object, which is included with the standard ADO library:</para>
    <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
      <thead>
        <tr>
          <TD>
            <para>Object</para>
          </TD>
          <TD>
            <para>Description</para>
          </TD>
        </tr>
      </thead>
      <tbody>
        <tr>
          <TD>
            <para>
              <legacyLink xlink:href="ef6b1824-5b12-43db-89d7-8f3d13896d4d">Connection</legacyLink>             </para>
          </TD>
          <TD>
            <para>Represents an open connection to a data source.</para>
          </TD>
        </tr>
      </tbody>
    </table>
    <para>The relationships between these objects are illustrated in the <legacyLink xlink:href="6242b374-091b-406f-827a-c0dcd3e1967a">ADO MD Object Model</legacyLink>.</para>
    <para>Many ADO MD objects can be contained in a corresponding collection. For example, a <legacyLink xlink:href="feb2581c-fc41-471c-bb69-29f8a55fda70">CubeDef</legacyLink> object can be contained in a <legacyLink xlink:href="c79a5e36-71fd-44c4-948d-d6a7a89bb3b5">CubeDefs</legacyLink> collection of a <legacyBold>Catalog</legacyBold>. For more information, see <legacyLink xlink:href="01c53429-ccc9-4077-b738-d3c1f43bd76c">ADO MD Collections</legacyLink>.</para>
  </introduction>
  <relatedTopics>
<link xlink:href="ad709f69-113b-4972-9384-c1215641844d">ADO MD API Reference</link>
<link xlink:href="72cf9eb3-31f6-441c-aede-5383fdfb81af">ADO MD Code Examples</link>
<link xlink:href="01c53429-ccc9-4077-b738-d3c1f43bd76c">ADO MD Collections</link>
<link xlink:href="d9e66999-96f3-48ec-93b2-d9442da56d9b">ADO MD Enumerated Constants</link>
<link xlink:href="78bfa2f0-358b-40bb-be2e-16262752d676">ADO MD Methods</link>
<link xlink:href="6242b374-091b-406f-827a-c0dcd3e1967a">ADO MD Object Model</link>
<link xlink:href="11ca7e42-ab6a-47da-ab32-55abab663069">ADO MD Properties</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>