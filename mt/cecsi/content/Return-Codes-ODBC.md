---
title: Return Codes ODBC
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e893b719-4392-476f-911a-5ed6da6f7e94
manager:jhubbard
translation.priority.ht: 
  - en-gb
---
# Return Codes ODBC
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Each function in ODBC returns a code, known as its <legacyItalic>return code,</legacyItalic> which indicates the overall success or failure of the function. Program logic is generally based on return codes.</para>
    <para>For example, the following code calls <legacyBold>SQLFetch</legacyBold> to retrieve the rows in a result set. It checks the return code of the function to determine if the end of the result set was reached (SQL_NO_DATA), if any warning information was returned (SQL_SUCCESS_WITH_INFO), or if an error occurred (SQL_ERROR).</para>
    <code>SQLRETURN   rc;
SQLHSTMT    hstmt;

while ((rc=SQLFetch(hstmt)) != SQL_NO_DATA) {
   if (rc == SQL_SUCCESS_WITH_INFO) {
      // Call function to display warning information.
   } else if (rc == SQL_ERROR) {
      // Call function to display error information.
      break;
   }
   // Process row.
}</code>
    <para>The return code SQL_INVALID_HANDLE always indicates a programming error and should never be encountered at run time. All other return codes provide run-time information, although SQL_ERROR may indicate a programming error.</para>
    <para>The following table defines the return codes.</para>
    <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
      <thead>
        <tr>
          <TD>
            <para>Return code</para>
          </TD>
          <TD>
            <para>Description</para>
          </TD>
        </tr>
      </thead>
      <tbody>
        <tr>
          <TD>
            <para>SQL_SUCCESS</para>
          </TD>
          <TD>
            <para>Function completed successfully. The application calls <legacyBold>SQLGetDiagField</legacyBold> to retrieve additional information from the header record.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_SUCCESS_WITH_INFO</para>
          </TD>
          <TD>
            <para>Function completed successfully, possibly with a nonfatal error (warning). The application calls <legacyBold>SQLGetDiagRec</legacyBold> or <legacyBold>SQLGetDiagField</legacyBold> to retrieve additional information.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_ERROR</para>
          </TD>
          <TD>
            <para>Function failed. The application calls <legacyBold>SQLGetDiagRec</legacyBold> or <legacyBold>SQLGetDiagField</legacyBold> to retrieve additional information. The contents of any output arguments to the function are undefined.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_INVALID_HANDLE</para>
          </TD>
          <TD>
            <para>Function failed due to an invalid environment, connection, statement, or descriptor handle. This indicates a programming error. No additional information is available from <legacyBold>SQLGetDiagRec</legacyBold> or <legacyBold>SQLGetDiagField</legacyBold>. This code is returned only when the handle is a null pointer or is the wrong type, such as when a statement handle is passed for an argument that requires a connection handle.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_NO_DATA</para>
          </TD>
          <TD>
            <para>No more data was available. The application calls <legacyBold>SQLGetDiagRec</legacyBold> or <legacyBold>SQLGetDiagField</legacyBold> to retrieve additional information. One or more driver-defined status records in class 02xxx may be returned.</para>
            <alert class="note">
              <para>In ODBC 2.<legacyItalic>x</legacyItalic>, this return code was named SQL_NO_DATA_FOUND.</para>
            </alert>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_NEED_DATA</para>
          </TD>
          <TD>
            <para>More data is needed, such as when parameter data is sent at execution time or additional connection information is required. The application calls <legacyBold>SQLGetDiagRec</legacyBold> or <legacyBold>SQLGetDiagField</legacyBold> to retrieve additional information, if any.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_STILL_EXECUTING</para>
          </TD>
          <TD>
            <para>A function that was started asynchronously is still executing. The application calls <legacyBold>SQLGetDiagRec</legacyBold> or <legacyBold>SQLGetDiagField</legacyBold> to retrieve additional information, if any.</para>
          </TD>
        </tr>
      </tbody>
    </table>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>