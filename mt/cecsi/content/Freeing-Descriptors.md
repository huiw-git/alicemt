---
title: Freeing Descriptors
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 317213f4-0ebb-4bf8-a37a-4d6b1313823f
manager:jhubbard
translation.priority.ht: 
  - en-gb
---
# Freeing Descriptors
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Explicitly allocated descriptors can be freed either explicitly, by calling <legacyBold>SQLFreeHandle</legacyBold> with <legacyItalic>HandleType</legacyItalic> of SQL_HANDLE_DESC, or implicitly, when the connection handle is freed. When an explicitly allocated descriptor is freed, all statement handles to which the freed descriptor applied automatically revert to the descriptors implicitly allocated for them.</para>
    <para>Implicitly allocated descriptors can be freed only by calling <legacyBold>SQLDisconnect</legacyBold>, which drops any statements or descriptors open on the connection, or by calling <legacyBold>SQLFreeHandle</legacyBold> with a <legacyItalic>HandleType</legacyItalic> of SQL_HANDLE_STMT to free a statement handle and all the implicitly allocated descriptors associated with the statement. An implicitly allocated descriptor cannot be freed by calling <legacyBold>SQLFreeHandle</legacyBold> with a <legacyItalic>HandleType</legacyItalic> of SQL_HANDLE_DESC. </para>
    <para>Even when freed, an implicitly allocated descriptor remains valid, and <legacyBold>SQLGetDescField </legacyBold>can be called on its fields. </para>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>