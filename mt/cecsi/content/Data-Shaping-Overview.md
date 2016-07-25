---
title: "Data Shaping Overview"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4cb5fd29-4e56-46ac-ae48-a6771c321c0c
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
# Data Shaping Overview
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>       <legacyItalic>Data shaping</legacyItalic> means building hierarchical relationships between two or more logical entities in a query. The hierarchy can be seen in parent-child relationships between a record of one <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink>, and one or more records (also known as a chapter) of another <legacyBold>Recordset</legacyBold>. In a parent-child relationship, the parent <legacyBold>Recordset</legacyBold> contains the child <legacyBold>Recordset</legacyBold>. An example of such a hierarchical relationship is customers and orders. For every customer in a database, there can be zero or more orders. The hierarchical relationship can be recursive, meaning that grandchild records can be nested in a child record. In principle, a hierarchical record can be nested to any depth. In practice, ADO limits the recursion to a maximum of 512 <legacyBold>Recordset</legacyBold>s.</para>
    <para>In general, columns of a shaped <legacyBold>Recordset</legacyBold> can contain data from a data provider such as Microsoft® SQL Server, references to another <legacyBold>Recordset</legacyBold>, values derived from a calculation on a single row of a <legacyBold>Recordset</legacyBold>, or values derived from an operation over a column of an entire <legacyBold>Recordset</legacyBold>. A column can also be newly fabricated and empty.</para>
    <para>When you retrieve the value of a column that contains a reference to another <legacyBold>Recordset</legacyBold>, ADO automatically returns the actual <legacyBold>Recordset</legacyBold> represented by the reference. The reference to a <legacyBold>Recordset</legacyBold> is actually a reference to a subset of the child, called a <legacyItalic>chapter</legacyItalic>. A single parent can reference more than one child <legacyBold>Recordset</legacyBold>.</para>
    <para>ADO support for data shaping enables you to query a data source and return a <legacyBold>Recordset</legacyBold> in which a (parent) record represents a (child) <legacyBold>Recordset</legacyBold>. In the customer-order scenario, you can use data shaping to retrieve customers' information as well as the orders placed by each customer in a single query. The resultant <legacyBold>Recordset</legacyBold> is also known as shaped <legacyBold>Recordset</legacyBold>.</para>
    <para>In addition, data shaping in ADO allows you to create new <legacyBold>Recordset</legacyBold> objects without an underlying data source by using the <legacyBold>NEW</legacyBold> keyword to describe the fields of the parent and child <legacyBold>Recordsets</legacyBold>. The new <legacyBold>Recordset</legacyBold> object can then be populated with data and persistently stored. Developers can also perform various calculations or aggregations (for example, <legacyBold>SUM</legacyBold>, <legacyBold>AVG</legacyBold>, and <legacyBold>MAX</legacyBold>) on child fields. Data shaping can also create a parent <legacyBold>Recordset</legacyBold> from a child <legacyBold>Recordset</legacyBold> by grouping records in the child and placing one row in the parent for each group in the child.</para>
    <para>Regular SQL allows you to retrieve data using <legacyBold>JOIN</legacyBold> syntax, but this can be inefficient and unwieldy because redundant parent data is repeated in each record returned for a given parent-child relationship. Data shaping can relate a single parent record in the parent <legacyBold>Recordset</legacyBold> to multiple child records in the child <legacyBold>Recordset</legacyBold>, avoiding the redundancy of a <legacyBold>JOIN</legacyBold>. Most people find the parent-child multiple <legacyBold>Recordset</legacyBold> programming model more natural and easier to work with than the single <legacyBold>Recordset</legacyBold> <legacyBold>JOIN</legacyBold> model.</para>
  </introduction>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>