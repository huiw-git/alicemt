---
title: "Updating Data Overview"
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 062036a4-cda6-4aaa-9765-f1ec3e0b31b1
caps.latest.revision: 4
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Updating Data Overview
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Applications can update data either by executing SQL statements or by calling <legacyBold>SQLSetPos</legacyBold> or <legacyBold>SQLBulkOperations</legacyBold>. <legacyBold>UPDATE</legacyBold>, <legacyBold>DELETE</legacyBold>, and <legacyBold>INSERT</legacyBold> statements act directly on the data source and are usually supported by drivers. Searched update and delete statements contain a specification of the rows to change. Positioned update and delete statements and <legacyBold>SQLSetPos</legacyBold> act on the data source through a cursor and are less widely supported.</para>
    <para>Whether cursors can detect changes made to the result set with the methods described in this section depends on the type of the cursor and how it is implemented. Forward-only cursors do not revisit rows and therefore will not detect any changes. For information about whether scrollable cursors can detect changes, see <legacyLink xlink:href="2c8a5f50-9b37-452f-8160-05f42bc4d97e">Scrollable Cursors</legacyLink>.</para>
    <para>This section contains the following topics.  </para>
    <list class="bullet">
      <listItem>
        <para>             <legacyLink xlink:href="5004ea72-4c49-4064-9752-f7032ba7f133">UPDATE, DELETE, and INSERT Statements</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="0eafba50-02c7-46ca-a439-ef3307b935dc">Positioned Update and Delete Statements</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="b24ed59f-f25b-4646-a135-5f3596abc1a4">Simulating Positioned Update and Delete Statements</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="1e56297d-a786-415e-b66d-b42d1b2a8d45">Determining the Number of Affected Rows</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="e9625b59-06a0-4883-b155-b932ba7528d9">Updating Data with SQLSetPos</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="7645a704-341e-4267-adbe-061a9fda225b">Updating Data with SQLBulkOperations</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="e2fdf842-5e4c-46ca-bb21-4625c3324f28">Long Data and SQLSetPos and SQLBulkOperations</legacyLink>           </para>
      </listItem>
    </list>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>