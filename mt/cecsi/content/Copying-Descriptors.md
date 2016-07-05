---
title: Copying Descriptors
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 949a860d-6579-4218-882e-8c061688dd87
translation.priority.ht: 
  - en-gb
---
# Copying Descriptors
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The <legacyBold>SQLCopyDesc</legacyBold> function is called to copy the fields of one descriptor to another descriptor. Fields can be copied only to an application descriptor or an IPD, but not to an IRD. Fields can be copied from any type of descriptor. Only those fields that are defined for both the source and target descriptors are copied. <legacyBold>SQLCopyDesc</legacyBold> does not copy the SQL_DESC_ALLOC_TYPE field, because a descriptor's allocation type cannot be changed. Copied fields overwrite the existing fields. </para>
    <para>An ARD on one statement handle can serve as the APD on another statement handle. This allows an application to copy rows between tables without copying data at the application level. To do this, a row descriptor that describes a fetched row of a table is reused as a parameter descriptor for a parameter in an INSERT statement. The SQL_MAX_CONCURRENT_ACTIVITIES information type must be greater than 1 for this operation to succeed.</para>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>