---
title: Limitations of Using Keyset-Driven Cursors
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 59d86fed-387c-4719-9550-36343e74da44
translation.priority.ht: 
  - en-gb
---
# Limitations of Using Keyset-Driven Cursors
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <alert class="important">
      <para>This feature will be removed in a future version of Windows. Avoid using this feature in new development work, and plan to modify applications that currently use this feature. Instead, use the ODBC driver provided by Oracle.</para>
    </alert>
    <para>You must be able to retrieve a single ROWID column for the table queried. A keyset-driven cursor cannot be used on joins, queries, or statements that contain DISTINCT, GROUP BY, UNION, INTERSECT, or MINUS clauses.</para>
    <para>Also, if your application uses table aliases, keyset-driven cursors will not work; forward-only or static cursor types are required. Using the keyset cursor type with table aliases will cause the following error: "[Microsoft][ODBC driver for Oracle]Cannot use Keyset-driven cursor on join, with union, intersect or minus or on read only result set."</para>
    <alert class="note">
      <para>Because of the way the driver handles the SQL statement that is sent to the Oracle server, Oracle internally returns the following error message: "ORA-00964: table name not in FROM list."</para>
    </alert>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>