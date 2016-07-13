---
title: ALTER TABLE Statement Limitations
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f3e88f85-edf4-47cd-a822-292b106ddb34
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# ALTER TABLE Statement Limitations
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>When the dBASE or Paradox driver is used, once an index has been created and a new record added, the structure of the table cannot be changed by the ALTER TABLE statement unless the index is dropped and the contents of the table are deleted.</para>
    <para>ALTER TABLE statements are not supported for the Microsoft Excel or Text drivers.</para>
    <alert class="note">
      <para>When you use the Paradox driver without implementing the Borland Database Engine, ALTER TABLE statements are not supported; only read and append statements are allowed. </para>
    </alert>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>