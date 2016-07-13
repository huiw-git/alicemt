---
title: SQLSetScrollOptions (Desktop Database Drivers)
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 51d643ed-015b-4639-969a-9491d9875aca
manager:jhubbard
translation.priority.ht: 
  - en-gb
---
# SQLSetScrollOptions (Desktop Database Drivers)
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Forward and static cursors are supported for SQL_CONCUR_READ_ONLY. </para>
    <para>Only keyset-driven cursors are supported for an <legacyItalic>fConcurrency</legacyItalic> argument of SQL_CONCUR_LOCK. </para>
    <para>An <legacyItalic>fConcurrency</legacyItalic> argument of SQL_CONCUR_ROWVER is not supported.</para>
    <para>Dynamic cursors and mixed cursors are not supported.</para>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>