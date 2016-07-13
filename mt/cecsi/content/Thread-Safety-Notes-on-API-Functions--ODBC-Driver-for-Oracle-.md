---
title: Thread-Safety Notes on API Functions (ODBC Driver for Oracle)
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f0c9bdfd-f79d-4088-9ecb-afcd8ca7fb73
manager:jhubbard
translation.priority.ht: 
  - en-gb
---
# Thread-Safety Notes on API Functions (ODBC Driver for Oracle)
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <alert class="important">
      <para>This feature will be removed in a future version of Windows. Avoid using this feature in new development work, and plan to modify applications that currently use this feature. Instead, use the ODBC driver provided by Oracle.</para>
    </alert>
    <para>The Microsoft ODBC Driver for Oracle is thread-safe; however, Oracle does not allow multiple concurrent statements on a single connection. The driver enforces this restriction. In other words, in multithreaded applications, although any thread can call into the ODBC Driver for Oracle at any time, the driver blocks any other thread from the driver on the same connection until the original thread leaves the driver.</para>
    <para>The driver does not block if there are two statements on two different connections. However, if there is a single connection with two statements, there is potential for blocking.</para>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>