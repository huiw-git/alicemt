---
title: SQLDescribeCol and SQLColAttribute
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c2ca442c-03a8-4e0f-9e67-b300bb15962f
manager:jhubbard
translation.priority.ht: 
  - en-gb
---
# SQLDescribeCol and SQLColAttribute
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>       <legacyBold>SQLDescribeCol</legacyBold> and <legacyBold>SQLColAttribute</legacyBold> are used to retrieve result set metadata. The difference between these two functions is that <legacyBold>SQLDescribeCol</legacyBold> always returns the same five pieces of information (a column's name, data type, precision, scale, and nullability), while <legacyBold>SQLColAttribute</legacyBold> returns a single piece of information requested by the application. However, <legacyBold>SQLColAttribute</legacyBold> can return a much richer selection of metadata, including a column's case-sensitivity, display size, updatability, and searchability.</para>
    <para>Many applications, especially ones that only display data, require only the metadata returned by <legacyBold>SQLDescribeCol</legacyBold>. For these applications, it is faster to use <legacyBold>SQLDescribeCol</legacyBold> than <legacyBold>SQLColAttribute</legacyBold> because the information is returned in a single call. Other applications, especially ones that update data, require the additional metadata returned by <legacyBold>SQLColAttribute</legacyBold> and therefore use both functions. In addition, <legacyBold>SQLColAttribute</legacyBold> supports driver-specific metadata; for more information, see <legacyLink xlink:href="ad4c76d3-5191-4262-b47c-5dd1d19d1154">Driver-Specific Data Types, Descriptor Types, Information Types, Diagnostic Types, and Attributes</legacyLink>.</para>
    <para>An application can retrieve result set metadata at any time after a statement has been prepared or executed and before the cursor over the result set is closed. Very few applications require result set metadata after the statement is prepared and before it is executed. If possible, applications should wait to retrieve metadata until after the statement is executed, because some data sources cannot return metadata for prepared statements and emulating this capability in the driver is often a slow process. For example, the driver might generate a zero-row result set by replacing the <legacyBold>WHERE</legacyBold> clause of a <legacyBold>SELECT</legacyBold> statement with the clause <legacyBold>WHERE 1 = 2</legacyBold> and executing the resulting statement.</para>
    <para>Metadata is often expensive to retrieve from the data source. Because of this, drivers should cache any metadata they retrieve from the server and hold it for as long as the cursor over the result set is open. Also, applications should request only the metadata they absolutely need.</para>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>