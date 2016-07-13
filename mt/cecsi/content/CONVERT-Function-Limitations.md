---
title: CONVERT Function Limitations
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3c81fc58-57f0-4dd7-be16-2b146eb15cbc
manager:jhubbard
translation.priority.ht: 
  - en-gb
---
# CONVERT Function Limitations
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Type conversion failures result in the affected column being set to NULL.</para>
    <para>Neither the DATE nor TIMESTAMP data type can be converted to another data type (or itself) by the CONVERT function.</para>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>