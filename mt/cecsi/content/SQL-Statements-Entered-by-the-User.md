---
title: SQL Statements Entered by the User
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 109af162-93ba-425a-8fe5-49c7dc7cc784
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# SQL Statements Entered by the User
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Applications that perform ad hoc analysis also commonly allow the user to enter SQL statements directly. For example:</para>
    <code>SQLCHAR *     Statement, SqlState[6], Msg[SQL_MAX_MESSAGE_LENGTH];
SQLSMALLINT   i, MsgLen;
SQLINTEGER    NativeError;
SQLRETURN     rc1, rc2;

// Prompt user for SQL statement.
GetSQLStatement(Statement);

// Execute the statement directly. Because it will be executed only once,
// do not prepare it.
rc1 = SQLExecDirect(hstmt, Statement, SQL_NTS);

// Process any errors or returned information.
if ((rc1 == SQL_ERROR) || rc1 == SQL_SUCCESS_WITH_INFO) {
   i = 1;
   while ((rc2 = SQLGetDiagRec(SQL_HANDLE_STMT, hstmt, i, SqlState, &amp;NativeError,
         Msg, sizeof(Msg), &amp;MsgLen)) != SQL_NO_DATA) {
      DisplayError(SqlState, NativeError, Msg, MsgLen);
      i++;
   }
}</code>
    <para>This approach simplifies application coding; the application relies on the user to build the SQL statement and on the data source to check the statement's validity. Because it's difficult to write a graphical user interface that adequately exposes the intricacies of SQL, simply asking the user to enter the SQL statement text may be a preferable alternative. However, this requires the user to know not only SQL but also the schema of the data source being queried. Some applications provide a graphical user interface by which the user can create a basic SQL statement and also provide a text interface with which the user can modify it.</para>
  </introduction>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>