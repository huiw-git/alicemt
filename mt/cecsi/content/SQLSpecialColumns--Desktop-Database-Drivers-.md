---
title: SQLSpecialColumns (Desktop Database Drivers)
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3de66fdf-053b-4354-979d-e76a5a5e975f
manager:jhubbard
translation.priority.ht: 
  - en-gb
---
# SQLSpecialColumns (Desktop Database Drivers)
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>A unique index will be returned (if one exists) for the SQL_BEST_ROWID flag in <legacyItalic>fColType</legacyItalic>. No result set will be returned for the SQL_ROWVER flag. </para>
    <para>All row IDs have a scope of SQL_SCOPE_CURROW.</para>
    <para>Pattern matching is not supported for either the <legacyItalic>szTableQualifier</legacyItalic> or <legacyItalic>szTableName</legacyItalic> argument.</para>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>