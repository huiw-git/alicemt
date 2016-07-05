---
title: SQLSetCursorName (Desktop Database Drivers)
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9bd7c87b-d99d-4e23-b2db-868d3b461c94
translation.priority.ht: 
  - en-gb
---
# SQLSetCursorName (Desktop Database Drivers)
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Because the driver does not support a positioned update or delete by the WHERE CURRENT OF <legacyItalic>cursorname</legacyItalic> syntax, <legacyBold>SQLSetCursorName</legacyBold> is supported, but cannot be used for positioned updates. It can only be used when the Cursor Library is enabled and the application is using <legacyBold>SQLExtendedFetch</legacyBold>.</para>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>