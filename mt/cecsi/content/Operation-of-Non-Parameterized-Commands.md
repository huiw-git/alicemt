---
title: "Operation of Non-Parameterized Commands"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9700e50a-9f17-4ba3-8afb-f750741dc6ca
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
# Operation of Non-Parameterized Commands
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>For non-parameterized commands, all the provider commands are executed and the <legacyBold>Recordsets</legacyBold> are created during command execution. If the command is executed synchronously, all the <legacyBold>Recordsets</legacyBold> will be fully populated. If an asynchronous population mode was selected, the populated state of the <legacyBold>Recordsets</legacyBold> will depend on the population mode and the size of the <legacyBold>Recordsets</legacyBold>.</para>
    <para>For example, the <legacyItalic>parent-command</legacyItalic> could return a <legacyBold>Recordset</legacyBold> of customers for a company from a Customers table, and the <legacyItalic>child-command</legacyItalic> could return a <legacyBold>Recordset</legacyBold> of orders for all customers from an Orders table.</para>
    <code>SHAPE {SELECT * FROM Customers} 
   APPEND ({SELECT * FROM Orders} AS chapOrders 
   RELATE customerID TO customerID)</code>
    <para>For non-parameterized parent-child relationships, each parent and child <legacyBold>Recordset</legacyBold> object must have a column in common to associate them. The columns are named in the RELATE clause, <legacyItalic>parent-column</legacyItalic> first and then <legacyItalic>child-column</legacyItalic>. The columns may have different names in their respective <legacyBold>Recordset</legacyBold> objects but must refer to the same information in order to specify a meaningful relation. For example, the <legacyBold>Customers</legacyBold> and <legacyBold>Orders</legacyBold> <legacyBold>Recordset</legacyBold> objects could both have a customerID field. Because the membership of the child <legacyBold>Recordset</legacyBold> is determined by the provider command, the child <legacyBold>Recordset</legacyBold> can contain orphaned rows. These orphaned rows are inaccessible without additional reshaping.</para>
    <para>Data shaping appends a chapter column to the parent <legacyBold>Recordset</legacyBold>. The values in the chapter column are references to rows in the child <legacyBold>Recordset</legacyBold>, which satisfy the RELATE clause. That is, the same value is in the <legacyItalic>parent-column</legacyItalic> of a given parent row as is in the <legacyItalic>child-column </legacyItalic>of all the rows of the chapter child. When multiple TO clauses are used in the same RELATE clause, they are implicitly combined using an AND operator. If the parent columns in the RELATE clause do not constitute a key to the parent <legacyBold>Recordset</legacyBold>, a single child row can have multiple parent rows.</para>
    <para>When you access the reference in the chapter column, ADO automatically retrieves the <legacyBold>Recordset</legacyBold> represented by the reference. Note that in a non-parameterized command, although the entire child <legacyBold>Recordset</legacyBold> has been retrieved, the chapter only presents a subset of rows.</para>
    <para>If the appended column has no <legacyItalic>chapter-alias</legacyItalic>, a name will be generated for it automatically. A <legacyLink xlink:href="b10a72fc-3c4b-4186-a70b-993dc9f7a092">Field</legacyLink> object for the column will be appended to the <legacyBold>Recordset</legacyBold> object's <legacyLink xlink:href="7c371474-b88f-4730-afa5-44163a0488d5">Fields</legacyLink> collection, and its data type will be <legacyBold>adChapter</legacyBold>.</para>
    <para>For information about navigating a hierarchical <legacyBold>Recordset</legacyBold>, see <legacyLink xlink:href="25f1d2a1-6d5e-4457-aa07-5db5c75dee18">Accessing Rows in a Hierarchical Recordset</legacyLink>.</para>
  </introduction>
  <relatedTopics>
<link xlink:href="1bfdcad4-52e1-45bc-ad21-783657ef0a44">Data Shaping</link>
<link xlink:href="ea691475-0f03-4abe-a785-b77e77712d1d">Formal Shape Grammar</link>
<link xlink:href="1fac7831-a187-4b15-9b43-aad380c5556c">Shape Commands in General</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>