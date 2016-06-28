---
title: WHERE Clause Limitations
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 46b54f74-e4a3-4318-87cf-8a97c38a2718
translation.priority.ht: 
  - en-gb
---
# WHERE Clause Limitations
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The maximum number of clauses in a WHERE clause is 40.</para>
    <para>LONGVARBINARY and LONGVARCHAR columns can be compared to literals of up to 255 characters in length, but cannot be compared using parameters.</para>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>