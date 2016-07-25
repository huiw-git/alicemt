---
title: "Working with Multidimensional Data"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 84387746-aa3e-44fd-ad6c-a8214a6966dc
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
# Working with Multidimensional Data
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>A <legacyItalic>cellset</legacyItalic> is the result of a query on multidimensional data. It consists of a collection of axes, usually no more than four axes and typically only two or three. An <legacyItalic>axis</legacyItalic> is a collection of members from one or more dimensions, which is used to locate or filter specific values in a cube.</para>
    <para>A <legacyItalic>position</legacyItalic> is a point along an axis. For an axis consisting of a single dimension, these positions are a subset of the dimension members. If an axis consists of more than one dimension, then each position is a compound entity, which has <legacyItalic>n</legacyItalic> parts where <legacyItalic>n</legacyItalic> is the number of dimensions oriented along that axis. Each part of the position is a member from one constituent dimension.</para>
    <para>For example, if the Geography and Product dimensions from a cube containing sales data are oriented along the x-axis of a cellset, a position along this axis may contain the members "USA" and "Computers." In this example, determining a position along the x-axis requires that members from each dimension are oriented along the axis.</para>
    <para>A <legacyItalic>cell</legacyItalic> is an object positioned at the intersection of axis coordinates. Each cell has multiple pieces of information associated with it, including the data itself, a formatted string (the displayable form of cell data), and the cell ordinal value. (Each cell is a unique ordinal value in the cellset. The ordinal value of the first cell in the cellset is zero, while the leftmost cell in the second row of a cellset with eight columns would have an ordinal value of eight.)</para>
    <para>For example, a cube has the following six dimensions (note that this cube schema differs slightly from the example given in <legacyLink xlink:href="ce37fa06-c581-4d80-9a9b-c3aa66408909">Overview of Multidimensional Schemas and Data</legacyLink>):  </para>
    <list class="bullet">
      <listItem>
        <para>Salesperson</para>
      </listItem>
      <listItem>
        <para>Geography (natural hierarchy) — Continents, Countries, States, and so on</para>
      </listItem>
      <listItem>
        <para>Quarters — Quarters, Months, Days</para>
      </listItem>
      <listItem>
        <para>Years</para>
      </listItem>
      <listItem>
        <para>Measures — Sales, PercentChange, BudgetedSales</para>
      </listItem>
      <listItem>
        <para>Products</para>
      </listItem>
    </list>
    <para>The following cellset represents sales for 1991 for all products:</para>
    <alert class="note">
      <para>The cell values in the example can be viewed as ordered pairs of axis position ordinals where the first digit represents the x-axis position and the second digit the y-axis position.</para>
    </alert>
    <para>The characteristics of this cellset are as follows:  </para>
    <list class="bullet">
      <listItem>
        <para>Axis dimensions: Quarters, Salesperson, Geography</para>
      </listItem>
      <listItem>
        <para>Filter dimensions: Measures, Years, Products</para>
      </listItem>
      <listItem>
        <para>Two axes: COLUMN (x, or Axis 0) and ROW (y, or Axis 1)</para>
      </listItem>
      <listItem>
        <para>x-axis: two nested dimensions, Salesperson and Geography</para>
      </listItem>
      <listItem>
        <para>y-axis: Quarters dimension</para>
      </listItem>
    </list>
    <para>The x-axis has two nested dimensions: Salesperson and Geography. From Geography, four members are selected: Seattle, Boston, USA-South, and Japan. Two members are selected from Salesperson: Valentine and Nash. This yields a total of eight positions on this axis (8 = 4*2).</para>
    <para>Each coordinate is represented as a position with two members — one from the Salesperson dimension and another from the Geography dimension:</para>
    <code>(Valentine, Seattle), (Valentine, Boston), (Valentine, USA_North),
(Valentine, Japan), (Nash, Seattle), (Nash, Boston), (Nash, USA_North),
(Nash, Japan)</code>
    <para>The y-axis has only one dimension, containing the following eight positions:</para>
    <code>Jan, Feb, Mar, Qtr2, Qtr3, Oct, Nov, Dec</code>
    <para>Cellsets, cells, axes, and positions are all represented in ADO MD by corresponding objects: <legacyLink xlink:href="5e2452c0-cac0-49b2-8099-836c35794d50">Cellset</legacyLink>, <legacyLink xlink:href="dcc2f044-b785-4a29-9bc5-b673f66eedf9">Cell</legacyLink>, <legacyLink xlink:href="5f498c9a-b1e7-4e6e-9ae6-71eadaf9aada">Axis</legacyLink>, and <legacyLink xlink:href="91eab784-3ce9-41d6-a840-9b0939ca0608">Position</legacyLink>.</para>
  </introduction>
  <relatedTopics>
<link xlink:href="6242b374-091b-406f-827a-c0dcd3e1967a">ADO MD Object Model</link>
<link xlink:href="75b774a5-fa94-490a-b521-b2b8f7d48919">Microsoft ADO MD Programmer's Reference</link>
<link xlink:href="ce37fa06-c581-4d80-9a9b-c3aa66408909">Overview of Multidimensional Schemas and Data</link>
<link xlink:href="c826b9b5-0d78-43a2-8174-5844db62a93c">Programming with ADO MD</link>
<link xlink:href="cfae435e-2ac3-4312-8c1e-9ca4a74cd875">Using ADO with ADO MD</link>
</relatedTopics>
</developerConceptualDocument>