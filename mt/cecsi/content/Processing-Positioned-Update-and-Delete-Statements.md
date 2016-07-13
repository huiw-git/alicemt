---
title: Processing Positioned Update and Delete Statements
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2975dd97-48e6-4d0a-a9c7-40759a7d94c8
manager:jhubbard
translation.priority.ht: 
  - en-gb
---
# Processing Positioned Update and Delete Statements
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <alert class="important">
      <para>This feature will be removed in a future version of Windows. Avoid using this feature in new development work and plan to modify applications that currently use this feature. Microsoft recommends using the driver's cursor functionality.</para>
    </alert>
    <para>The cursor library supports positioned update and delete statements by replacing the <legacyBold>WHERE CURRENT OF</legacyBold> clause in such statements with a <legacyBold>WHERE</legacyBold> clause that enumerates the values stored in its cache for each bound column. The cursor library passes the newly constructed <legacyBold>UPDATE</legacyBold> and <legacyBold>DELETE</legacyBold> statements to the driver for execution. For positioned update statements, the cursor library then updates its cache from the values in the rowset buffers and sets the corresponding value in the row status array to SQL_ROW_UPDATED. For positioned delete statements, it sets the corresponding value in the row status array to SQL_ROW_DELETED.</para>
    <alert class="caution">
      <para>The <legacyBold>WHERE</legacyBold> clause constructed by the cursor library to identify the current row can fail to identify any rows, identify a different row, or identify more than one row. For more information, see <legacyLink xlink:href="e429254c-c43f-4fbf-98b2-5f1ed53501ff">Constructing Searched Statements</legacyLink>, later in this appendix.</para>
    </alert>
    <para>Positioned update and delete statements are subject to the following restrictions:  </para>
    <list class="bullet">
      <listItem>
        <para>Positioned update and delete statements can be used only in the following cases: when a <legacyBold>SELECT</legacyBold> statement generated the result set; when the <legacyBold>SELECT</legacyBold> statement did not contain a join, a <legacyBold>UNION</legacyBold> clause, or a <legacyBold>GROUP BY</legacyBold> clause; and when any columns that used an alias or expression in the select list were not bound with <legacyBold>SQLBindCol</legacyBold>.</para>
      </listItem>
      <listItem>
        <para>If an application prepares a positioned update or delete statement, it must do so after it has called <legacyBold>SQLFetch</legacyBold> or <legacyBold>SQLFetchScroll</legacyBold>. Although the cursor library submits the statement to the driver for preparation, it closes the statement and executes it directly when the application calls <legacyBold>SQLExecute</legacyBold>.</para>
      </listItem>
      <listItem>
        <para>If the driver supports only one active statement, the cursor library fetches the rest of the result set and then refetches the current rowset from its cache before it executes a positioned update or delete statement. If the application then calls a function that returns metadata in a result set (for example, <legacyBold>SQLNumResultCols</legacyBold> or <legacyBold>SQLDescribeCol</legacyBold>), the cursor library returns an error.</para>
      </listItem>
      <listItem>
        <para>If a positioned update or delete statement is performed on a column of a table that includes a timestamp column that is automatically updated every time an update is performed, all subsequent positioned update or delete statements will fail if the timestamp column is bound. This occurs because the searched update or delete statement that the cursor library creates will not accurately identify the row to update. The value in the searched statement for the timestamp column will not match the automatically updated value of the timestamp column.</para>
      </listItem>
    </list>
  </introduction>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>