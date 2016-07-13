---
title: Escape Sequences
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 5913abfa-d280-43e4-a2f1-05a924388bf9
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Escape Sequences
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>ODBC defines escape sequences containing standard grammar for date, time, timestamp, and datetime interval literals, scalar function calls, <legacyBold>LIKE</legacyBold> predicate escape characters, outer joins, and procedure calls. Interoperable applications should use these sequences whenever possible.</para>
    <para>To determine if a driver supports the escape sequences for date, time, timestamp, or datetime interval literals, an application calls <legacyBold>SQLGetTypeInfo</legacyBold>. If the data source supports a date, time, timestamp, or datetime interval data type, it must also support the corresponding escape sequence. To determine whether the other escape sequences are supported, an application calls <legacyBold>SQLGetInfo</legacyBold>.</para>
    <para>For more information, see <legacyLink xlink:href="cf229f21-6c38-4b5b-aca8-f1be0dfeb3d0">Escape Sequences in ODBC</legacyLink>, later in this section.</para>
  </introduction>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>