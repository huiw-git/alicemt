---
title: Retrieving Results (Advanced)
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: bc00c379-71a7-407a-975c-898243f39bb6
manager:jhubbard
translation.priority.ht: 
  - en-gb
---
# Retrieving Results (Advanced)
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>An application can specify that an offset is added to bound data buffer addresses and the corresponding length/indicator buffer addresses when <legacyBold>SQLBulkOperations</legacyBold>, <legacyBold>SQLFetch</legacyBold>, <legacyBold>SQLFetchScroll</legacyBold>, or <legacyBold>SQLSetPos</legacyBold> is called. The results of these additions determine the addresses used in these operations.</para>
    <para>Bind offsets allow an application to change bindings without calling <legacyBold>SQLBindCol</legacyBold> for previously bound columns. A call to <legacyBold>SQLBindCol</legacyBold> to rebind data changes the buffer address and the length/indicator pointer. Rebinding with an offset, on the other hand, simply adds an offset to the existing bound data buffer address and length/indicator buffer address. When offsets are used, the bindings are a "template" of how the application buffers are laid out and the application can move this "template" to different areas of memory by changing the offset. A new offset can be specified at any time and is always added to the originally bound values.</para>
    <para>To specify a bind offset, the application sets the SQL_ATTR_ROW_BIND_OFFSET_PTR statement attribute to the address of an SQLINTEGER buffer. Before the application calls a function that uses the bindings, such as <legacyBold>SQLBulkOperations</legacyBold>, <legacyBold>SQLFetch</legacyBold>, <legacyBold>SQLFetchScroll</legacyBold>, or <legacyBold>SQLSetPos</legacyBold>, it places an offset in bytes in this buffer, as long as neither the data buffer address nor the length/indicator buffer address is 0, and as long as the bound column is in the result set. The sum of the address and the offset must be a valid address. (This means that either or both the offset and the address to which the offset is added can be invalid, as long as their sum is a valid address.) The SQL_ATTR_ROW_BIND_OFFSET_PTR statement attribute is a pointer so that the offset value can be applied to more than one set of binding data, all of which can be changed by changing one offset value. An application must make sure that the pointer remains valid until the cursor is closed.</para>
    <alert class="note">
      <para>Binding offsets are not supported by ODBC 2.<legacyItalic>x</legacyItalic> drivers.</para>
    </alert>
    <para>This section contains the following topics.  </para>
    <list class="bullet">
      <listItem>
        <para>             <legacyLink xlink:href="1a92b5d8-7c6e-4ce5-8c99-600a387026aa">Block Cursors</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="2c8a5f50-9b37-452f-8160-05f42bc4d97e">Scrollable Cursors</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="32fb7df0-953a-4f68-b041-7d2852e45d0f">The ODBC Cursor Library</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="a3c32e4b-8fe7-4a33-ae39-ae664001f315">Multiple Results</legacyLink>           </para>
      </listItem>
    </list>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>