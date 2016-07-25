---
title: "SQLGetData and Block Cursors"
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 12599cdc-7725-4faf-bcae-e163ea0f5851
caps.latest.revision: 4
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# SQLGetData and Block Cursors
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>       <legacyBold>SQLGetData</legacyBold> operates on a single column of a single row and cannot fetch an array containing data from multiple rows. This is because the primary use of <legacyBold>SQLGetData</legacyBold> is to fetch long data in parts, and there is little or no reason to do this for more than one row at a time.</para>
    <para>To use <legacyBold>SQLGetData</legacyBold> with a block cursor, an application first calls <legacyBold>SQLSetPos</legacyBold> to position the cursor on a single row. It then calls <legacyBold>SQLGetData</legacyBold> for a column in that row. However, this behavior is optional. To determine if a driver supports the use of <legacyBold>SQLGetData</legacyBold> with block cursors, an application calls <legacyBold>SQLGetInfo</legacyBold> with the SQL_GETDATA_EXTENSIONS option.</para>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>