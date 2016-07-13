---
title: Freeing a Statement Handle ODBC
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ee18e2f1-2690-4cc1-9e5c-e20244e5d480
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Freeing a Statement Handle ODBC
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>As mentioned earlier, it is more efficient to reuse statements than to drop them and allocate new ones. Before executing a new SQL statement on a statement, applications should be sure that the current statement settings are appropriate. These include statement attributes, parameter bindings, and result set bindings. Generally, parameters and result sets for the old SQL statement need to be unbound (by calling <legacyBold>SQLFreeStmt</legacyBold> with the SQL_RESET_PARAMS and SQL_UNBIND options) and rebound for the new SQL statement.</para>
    <para>When the application has finished using the statement, it calls <legacyBold>SQLFreeHandle</legacyBold> to free the statement. After freeing the statement, it is an application programming error to use the statement's handle in a call to an ODBC function; doing so has undefined but probably fatal consequences.</para>
    <para>When <legacyBold>SQLFreeHandle</legacyBold> is called, the driver releases the structure used to store information about the statement.</para>
    <para>         <legacyBold>SQLDisconnect</legacyBold> automatically frees all statements on a connection.</para>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>