---
title: Core Level API Functions (ODBC Driver for Oracle)
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 8596eed7-bda6-4cac-ae1f-efde1aab785f
manager:jhubbard
translation.priority.ht: 
  - en-gb
---
# Core Level API Functions (ODBC Driver for Oracle)
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <alert class="important">
      <para>This feature will be removed in a future version of Windows. Avoid using this feature in new development work, and plan to modify applications that currently use this feature. Instead, use the ODBC driver provided by Oracle.</para>
    </alert>
    <para>Functions at this level comprise the minimum level of interface conformance for ODBC drivers.</para>
    <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
      <thead>
        <tr>
          <TD>
            <para>API function</para>
          </TD>
          <TD>
            <para>Notes</para>
          </TD>
        </tr>
      </thead>
      <tbody>
        <tr>
          <TD>
            <para>
              <legacyBold>SQLAllocConnect</legacyBold>
            </para>
          </TD>
          <TD>
            <para>Allocates memory for a connection handle, <legacyItalic>hdbc</legacyItalic>, within the environment identified by <legacyItalic>henv</legacyItalic>. The Driver Manager processes this call and calls the driver's <legacyBold>SQLAllocConnect</legacyBold> function whenever <legacyBold>SQLConnect</legacyBold>, <legacyBold>SQLBrowseConnect</legacyBold>, or <legacyBold>SQLDriverConnect</legacyBold> is called.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>SQLAllocEnv</legacyBold>
            </para>
          </TD>
          <TD>
            <para>Displays a dialog box specifying the requirement for Oracle Client software and then returns SQL_NULL_HANDLE. If the Oracle Client software is not installed, this function allocates memory for an environment handle, <legacyItalic>henv</legacyItalic>,and initializes the ODBC call-level interface for use by an application.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>SQLAllocStmt</legacyBold>
            </para>
          </TD>
          <TD>
            <para>Allocates memory for a statement handle and associates the statement handle with the connection specified by hdbc. The Driver Manager passes this call to the driver, which allocates the memory for the hstmt structure.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>SQLBindCol</legacyBold>
            </para>
          </TD>
          <TD>
            <para>Assigns storage space for a result column and specifies the type of the result. </para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>SQLCancel</legacyBold>
            </para>
          </TD>
          <TD>
            <para>Cancels the processing on a statement handle, hstmt. In some cases, Oracle does not allow cancellation of a running statement. This means that a running statement will continue until Oracle completes the process, at which time the results from the statements are canceled by the ODBC Driver for Oracle.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>SQLColAttributes</legacyBold>
            </para>
          </TD>
          <TD>
            <para>Returns descriptor information for a column in a result set. Descriptor information is returned as a character string, a 32-bit descriptor-dependent value, or an integer value. </para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>SQLConnect</legacyBold>
            </para>
          </TD>
          <TD>
            <para>Connects to a data source. To use Oracle Operating System Authentication, specify "/" as the <legacyItalic>szUID</legacyItalic> parameter and "" as the <legacyItalic>szAuthStr</legacyItalic> parameter.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>SQLDescribeCol</legacyBold>
            </para>
          </TD>
          <TD>
            <para>Returns the name, type, precision, scale, and nullability of the given result column.</para>
            <alert class="note">
              <para> <legacyBold>SQLDescribeCol</legacyBold> reports calculated columns as SQL_VARCHAR. </para>
            </alert>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>SQLDisconnect</legacyBold>
            </para>
          </TD>
          <TD>
            <para>Closes a connection. If connection pooling is enabled for a shared environment and an application calls <legacyBold>SQLDisconnect</legacyBold> on a connection in that environment, the connection is returned to the connection pool and is still available to other components using the same shared environment.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>SQLError</legacyBold>
            </para>
          </TD>
          <TD>
            <para>Returns error or status information about the last error. The driver maintains a stack or list of errors that can be returned for the <legacyItalic>hstmt</legacyItalic>, <legacyItalic>hdbc</legacyItalic>, and <legacyItalic>henv</legacyItalic> arguments, depending on how the call to <legacyBold>SQLError</legacyBold> is made. The error queue is flushed after each statement. Usually retrieves an Oracle error message and is otherwise empty.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>SQLExecDirect</legacyBold>
            </para>
          </TD>
          <TD>
            <para>Executes a new, unprepared SQL statement. The driver uses the current values of the parameter marker variables if any parameters exist in the statement. If your table, view, or field names contain spaces, enclose the names in back quote marks. For example, if your database contains a table named <legacyItalic>My Table</legacyItalic> and the field <legacyItalic>My Field</legacyItalic>, enclose each element of the identifier like so:</para>
            <para>SELECT `My Table`. `My Field1`,; `My Table`.`My Field2` FROM `My Table`</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>SQLExecute</legacyBold>
            </para>
          </TD>
          <TD>
            <para>Executes a prepared SQL statement (a statement already prepared by <legacyBold>SQLPrepare</legacyBold>). The driver uses the current values of the parameter marker variables if any parameters exist in the statement.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>SQLFetch</legacyBold>
            </para>
          </TD>
          <TD>
            <para>Retrieves one row from a result set into the locations specified by the previous calls to <legacyBold>SQLBindCol</legacyBold>. Prepares the driver for a call to <legacyBold>SQLGetData</legacyBold> for the unbound columns.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>SQLFreeConnect</legacyBold>
            </para>
          </TD>
          <TD>
            <para>Releases a connection handle and frees all memory allocated for the handle.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>SQLFreeEnv</legacyBold>
            </para>
          </TD>
          <TD>
            <para>Closes the ODBC Driver for Oracle and releases all memory associated with the driver.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>SQLFreeStmt</legacyBold>
            </para>
          </TD>
          <TD>
            <para>Stops processing associated with a specific hstmt, closes any open cursors associated with the hstmt, discards pending results, and optionally frees all resources associated with the statement handle.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>SQLGetCursorName</legacyBold>
            </para>
          </TD>
          <TD>
            <para>Returns the name of the cursor associated with the given hstmt. </para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>SQLNumResultCols</legacyBold>
            </para>
          </TD>
          <TD>
            <para>Returns the number of columns in a result set cursor.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>SQLPrepare</legacyBold>
            </para>
          </TD>
          <TD>
            <para>Prepares an SQL statement by planning how to optimize and execute the statement. The SQL statement is compiled for execution by <legacyBold>SQLExecDirect</legacyBold>.</para>
            <para>If your table, view, or field names contain spaces, enclose the names in back quote marks. For example, if your database contains a table named <legacyItalic>My Table</legacyItalic> and the field <legacyItalic>My Field</legacyItalic>, enclose each element of the identifier as follows:</para>
            <para>SELECT `My Table`.`My Field` FROM `My Table`</para>
            <para>For information about using result sets containing arrays as formal parameters, see <legacyLink xlink:href="2018069b-da5d-4cee-a971-991897d4f7b5">Returning Array Parameters from Stored Procedures</legacyLink>.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>SQLRowCount</legacyBold>
            </para>
          </TD>
          <TD>
            <para>Oracle does not provide a way to determine the number of rows in a result set until after you fetch the last row, so it returns –1.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>SQLSetCursorName</legacyBold>
            </para>
          </TD>
          <TD>
            <para>Associates a cursor name with an active statement handle, <legacyItalic>hstmt</legacyItalic>. </para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>SQLSetParam</legacyBold>
            </para>
          </TD>
          <TD>
            <para>Replaced by SQLBindParameter in ODBC 2.<legacyItalic>x</legacyItalic>.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>SQLTransact</legacyBold>
            </para>
          </TD>
          <TD>
            <para>Requests a commit or rollback operation for all active operations on all statement handles (hstmts) associated with a connection, or for all connections associated with the environment handle, <legacyItalic>henv</legacyItalic>. If a commit fails when in manual mode, the transaction remains active; you can choose to roll back the transaction or retry the commit operation. If a commit operation fails when in automatic transaction mode, the transaction is rolled back automatically; the transaction cannot be inactive.</para>
          </TD>
        </tr>
      </tbody>
    </table>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>