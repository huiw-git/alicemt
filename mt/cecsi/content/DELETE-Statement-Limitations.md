---
title: DELETE Statement Limitations
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 084761fe-e65b-4f38-ba4f-69884b2a7700
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# DELETE Statement Limitations
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The DELETE statement is not supported for the Microsoft Excel or Text driver. Note that the INSERT statement is supported for the Text driver.</para>
    <para>The dBASE driver does not support packing a table to remove "deleted" values.</para>
    <para>For the Paradox driver to delete a row from a table, the table must have a unique index (Paradox primary key). </para>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>