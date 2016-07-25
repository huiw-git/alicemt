---
title: "SQLSetPos (Desktop Database Drivers)"
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 8ef027ec-8512-48fe-8fe2-2ff7cd81e331
caps.latest.revision: 4
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# SQLSetPos (Desktop Database Drivers)
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The bulk-model semantics for <legacyBold>SQLSetPos</legacyBold> calls with the <legacyItalic>irow</legacyItalic> argument equal to 0 are supported.</para>
    <para>SQL_LOCK_NO_CHANGE is supported for <legacyItalic>fLock</legacyItalic>. SQL_LOCK_EXCLUSIVE and SQL_LOCK_UNLOCK are not supported.</para>
    <para>         <legacyBold>SQLSetPos</legacyBold> supports updatable joins. (For more information, see the <legacyItalic>Microsoft Jet Database Engine Programmer's Guide</legacyItalic>.)</para>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>