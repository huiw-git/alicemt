---
title: "Overview of Multidimensional Schemas and Data"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ce37fa06-c581-4d80-9a9b-c3aa66408909
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
# Overview of Multidimensional Schemas and Data
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction />
  <section>
    <title>Understanding Multidimensional Schemas</title>
    <content>
      <para>The central metadata object in ADO MD is the <legacyItalic>cube</legacyItalic>, which consists of a structured set of related dimensions, hierarchies, levels, and members.</para>
      <para>A <legacyItalic>dimension</legacyItalic> is an independent category of data from your multidimensional database, derived from your business entities. A dimension typically contains items to be used as query criteria for the measures of the database.</para>
      <para>A <legacyItalic>hierarchy</legacyItalic> is a path of aggregation of a dimension. A dimension may have multiple levels of granularity, which have parent-child relationships. A hierarchy defines how these levels are related.</para>
      <para>A <legacyItalic>level</legacyItalic> is a step of aggregation in a hierarchy. For dimensions with multiple layers of information, each layer is a level.</para>
      <para>A <legacyItalic>member</legacyItalic> is a data item in a dimension. Typically, you create a caption or describe a measure of the database using members.</para>
      <para>Cubes are represented by <legacyLink xlink:href="feb2581c-fc41-471c-bb69-29f8a55fda70">CubeDef</legacyLink> objects in ADO MD. Dimensions, hierarchies, levels, and members are also represented by their corresponding ADO MD objects: <legacyLink xlink:href="66adbbd2-23a3-4c19-a91b-84c31309aa1b">Dimension</legacyLink>, <legacyLink xlink:href="034af340-ac79-494e-ba5e-2b57da1cb9de">Hierarchy</legacyLink>, <legacyLink xlink:href="37815869-ed30-45fd-9aea-0a986c1b305c">Level</legacyLink>, and <legacyLink xlink:href="3dedf755-0741-4c3f-8b4e-bff8ff8809c8">Member</legacyLink>.</para>
    </content>
    <sections>
      <section>
        <title>Dimensions</title>
        <content>
          <para>The dimensions of a cube depend on your business entities and types of data to be modeled in the database. Typically, each dimension is an independent entry point or mechanism for selecting data.</para>
          <para>For example, a cube containing sales data has the following five dimensions: Salesperson, Geography, Time, Products, and Measures. The Measures dimension contains actual sales data values, while the other dimensions represent ways to categorize and group the sales data values.</para>
          <para>The Geography dimension has the following set of members:</para>
          <code>{All, North America, Europe, Canada, USA, UK, Germany, Canada-West,
Canada-East, USA-NW, USA-SW, USA-NE, USA-SE, England, Scotland, 
Wales,Ireland, Germany-North, Germany-South, Ottawa, Toronto, 
Vancouver, Calgary, Seattle, Boise, Los Angeles, Houston, 
Shreveport, Miami, Boston, New York, London, Dover, Glasgow, 
Edinburgh, Cardiff, Pembroke, Belfast, Derry, Berlin, 
Hamburg, Munich, Stuttgart}</code>
        </content>
      </section>
      <section>
        <title>Hierarchies</title>
        <content>
          <para>Hierarchies define the ways in which the levels of a dimension can be "rolled up" or grouped. A dimension can have more than one hierarchy. A natural hierarchy exists in the Geography dimension:</para>
        </content>
      </section>
      <section>
        <title>Levels</title>
        <content>
          <para>In the example Geography dimension pictured in the previous figure, each box represents a level in the hierarchy.</para>
          <para>Each level has a set of members, as follows:  </para>
          <list class="bullet">
            <listItem>
              <para>The World<codeInline> = {All}</codeInline></para>
            </listItem>
            <listItem>
              <para>Continents<codeInline> = {North America, Europe}</codeInline></para>
            </listItem>
            <listItem>
              <para>Countries<codeInline> = {Canada, USA, UK, Germany}</codeInline></para>
            </listItem>
            <listItem>
              <para>Regions<codeInline> = {Canada-East, Canada-West, USA-NE, USA-NW, USA-SE, USA-SW, England, Ireland, Scotland, Wales, Germany-North, Germany-South}</codeInline></para>
            </listItem>
            <listItem>
              <para>Cities<codeInline> = {Ottawa, Toronto, Vancouver, Calgary, Seattle, Boise, Los Angeles, Houston, Shreveport, Miami, Boston, New York, London, Dover, Glasgow, Edinburgh, Cardiff, Pembroke, Belfast, Derry, Berlin, Hamburg, Munich, Stuttgart}</codeInline></para>
            </listItem>
          </list>
        </content>
      </section>
      <section>
        <title>Members</title>
        <content>
          <para>Members at the leaf level of a hierarchy have no children, and members at the root level have no parent. All other members have at least one parent and at least one child. For example, a partial traversal of the hierarchy tree in the Geography dimension yields the following parent-child relationships:  </para>
          <list class="bullet">
            <listItem>
              <para>                 <codeInline>{All} (parent of) {Europe, North America}</codeInline>               </para>
            </listItem>
            <listItem>
              <para>                 <codeInline>{North America} (parent of) {Canada, USA}</codeInline>               </para>
            </listItem>
            <listItem>
              <para>                 <codeInline>{USA} (parent of) {USA-NE, USA-NW, USA-SE, USA-SW}</codeInline>               </para>
            </listItem>
            <listItem>
              <para>                 <codeInline>{USA-NW} (parent of) {Boise, Seattle}</codeInline>               </para>
            </listItem>
          </list>
          <para>Members can be consolidated along one or more hierarchies per dimension. Consider a Time dimension where there are two ways to roll up to the Year level from the Days level:</para>
          <para>This example also illustrates another characteristic: Some members of the Week level of the Year-Week hierarchy do not appear in any level of the Year-Quarter hierarchy. Thus, a hierarchy need not include all members of a dimension.</para>
        </content>
      </section>
    </sections>
  </section>
  <relatedTopics>
<link xlink:href="6242b374-091b-406f-827a-c0dcd3e1967a">ADO MD Object Model</link>
<link xlink:href="75b774a5-fa94-490a-b521-b2b8f7d48919">Microsoft ADO MD Programmer's Reference</link>
<link xlink:href="c826b9b5-0d78-43a2-8174-5844db62a93c">Programming with ADO MD</link>
<link xlink:href="cfae435e-2ac3-4312-8c1e-9ca4a74cd875">Using ADO with ADO MD</link>
<link xlink:href="84387746-aa3e-44fd-ad6c-a8214a6966dc">Working with Multidimensional Data</link>
</relatedTopics>
</developerConceptualDocument>