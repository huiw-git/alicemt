---
title: Constructing Searched Statements
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e429254c-c43f-4fbf-98b2-5f1ed53501ff
translation.priority.ht: 
  - en-gb
---
# Constructing Searched Statements
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <alert class="important">
      <para>This feature will be removed in a future version of Windows. Avoid using this feature in new development work and plan to modify applications that currently use this feature. Microsoft recommends using the driver's cursor functionality.</para>
    </alert>
    <para>To support positioned update and delete statements, the cursor library constructs a searched <legacyBold>UPDATE</legacyBold> or <legacyBold>DELETE</legacyBold> statement from the positioned statement. To support calls to <legacyBold>SQLGetData</legacyBold> in a block of data, the cursor library constructs a searched <legacyBold>SELECT</legacyBold> statement to create a result set containing the current row of data. In each of these statements, the <legacyBold>WHERE</legacyBold> clause enumerates the values stored in the cache for each bound column that returns SQL_PRED_SEARCHABLE or SQL_PRED_BASIC for the SQL_DESC_SEARCHABLE field identifier in <legacyBold>SQLColAttribute</legacyBold>.</para>
  </introduction>
  <section>
    <content>
      <alert class="caution">
        <para>The <legacyBold>WHERE</legacyBold> clause constructed by the cursor library to identify the current row can fail to identify any rows, identify a different row, or identify more than one row.</para>
      </alert>
      <para>If a positioned update or delete statement affects more than one row, the cursor library updates the row status array only for the row on which the cursor is positioned and returns SQL_SUCCESS_WITH_INFO and SQLSTATE 01001 (Cursor operation conflict). If the statement does not identify any rows, the cursor library does not update the row status array and returns SQL_SUCCESS_WITH_INFO and SQLSTATE 01001 (Cursor operation conflict). An application can call <legacyBold>SQLRowCount</legacyBold> to determine the number of rows that were updated or deleted.</para>
      <para>If the <legacyBold>SELECT</legacyBold> clause used to position the cursor for a call to <legacyBold>SQLGetData</legacyBold> identifies more than one row, <legacyBold>SQLGetData</legacyBold> is not guaranteed to return the correct data. If it does not identify any rows, <legacyBold>SQLGetData</legacyBold> returns SQL_NO_DATA.</para>
      <para>If an application conforms to the following guidelines, the <legacyBold>WHERE</legacyBold> clause constructed by the cursor library should uniquely identify the current row, except when this is impossible, such as when the data source contains duplicate rows.  </para>
      <list class="bullet">
        <listItem>
          <para>
            <legacyBold>Bind columns that uniquely identify the row.</legacyBold> If the bound columns do not uniquely identify the row, the <legacyBold>WHERE</legacyBold> clause constructed by the cursor library might identify more than one row. In a positioned update or delete statement, such a clause might cause more than one row to be updated or deleted. In a call to <legacyBold>SQLGetData</legacyBold>, such a clause might cause the driver to return data for the wrong row. Binding all the columns in a unique key guarantees that each row is uniquely identified.</para>
        </listItem>
        <listItem>
          <para>
            <legacyBold>Allocate data buffers large enough that no truncation occurs.</legacyBold> The cursor library's cache is a copy of the values in the rowset buffers bound to the result set with <legacyBold>SQLBindCol</legacyBold>. If data is truncated when it is placed in these buffers, it will also be truncated in the cache. A <legacyBold>WHERE</legacyBold> clause constructed from truncated values might not correctly identify the underlying row in the data source.</para>
        </listItem>
        <listItem>
          <para>
            <legacyBold>Specify non-null length buffers for binary C data.</legacyBold> The cursor library allocates length buffers in its cache only if the <legacyItalic>StrLen_or_IndPtr</legacyItalic> argument in <legacyBold>SQLBindCol</legacyBold> is non-null. When the <legacyItalic>TargetType</legacyItalic> argument is SQL_C_BINARY, the cursor library requires the length of the binary data to construct a <legacyBold>WHERE</legacyBold> clause from the data. If there is no length buffer for a SQL_C_BINARY column and the application calls <legacyBold>SQLGetData</legacyBold> or attempts to execute a positioned update or delete statement, the cursor library returns SQL_ERROR and SQLSTATE SL014 (A positioned request was issued and not all column count fields were buffered).</para>
        </listItem>
        <listItem>
          <para>
            <legacyBold>Specify non-null length buffers for nullable columns.</legacyBold> The cursor library allocates length buffers in its cache only if the <legacyItalic>StrLen_or_IndPtr </legacyItalic>argument in <legacyBold>SQLBindCol</legacyBold> is non-null. Because SQL_NULL_DATA is stored in the length buffer, the cursor library assumes that any column for which no length buffer is specified is non-nullable. If no length column is specified for a nullable column, the cursor library constructs a <legacyBold>WHERE</legacyBold> clause that uses the data value for the column. This clause will not correctly identify the row.</para>
        </listItem>
      </list>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>