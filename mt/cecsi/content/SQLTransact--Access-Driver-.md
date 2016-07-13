---
title: SQLTransact (Access Driver)
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 892b79c7-9e20-4d1f-bc60-d4b25694ca25
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# SQLTransact (Access Driver)
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <alert class="note">
      <para>This topic provides Access Driver-specific information. For general information about this function, see the appropriate topic under <legacyLink xlink:href="b7a49774-f458-44ce-9a04-a0457501405b">ODBC API Reference</legacyLink>.</para>
    </alert>
    <para>When the Microsoft Access driver is used, SQL_COMMIT and SQL_ROLLBACK are supported for the <legacyItalic>fType</legacyItalic> argument in a call to <legacyBold>SQLTransact</legacyBold>.</para>
    <para>If a failure occurs during the commit process, the affected database can be repaired using the Repair Database option in the Microsoft Access driver setup, or through the use of the REPAIR_DB keyword in the <legacyBold>SQLConfigDataSource</legacyBold> function.</para>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>