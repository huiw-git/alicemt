---
title: SQLSetDescField and SQLSetDescRec (Cursor Library)
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4ccff067-85cd-4bfa-a6cd-7f28051fb5b9
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# SQLSetDescField and SQLSetDescRec (Cursor Library)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <alert class="important">
      <para>This feature will be removed in a future version of Windows. Avoid using this feature in new development work and plan to modify applications that currently use this feature. Microsoft recommends using the driver's cursor functionality.</para>
    </alert>
    <para>This topic discusses the use of the <legacyBold>SQLSetDescField</legacyBold> and <legacyBold>SQLSetDescRec</legacyBold> functions in the cursor library. For general information about these functions, see <legacyLink xlink:href="8c544388-fe9d-4f94-a0ac-fa0b9c9c88a5">SQLSetDescField Function</legacyLink> and <legacyLink xlink:href="bf55256c-7eb7-4e3f-97ef-b0fee09ba829">SQLSetDescRec Function</legacyLink>.</para>
    <para>The cursor library executes <legacyBold>SQLSetDescField</legacyBold> when it is called to return the value of the fields set for bookmark columns:</para>
    <para>SQL_DESC_DATA_PTR</para>
    <para>SQL_DESC_INDICATOR_PTR</para>
    <para>SQL_DESC_OCTET_LENGTH_PTR</para>
    <para>SQL_DESC_LENGTH</para>
    <para>SQL_DESC_OCTET_LENGTH</para>
    <para>SQL_DESC_DATETIME_INTERVAL_CODE</para>
    <para>SQL_DESC_SCALE</para>
    <para>SQL_DESC_PRECISION</para>
    <para>SQL_DESC_TYPE</para>
    <para>SQL_DESC_NAME</para>
    <para>SQL_DESC_UNNAMED</para>
    <para>SQL_DESC_NULLABLE</para>
    <para>The cursor library executes calls to <legacyBold>SQLSetDescRec</legacyBold> for a bookmark column.</para>
    <para>When working with an ODBC 2.<legacyItalic>x</legacyItalic> driver, the cursor library returns SQLSTATE HY090 (Invalid string or buffer length) when <legacyBold>SQLSetDescField</legacyBold> or <legacyBold>SQLSetDescRec</legacyBold> is called to set the SQL_DESC_OCTET_LENGTH field for the bookmark record of an ARD to a value not equal to 4. When working with an ODBC 3<legacyItalic>.x</legacyItalic> driver, the cursor library allows the buffer to be any size.</para>
    <para>The cursor library executes <legacyBold>SQLSetDescField</legacyBold> when it is called to return the value of the SQL_DESC_BIND_OFFSET_PTR, SQL_DESC_BIND_TYPE, SQL_DESC_ROW_ARRAY_SIZE, or SQL_DESC_ROW_STATUS_PTR field. These fields can be returned for any row, not just the bookmark row.</para>
    <para>The cursor library does not execute <legacyBold>SQLSetDescField</legacyBold> to change any descriptor field other than the fields mentioned previously. If an application calls <legacyBold>SQLSetDescField</legacyBold> to set any other field while the cursor library is loaded, the call is passed through to the driver.</para>
    <para>The cursor library supports changing the SQL_DESC_DATA_PTR, SQL_DESC_INDICATOR_PTR, and SQL_DESC_OCTET_LENGTH_PTR fields of any row of an application row descriptor dynamically (after a call to <legacyBold>SQLExtendedFetch</legacyBold>, <legacyBold>SQLFetch</legacyBold>, or <legacyBold>SQLFetchScroll</legacyBold>). The SQL_DESC_OCTET_LENGTH_PTR field can be changed to a null pointer only to unbind the length buffer for a column.</para>
    <para>The cursor library does not support changing the SQL_DESC_BIND_TYPE field in an APD or ARD when a cursor is open. The SQL_DESC_BIND_TYPE field can be changed only after the cursor is closed and before a new cursor is opened. The only descriptor fields that the cursor library supports changing when a cursor is open are SQL_DESC_ARRAY_STATUS_PTR, SQL_DESC_BIND_OFFSET_PTR, SQL_DESC_DATA_PTR, SQL_DESC_INDICATOR_PTR, SQL_DESC_OCTET_LENGTH_PTR, and SQL_DESC_ROWS_PROCESSED_PTR.</para>
    <para>The cursor library does not support modifying the SQL_DESC_COUNT field of the ARD after <legacyBold>SQLExtendedFetch</legacyBold> or <legacyBold>SQLFetchScroll</legacyBold> has been called and before the cursor has been closed.</para>
  </introduction>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>