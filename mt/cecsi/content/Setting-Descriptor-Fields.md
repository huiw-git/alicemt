---
title: Setting Descriptor Fields
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d735dc64-370f-48ab-a59f-6cef9bc4e1e8
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Setting Descriptor Fields
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>To modify the fields of a descriptor, an application can call <legacyBold>SQLSetDescField</legacyBold>. Some fields are read-only and cannot be set. (See the <legacyLink xlink:href="8c544388-fe9d-4f94-a0ac-fa0b9c9c88a5">SQLSetDescField</legacyLink> function description.) </para>
    <para>Descriptor record fields are set with a record number (<legacyItalic>RecNumber</legacyItalic>) of 1 or higher, while descriptor header fields are set with a record number of 0. A record number of 0 is also used to set bookmark fields, in accordance with the convention that bookmarks are contained in column 0. This might leave the impression that bookmark fields are contained within the descriptor header, but this is not the case. Bookmark fields are distinct from header fields.</para>
    <para>When setting fields individually, the application should follow the sequence defined in <legacyLink xlink:href="8c544388-fe9d-4f94-a0ac-fa0b9c9c88a5">SQLSetDescField</legacyLink>. Setting some fields causes the driver to set other fields. This ensures that the descriptor is always ready to use once the application has specified a data type. When the application sets the SQL_DESC_TYPE field, the driver checks that other fields that specify the type are valid and consistent.</para>
    <para>If a function call that would set a descriptor field fails, the contents of the descriptor field are undefined after the failed function call.</para>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>