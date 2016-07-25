---
title: "What is a Cursor?"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 596eb4b6-c22f-4cde-b23f-172dd66c3161
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
# What is a Cursor?
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Operations in a relational database act on a complete set of rows. The set of rows returned by a SELECT statement consists of all the rows that satisfy the conditions in the WHERE clause of the statement. This complete set of rows returned by the statement is known as the result set. Applications, especially those that are interactive and online, cannot always work effectively with the entire result set as a unit. These applications need a mechanism to work with one row or a small block of rows at a time. Cursors are an extension to result sets that provide that mechanism.</para>
    <para>A cursor is implemented by a cursor library. A cursor library is software, often implemented as a part of a database system or a data access API, that is used to manage attributes of data returned from a data source (a result set). These attributes include concurrency management, position in the result set, number of rows returned, and whether you can move forward or backward (or both) through the result set (scrollability).</para>
    <para>A cursor keeps track of the position in the result set, and allows you to perform multiple operations row by row against a result set, with or without returning to the original table. In other words, cursors conceptually return a result set based on tables within the databases. The cursor is so named because it indicates the current position in the result set, just as the cursor on a computer screen indicates current position.</para>
    <para>It is important to become familiar with the concept of cursors before moving on to learn the specifics of their usage in ADO.</para>
    <para>Using cursors, you can:  </para>
    <list class="bullet">
      <listItem>
        <para>Specify positioning at specific rows in the result set.</para>
      </listItem>
      <listItem>
        <para>Retrieve one row or a block of rows based on the current result set position.</para>
      </listItem>
      <listItem>
        <para>Modify data in the rows at the current position in the result set.</para>
      </listItem>
      <listItem>
        <para>Define different levels of sensitivity to data changes made by other users.</para>
      </listItem>
    </list>
    <para>For example, consider an application that displays a list of available products to a potential buyer. The buyer scrolls through the list to see product details and cost, and finally selects a product for purchase. Additional scrolling and selection occurs for the remainder of the list. As far as the buyer is concerned, the products appear one at a time, but the application uses a scrollable cursor to browse up and down through the result set.</para>
    <para>You can use cursors in a variety of ways:  </para>
    <list class="bullet">
      <listItem>
        <para>With no rows at all.</para>
      </listItem>
      <listItem>
        <para>With some or all of the rows in a single table.</para>
      </listItem>
      <listItem>
        <para>With some or all of the rows from logically joined tables.</para>
      </listItem>
      <listItem>
        <para>As read-only or updateable at the cursor or field level.</para>
      </listItem>
      <listItem>
        <para>As forward-only or fully scrollable.</para>
      </listItem>
      <listItem>
        <para>With the cursor keyset located on the server.</para>
      </listItem>
      <listItem>
        <para>Sensitive to underlying table changes caused by other applications (such as membership, sort, inserts, updates, and deletes).</para>
      </listItem>
      <listItem>
        <para>Existing on either the server or the client.</para>
      </listItem>
    </list>
    <para>Read-only cursors help users browse through the result set, and read/write cursors can implement individual row updates. Complex cursors can be defined with keysets that point back to base table rows. Although some cursors are read-only in a forward direction, others can move back and forth and provide a dynamic refresh of the result set based on changes that other applications are making to the database.</para>
    <para>Not all applications need to use cursors to access or update data. Some queries simply do not require direct row updating by using a cursor. Cursors should be one of the last techniques you choose to retrieve data—and then you should choose the lowest impact cursor possible. When you create a result set by using a stored procedure, the result set is not updateable using cursor edit or update methods.</para>
  </introduction>
  <section>
    <title>Concurrency</title>
    <content>
      <para>In some multiuser applications it is very important for the data presented to the end user to be as current as possible. A classic example of such a system is an airline reservation system, where many users might be contending for the same seat on a given flight (and therefore, a single record). In a case like this, the application design must handle concurrent operations on a single record.</para>
      <para>In other applications, concurrency is not as important. In such cases, the expense involved in keeping the data current at all times cannot be justified.</para>
    </content>
  </section>
  <section>
    <title>Position</title>
    <content>
      <para>A cursor also keeps track of the current position in a result set. Think of the cursor position as a pointer to the current record, similar to the way an array index points to the value at that particular location in the array.</para>
    </content>
  </section>
  <section>
    <title>Scrollability</title>
    <content>
      <para>The type of cursor employed by your application also affects the ability to move forward and backward through the rows in a result set; this is sometimes referred to as scrollability. The ability to move forward <legacyItalic>and</legacyItalic> backward through a result set adds to the complexity of the cursor, and is therefore more expensive to implement. For this reason, you should ask for a cursor with this functionality only when necessary.</para>
    </content>
  </section>
  <relatedTopics />
</developerConceptualDocument>