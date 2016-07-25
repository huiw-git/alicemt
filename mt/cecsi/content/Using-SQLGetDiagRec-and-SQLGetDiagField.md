---
title: "Using SQLGetDiagRec and SQLGetDiagField"
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4f486bb1-fad8-4064-ac9d-61f2de85b68b
caps.latest.revision: 4
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Using SQLGetDiagRec and SQLGetDiagField
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Applications call <legacyBold>SQLGetDiagRec</legacyBold> or <legacyBold>SQLGetDiagField</legacyBold> to retrieve diagnostic information. These functions accept an environment, connection, statement, or descriptor handle and return diagnostics from the function that last used that handle. The diagnostics logged on a particular handle are discarded when a new function is called using that handle. If the function returned multiple diagnostic records, the application calls these functions multiple times; the total number of status records is retrieved by calling <legacyBold>SQLGetDiagField</legacyBold> for the header record (record 0) with the SQL_DIAG_NUMBER option.</para>
    <para>Applications retrieve individual diagnostic fields by calling <legacyBold>SQLGetDiagField</legacyBold> and specifying the field to retrieve. Certain diagnostic fields do not have any meaning for certain types of handles. For a list of diagnostic fields and their meanings, see the <legacyLink xlink:href="1dbc4398-97a8-4585-bb77-1f7ea75e24c4">SQLGetDiagField</legacyLink> function description.</para>
    <para>Applications retrieve the SQLSTATE, native error code, and diagnostic message in a single call by calling <legacyBold>SQLGetDiagRec</legacyBold>; <legacyBold>SQLGetDiagRec</legacyBold> cannot be used to retrieve information from the header record.</para>
    <para>For example, the following code prompts the user for an SQL statement and executes it. If any diagnostic information was returned, it calls <legacyBold>SQLGetDiagField</legacyBold> to get the number of status records and <legacyBold>SQLGetDiagRec</legacyBold> to get the SQLSTATE, native error code, and diagnostic message from those records.</para>
    <code>SQLCHAR       SqlState[6], SQLStmt[100], Msg[SQL_MAX_MESSAGE_LENGTH];
SQLINTEGER    NativeError;
SQLSMALLINT   i, MsgLen;
SQLRETURN     rc1, rc2;
SQLHSTMT      hstmt;

// Prompt the user for an SQL statement.
GetSQLStmt(SQLStmt);

// Execute the SQL statement and return any errors or warnings.
rc1 = SQLExecDirect(hstmt, SQLStmt, SQL_NTS);
if ((rc1 == SQL_SUCCESS_WITH_INFO) || (rc1 == SQL_ERROR)) {
   // Get the status records.
   i = 1;
   while ((rc2 = SQLGetDiagRec(SQL_HANDLE_STMT, hstmt, i, SqlState, &amp;NativeError,
            Msg, sizeof(Msg), &amp;MsgLen)) != SQL_NO_DATA) {
      DisplayError(SqlState,NativeError,Msg,MsgLen);
      i++;
   }
}

if ((rc1 == SQL_SUCCESS) || (rc1 == SQL_SUCCESS_WITH_INFO)) {
   // Process statement results, if any.
}</code>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>