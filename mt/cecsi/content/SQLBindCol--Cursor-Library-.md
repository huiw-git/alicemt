---
title: SQLBindCol (Cursor Library)
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f4dd546a-0a6c-4397-8ee7-fafa6b9da543
manager:jhubbard
translation.priority.ht: 
  - en-gb
---
# SQLBindCol (Cursor Library)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <alert class="important">
      <para>This feature will be removed in a future version of Windows. Avoid using this feature in new development work and plan to modify applications that currently use this feature. Microsoft recommends using the driver's cursor functionality.</para>
    </alert>
    <para>This topic discusses the use of the <legacyBold>SQLBindCol </legacyBold>function in the cursor library. For general information about <legacyBold>SQLBindCol</legacyBold>, see <legacyLink xlink:href="41a37655-84cd-423f-9daa-e0b47b88dc54">SQLBindCol Function</legacyLink>.</para>
  </introduction>
  <section>
    <content>
      <para>An application allocates one or more buffers for the cursor library to return the current rowset in. It calls <legacyBold>SQLBindCol</legacyBold> one or more times to bind these buffers to the result set.</para>
      <para>An application can call <legacyBold>SQLBindCol</legacyBold> to rebind result set columns after it has called <legacyBold>SQLExtendedFetch</legacyBold>, <legacyBold>SQLFetch</legacyBold>, or <legacyBold>SQLFetchScroll</legacyBold>,as long as the C data type, column size, and decimal digits of the bound column remain the same. The application need not close the cursor to rebind columns to different addresses.</para>
      <para>The cursor library supports setting the SQL_ATTR_ROW_BIND_OFFSET_PTR statement attribute to use bind offsets. (<legacyBold>SQLBindCol</legacyBold> does not have to be called for this rebinding to occur.) If the cursor library is used with an ODBC 3<legacyItalic>.x</legacyItalic> driver, the bind offset is not used when <legacyBold>SQLFetch</legacyBold> is called. The bind offset is used if <legacyBold>SQLFetch</legacyBold> is called when the cursor library is used with an ODBC 2.<legacyItalic>x</legacyItalic> driver because <legacyBold>SQLFetch</legacyBold> is then mapped to <legacyBold>SQLExtendedFetch</legacyBold>.</para>
      <para>The cursor library supports calling <legacyBold>SQLBindCol</legacyBold> to bind the bookmark column.</para>
      <para>When working with an ODBC 2.<legacyItalic>x</legacyItalic> driver, the cursor library returns SQLSTATE HY090 (Invalid string or buffer length) when <legacyBold>SQLBindCol</legacyBold> is called to set the buffer length for a bookmark column to a value not equal to 4. When working with an ODBC 3<legacyItalic>.x</legacyItalic> driver, the cursor library allows the buffer to be any size.</para>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>