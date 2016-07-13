---
title: Allocating a Statement Handle ODBC
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4ce3b446-34ab-46dc-96e5-f40ec95c267e
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Allocating a Statement Handle ODBC
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Before the application can execute a statement, it must allocate a statement handle as follows:  </para>
    <list class="ordered">
      <listItem>
        <para>The application declares a variable of type HSTMT. It then calls <legacyBold>SQLAllocHandle</legacyBold> and passes the address of this variable, the handle of the connection in which to allocate the statement, and the SQL_HANDLE_STMT option. For example: </para>
        <code>SQLHSTMT hstmt1;

SQLAllocHandle(SQL_HANDLE_STMT, hdbc1, &amp;hstmt1);</code>
      </listItem>
      <listItem>
        <para>The Driver Manager allocates a structure in which to store information about the statement and calls <legacyBold>SQLAllocHandle</legacyBold> in the driver with the SQL_HANDLE_STMT option.</para>
      </listItem>
      <listItem>
        <para>The driver allocates its own structure in which to store information about the statement and returns the driver statement handle to the Driver Manager.</para>
      </listItem>
      <listItem>
        <para>The Driver Manager returns the Driver Manager statement handle to the application in the application variable.</para>
      </listItem>
    </list>
    <para>The statement handle identifies which statement to use when calling ODBC functions. For more information about statement handles, see <legacyLink xlink:href="65d6d78b-a8c8-489a-9dad-f8d127a44882">Statement Handles</legacyLink>.</para>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>