---
title: Parameter Binding Offsets
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 309339e9-9ccd-4a58-8aa4-b6dc88f4eb7c
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Parameter Binding Offsets
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>An application can specify that an offset is added to bound parameter buffer addresses and the corresponding length/indicator buffer addresses when <legacyBold>SQLExecDirect</legacyBold> or <legacyBold>SQLExecute</legacyBold> is called. The result of these additions determines the addresses used in these operations.</para>
    <para>Bind offsets allow an application to change bindings without calling <legacyBold>SQLBindParameter</legacyBold> for previously bound parameters. A call to <legacyBold>SQLBindParameter</legacyBold> to rebind a parameter changes the buffer address and the length/indicator pointer. Rebinding with an offset, on the other hand, simply adds an offset to the existing bound parameter buffer address and length/indicator buffer address. When offsets are used, the bindings are a "template" of how the application buffers are laid out and the application can move this "template" to different areas of memory by changing the offset. A new offset can be specified at any time and is always added to the originally bound values.</para>
    <para>To specify a bind offset, the application sets the SQL_ATTR_PARAM_BIND_OFFSET_PTR statement attribute to the address of an SQLINTEGER buffer. Before the application calls a function that uses the bindings, it places an offset in bytes in this buffer, as long as neither the parameter buffer address nor the length/indicator buffer address is 0, and the bound parameter is in the SQL statement. The sum of the address and the offset must be a valid address. (This means that either or both the offset and the address to which the offset is added can be invalid, as long as their sum is a valid address.)</para>
    <alert class="note">
      <para>Binding offsets are not supported by ODBC 2.<legacyItalic>x</legacyItalic> drivers.</para>
    </alert>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>