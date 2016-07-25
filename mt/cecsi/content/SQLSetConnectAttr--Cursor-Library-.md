---
title: "SQLSetConnectAttr (Cursor Library)"
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6f70bbd0-a057-49ef-8b05-4c80b58fc6e6
caps.latest.revision: 7
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# SQLSetConnectAttr (Cursor Library)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <alert class="important">
      <para>This feature will be removed in a future version of Windows. Avoid using this feature in new development work and plan to modify applications that currently use this feature. Microsoft recommends using the driver's cursor functionality.</para>
    </alert>
    <para>This topic discusses the use of the <legacyBold>SQLSetConnectAttr</legacyBold> function in the cursor library. For general information about <legacyBold>SQLSetConnectAttr</legacyBold>, see <legacyLink xlink:href="97fc7445-5a66-4eb9-8e77-10990b5fd685">SQLSetConnectAttr Function</legacyLink>.</para>
  </introduction>
  <section>
    <content>
      <para>An application calls <legacyBold>SQLSetConnectAttr</legacyBold> with the SQL_ATTR_ODBC_CURSORS attribute to specify whether the cursor library is always used, used if the driver does not support scrollable cursors, or never used. The cursor library assumes that a driver supports scrollable cursors if it returns SQL_CA1_RELATIVE for the SQL_STATIC_CURSOR_ATTRIBUTES1 information type in <legacyBold>SQLGetInfo</legacyBold>.</para>
      <para>The application must call <legacyBold>SQLSetConnectAttr</legacyBold> to specify the cursor library usage after it calls <legacyBold>SQLAllocHandle</legacyBold> with a <legacyItalic>HandleType</legacyItalic> of SQL_HANDLE_DBC to allocate the connection and before it connects to the data source. If an application calls <legacyBold>SQLSetConnectAttr</legacyBold> with the SQL_ATTR_ODBC_CURSORS attribute while the connection is still active, the cursor library returns an error.</para>
      <para>To set a statement attribute supported by the cursor library for all statements associated with a connection, an application must call <legacyBold>SQLSetConnectAttr</legacyBold> for that statement attribute after it connects to the data source and before it opens the cursor. If an application calls <legacyBold>SQLSetConnectAttr</legacyBold> with a statement attribute and a cursor is open on a statement associated with the connection, the statement attribute will not be applied to that statement until the cursor is closed and reopened.</para>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>