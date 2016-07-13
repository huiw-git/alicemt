---
title: SQLGetData (Cursor Library)
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ff40c9c0-b847-4426-a099-1bff47e6e872
manager:jhubbard
translation.priority.ht: 
  - en-gb
---
# SQLGetData (Cursor Library)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <alert class="important">
      <para>This feature will be removed in a future version of Windows. Avoid using this feature in new development work and plan to modify applications that currently use this feature. Microsoft recommends using the driver's cursor functionality.</para>
    </alert>
    <para>This topic discusses the use of the <legacyBold>SQLGetData</legacyBold> function in the cursor library. For general information about <legacyBold>SQLGetData</legacyBold>, see <legacyLink xlink:href="e3c1356a-5db7-4186-85fd-8b74633317e8">SQLGetData Function</legacyLink>.</para>
    <para>The cursor library implements <legacyBold>SQLGetData</legacyBold> by first constructing a <legacyBold>SELECT</legacyBold> statement with a <legacyBold>WHERE</legacyBold> clause that enumerates the values stored in its cache for each bound column in the current row. It then executes the <legacyBold>SELECT</legacyBold> statement to reselect the row and calls <legacyBold>SQLGetData</legacyBold> in the driver to retrieve the data from the data source (as opposed to the cache).</para>
    <alert class="caution">
      <para>The <legacyBold>WHERE</legacyBold> clause constructed by the cursor library to identify the current row can fail to identify any rows, identify a different row, or identify more than one row. For more information, see <legacyLink xlink:href="e429254c-c43f-4fbf-98b2-5f1ed53501ff">Constructing Searched Statements</legacyLink>.</para>
    </alert>
    <para>If the SQL_ATTR_USE_BOOKMARKS statement attribute is set to SQL_UB_VARIABLE, <legacyBold>SQLGetData</legacyBold> can be called on column 0 to return bookmark data.</para>
    <para>Calls to <legacyBold>SQLGetData</legacyBold> are subject to the following restrictions:  </para>
    <list class="bullet">
      <listItem>
        <para>
          <legacyBold>SQLGetData</legacyBold> cannot be called for forward-only cursors.</para>
      </listItem>
      <listItem>
        <para>
          <legacyBold>SQLGetData</legacyBold> can be called only when the following conditions are met: a <legacyBold>SELECT</legacyBold> statement generated the result set; the <legacyBold>SELECT</legacyBold> statement did not contain a join, a <legacyBold>UNION</legacyBold> clause, or a <legacyBold>GROUP BY</legacyBold> clause; and any columns that used an alias or expression in the select list were not bound with <legacyBold>SQLBindCol</legacyBold>.</para>
      </listItem>
      <listItem>
        <para>If the driver supports only one active statement, the cursor library fetches the rest of the result set before executing the <legacyBold>SELECT</legacyBold> statement and calling <legacyBold>SQLGetData</legacyBold>.</para>
      </listItem>
    </list>
  </introduction>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>