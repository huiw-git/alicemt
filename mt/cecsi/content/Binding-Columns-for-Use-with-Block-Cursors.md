---
title: Binding Columns for Use with Block Cursors
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 231beede-cdfa-4e28-8b10-2760b983250f
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Binding Columns for Use with Block Cursors
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Because block cursors return multiple rows, applications that use them must bind an array of variables to each column instead of a single variable. These arrays are collectively known as the <legacyItalic>rowset buffers</legacyItalic>. Following are the two styles of binding:  </para>
    <list class="bullet">
      <listItem>
        <para>Bind an array to each column. This is called <legacyItalic>column-wise binding</legacyItalic> because each data structure (array) contains data for a single column.</para>
      </listItem>
      <listItem>
        <para>Define a structure to hold the data for an entire row and bind an array of these structures. This is called <legacyItalic>row-wise binding</legacyItalic> because each data structure contains the data for a single row.</para>
      </listItem>
    </list>
    <para>As when the application binds single variables to columns, it calls <legacyBold>SQLBindCol</legacyBold> to bind arrays to columns. The only difference is that the addresses passed are array addresses, not single variable addresses. The application sets the SQL_BIND_BY_COLUMN statement attribute to specify whether it is using column-wise or row-wise binding. Whether to use column-wise or row-wise binding is largely a matter of application preference. Row-wise binding might correspond more closely to the application's layout of data, in which case it would provide better performance.</para>
    <para>This section contains the following topics.  </para>
    <list class="bullet">
      <listItem>
        <para>             <legacyLink xlink:href="86d37637-3a25-455d-9c82-a0d7bff8d70d">Column-Wise Binding</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="4f622cf4-0603-47a1-a48b-944c4ef46364">Row-Wise Binding</legacyLink>           </para>
      </listItem>
    </list>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>