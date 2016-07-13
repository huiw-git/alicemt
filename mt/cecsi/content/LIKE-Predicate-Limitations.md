---
title: LIKE Predicate Limitations
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: dbd39099-caf6-4c4c-9ad8-f6c63c1bd5e4
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# LIKE Predicate Limitations
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>If data in a column is longer than 255 characters, the LIKE comparison will be based only on the first 255 characters.</para>
    <para>A LIKE used in a procedure is supported only with constant patterns. The Desktop Database Drivers support SQL-92 LIKE pattern matching.</para>
    <para>Use of an escape clause in a LIKE predicate is not supported.</para>
    <para>A LIKE comparison should not be performed on a column containing data of a numeric or float data type. The results may be unpredictable. For more information, see the <legacyItalic>Microsoft Jet Database Engine Programmer's Guide</legacyItalic>.</para>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>