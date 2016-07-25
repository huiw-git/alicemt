---
title: "Retrieving Results (Basic)"
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 052870e3-3f3f-4f07-91da-b649348225f4
caps.latest.revision: 4
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Retrieving Results (Basic)
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>A <legacyItalic>result set</legacyItalic> is a set of rows on the data source that matches certain criteria. It is a conceptual table that results from a query and that is available to an application in tabular form. <legacyBold>SELECT</legacyBold> statements, catalog functions, and some procedures create result sets. In the following example, the first SQL statement creates a result set containing all the rows and all the columns in the Orders table, and the second SQL statement creates a result set containing OrderID, SalesPerson, and Status columns for the rows in the Orders table in which the Status is OPEN:</para>
    <code>SELECT * FROM Orders
SELECT OrderID, SalesPerson, Status FROM Orders WHERE Status = 'OPEN'</code>
    <para>A result set can be empty, which is different from no result set at all. For example, the following SQL statement creates an empty result set:</para>
    <code>SELECT * FROM Orders WHERE 1 = 2</code>
    <para>An empty result set is no different from any other result set except that it has no rows. For example, the application can retrieve metadata for the result set, can attempt to fetch rows, and must close the cursor over the result set.</para>
    <para>The process of retrieving rows from the data source and returning them to the application is called <legacyItalic>fetching</legacyItalic>. This section explains the basic parts of that process. For information about more advanced topics, such as block and scrollable cursors, see <legacyLink xlink:href="1a92b5d8-7c6e-4ce5-8c99-600a387026aa">Block Cursors</legacyLink> and <legacyLink xlink:href="2c8a5f50-9b37-452f-8160-05f42bc4d97e">Scrollable Cursors</legacyLink>. For information about updating, deleting, and inserting rows, see <legacyLink xlink:href="062036a4-cda6-4aaa-9765-f1ec3e0b31b1">Updating Data Overview</legacyLink>.</para>
    <para>This section contains the following topics.  </para>
    <list class="bullet">
      <listItem>
        <para>             <legacyLink xlink:href="4a83b8cb-2d57-4e64-b497-80bd587ee1f9">Was a Result Set Created?</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="6d134515-e34d-4563-96d7-8ad7714818fd">Result Set Metadata</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="c4407694-c8e1-4b0b-a39d-b007e6c3b54d">Binding Columns</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="04a1efc1-0a46-42f9-8c4e-9f063740dd8a">Fetching Data</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="4f19bf5e-6d8c-40ae-a975-cfd62a0790ec">Closing the Cursor</legacyLink>           </para>
      </listItem>
    </list>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>