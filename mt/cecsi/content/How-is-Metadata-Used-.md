---
title: "How is Metadata Used?"
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 70fb976c-9342-4edd-b066-1140696fd0fa
caps.latest.revision: 4
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# How is Metadata Used?
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Applications require metadata for most result set operations. For example, the application uses the data type of a column to determine what kind of variable to bind to that column. It uses the byte length of a character column to determine how much space it needs to display data from that column. How an application determines the metadata for a column depends on the type of the application.</para>
    <para>Vertical applications work with predefined tables and perform predefined operations on those tables. Because the result set metadata for such applications is defined before the application is even written and is controlled by the application developer, it can be hard-coded into the application. For example, if an order ID column is defined as a 4-byte integer in the data source, the application can always bind a 4-byte integer to that column. When metadata is hard-coded in the application, a change to the tables used by the application generally implies a change to the application code. This is rarely a problem, because such changes are usually made as part of a new release of the application.</para>
    <para>Like vertical applications, custom applications generally work with predefined tables and perform predefined operations on those tables. For example, an application might be written to transfer data among three different data sources; the data to be transferred is usually known when the application is written. Thus, custom applications also tend to have hard-coded metadata.</para>
    <para>Generic applications, especially those that support ad hoc queries, almost never know the metadata of the result sets they create. Therefore, they must discover the metadata at run time using the functions <legacyBold>SQLNumResultCols</legacyBold>, <legacyBold>SQLDescribeCol</legacyBold>, and <legacyBold>SQLColAttribute</legacyBold>, which are described in the next section, <legacyLink xlink:href="c2ca442c-03a8-4e0f-9e67-b300bb15962f">SQLDescribeCol and SQLColAttribute</legacyLink>.</para>
    <para>All applications, regardless of their type, can hard-code metadata for the result sets returned by the catalog functions. These result sets are defined in the reference section of this manual.</para>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>