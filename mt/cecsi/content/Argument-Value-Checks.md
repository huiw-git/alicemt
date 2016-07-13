---
title: Argument Value Checks
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 37a65f8b-83aa-456c-b7cf-500404abb38a
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Argument Value Checks
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The Driver Manager checks the following types of arguments. Unless otherwise noted, the Driver Manager returns SQL_ERROR for errors in argument values.  </para>
    <list class="bullet">
      <listItem>
        <para>Environment, connection, and statement handles usually cannot be null pointers. The Driver Manager returns SQL_INVALID_HANDLE when it finds a null handle.</para>
      </listItem>
      <listItem>
        <para>Required pointer arguments, such as <legacyItalic>OutputHandlePtr</legacyItalic> in <legacyBold>SQLAllocHandle</legacyBold> and <legacyItalic>CursorName</legacyItalic> in <legacyBold>SQLSetCursorName</legacyBold>, cannot be null pointers.</para>
      </listItem>
      <listItem>
        <para>Option flags that do not support driver-specific values must be a legal value. For example, <legacyItalic>Operation</legacyItalic> in <legacyBold>SQLSetPos</legacyBold> must be SQL_POSITION, SQL_REFRESH, SQL_UPDATE, SQL_DELETE, or SQL_ADD.</para>
      </listItem>
      <listItem>
        <para>Option flags must be supported in the version of ODBC supported by the driver. For example, <legacyItalic>InfoType</legacyItalic> in <legacyBold>SQLGetInfo</legacyBold> cannot be SQL_ASYNC_MODE (introduced in ODBC 3.0) when calling an ODBC 2.0 driver.</para>
      </listItem>
      <listItem>
        <para>Column and parameter numbers must be greater than 0 or greater than or equal to 0, depending on the function. The driver must check the upper limit of these argument values based on the current result set or SQL statement.</para>
      </listItem>
      <listItem>
        <para>Length/indicator arguments and data buffer length arguments must contain appropriate values. For example, the argument that specifies the length of a table name in <legacyBold>SQLColumns</legacyBold> (<legacyItalic>NameLength3</legacyItalic>) must be SQL_NTS or a value greater than 0; <legacyItalic>BufferLength</legacyItalic> in <legacyBold>SQLDescribeCol</legacyBold> must be greater than or equal to 0. The driver might also need to check these arguments. For example, it might check that <legacyItalic>NameLength3</legacyItalic> is less than or equal to the maximum length of a table name in the data source.</para>
      </listItem>
    </list>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>