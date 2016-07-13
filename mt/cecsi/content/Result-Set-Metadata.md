---
title: Result Set Metadata
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6d134515-e34d-4563-96d7-8ad7714818fd
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Result Set Metadata
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>       <legacyItalic>Metadata</legacyItalic> is data that describes other data. For example, result set metadata describes the result set, such as the number of columns in the result set, the data types of those columns, their names, precision, nullability, and so on.</para>
    <para>Interoperable applications should always check the metadata of result set columns. The metadata for a column in a result set might differ from the metadata for the column as returned by a catalog function. For example, suppose that an updatable column is included in a result set created by joining two tables. While <legacyBold>SQLColumnPrivileges</legacyBold> might indicate that a user can update the column, the result set metadata might not if the column is on the "many" side of the join; many data sources can update columns on the "one" side of a join but not on the "many" side. Even data types cannot be assumed to be the same, because the data source might promote the data type while creating the result set.</para>
    <para>This section contains the following topics.  </para>
    <list class="bullet">
      <listItem>
        <para>             <legacyLink xlink:href="70fb976c-9342-4edd-b066-1140696fd0fa">How is Metadata Used?</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="c2ca442c-03a8-4e0f-9e67-b300bb15962f">SQLDescribeCol and SQLColAttribute</legacyLink>           </para>
      </listItem>
    </list>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>