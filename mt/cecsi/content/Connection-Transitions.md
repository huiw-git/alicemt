---
title: Connection Transitions
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6b6e1a47-4a52-41c8-bb9e-7ddeae09913e
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Connection Transitions
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>ODBC connections have the following states.</para>
    <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
      <thead>
        <tr>
          <TD>
            <para>State</para>
          </TD>
          <TD>
            <para>Description</para>
          </TD>
        </tr>
      </thead>
      <tbody>
        <tr>
          <TD>
            <para>C0</para>
          </TD>
          <TD>
            <para>Unallocated environment, unallocated connection</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>C1</para>
          </TD>
          <TD>
            <para>Allocated environment, unallocated connection</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>C2</para>
          </TD>
          <TD>
            <para>Allocated environment, allocated connection</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>C3</para>
          </TD>
          <TD>
            <para>Connection function needs data</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>C4</para>
          </TD>
          <TD>
            <para>Connected connection</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>C5</para>
          </TD>
          <TD>
            <para>Connected connection, allocated statement</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>C6</para>
          </TD>
          <TD>
            <para>Connected connection, transaction in progress. It is possible for a connection to be in state C6 with no statements allocated on the connection. For example, suppose the connection is in manual commit mode and is in state C4. If a statement is allocated, executed (starting a transaction), and then freed, the transaction remains active but there are no statements on the connection.</para>
          </TD>
        </tr>
      </tbody>
    </table>
    <para>The following tables show how each ODBC function affects the connection state.</para>
  </introduction>
  <section>
    <title>SQLAllocHandle</title>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>C0 </para>
              <para>No Env.</para>
            </TD>
            <TD>
              <para>C1 Unallocated</para>
            </TD>
            <TD>
              <para>C2</para>
              <para>Allocated</para>
            </TD>
            <TD>
              <para>C3</para>
              <para>Need Data</para>
            </TD>
            <TD>
              <para>C4</para>
              <para>Connected</para>
            </TD>
            <TD>
              <para>C5</para>
              <para>Statement</para>
            </TD>
            <TD>
              <para>C6</para>
              <para>Transaction</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>C1[1]</para>
            </TD>
            <TD>
              <para>--[5]</para>
            </TD>
            <TD>
              <para>--[5]</para>
            </TD>
            <TD>
              <para>--[5]</para>
            </TD>
            <TD>
              <para>--[5]</para>
            </TD>
            <TD>
              <para>--[5]</para>
            </TD>
            <TD>
              <para>--[5]</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>(IH)[2]</para>
            </TD>
            <TD>
              <para>C2</para>
            </TD>
            <TD>
              <para>--[5]</para>
            </TD>
            <TD>
              <para>--[5]</para>
            </TD>
            <TD>
              <para>--[5]</para>
            </TD>
            <TD>
              <para>--[5]</para>
            </TD>
            <TD>
              <para>--[5]</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>(IH)[3]</para>
            </TD>
            <TD>
              <para>(IH)</para>
            </TD>
            <TD>
              <para>(08003)</para>
            </TD>
            <TD>
              <para>(08003)</para>
            </TD>
            <TD>
              <para>C5</para>
            </TD>
            <TD>
              <para>--[5]</para>
            </TD>
            <TD>
              <para>--[5]</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>(IH)[4]</para>
            </TD>
            <TD>
              <para>(IH)</para>
            </TD>
            <TD>
              <para>(08003)</para>
            </TD>
            <TD>
              <para>(08003)</para>
            </TD>
            <TD>
              <para>--[5]</para>
            </TD>
            <TD>
              <para>--[5]</para>
            </TD>
            <TD>
              <para>--[5]</para>
            </TD>
          </tr>
        </tbody>
      </table>
      <para>[1]   This row shows transitions when <legacyItalic>HandleType</legacyItalic> was SQL_HANDLE_ENV.</para>
      <para>[2]   This row shows transitions when <legacyItalic>HandleType</legacyItalic> was SQL_HANDLE_DBC.</para>
      <para>[3]   This row shows transitions when <legacyItalic>HandleType</legacyItalic> was SQL_HANDLE_STMT.</para>
      <para>[4]   This row shows transitions when <legacyItalic>HandleType</legacyItalic> was SQL_HANDLE_DESC.</para>
      <para>[5]   Calling <legacyBold>SQLAllocHandle</legacyBold> with <legacyItalic>OutputHandlePtr</legacyItalic> pointing to a valid handle overwrites that handle without regard for the previous contents ofthat handle, and might cause problems for ODBC drivers. It is incorrect ODBC application programming to call <legacyBold>SQLAllocHandle</legacyBold> twice with the same application variable defined for <legacyItalic>*OutputHandlePtr</legacyItalic> without calling <legacyBold>SQLFreeHandle</legacyBold> to free the handle before reallocating it. Overwriting ODBC handles in such a manner can lead to inconsistent behavior or errors on the part of ODBC drivers.</para>
    </content>
  </section>
  <section>
    <title>SQLBrowseConnect</title>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>C0 </para>
              <para>No Env.</para>
            </TD>
            <TD>
              <para>C1</para>
              <para>Unallocated</para>
            </TD>
            <TD>
              <para>C2</para>
              <para>Allocated</para>
            </TD>
            <TD>
              <para>C3</para>
              <para>Need Data</para>
            </TD>
            <TD>
              <para>C4</para>
              <para>Connected</para>
            </TD>
            <TD>
              <para>C5</para>
              <para>Statement</para>
            </TD>
            <TD>
              <para>C6</para>
              <para>Transaction</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>(IH)</para>
            </TD>
            <TD>
              <para>(IH)</para>
            </TD>
            <TD>
              <para>C3 [d] C4 [s]</para>
            </TD>
            <TD>
              <para>-- [d] C2 [e] C4 [s]</para>
            </TD>
            <TD>
              <para>(08002)</para>
            </TD>
            <TD>
              <para>(08002)</para>
            </TD>
            <TD>
              <para>(08002)</para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <section>
    <title>SQLCloseCursor</title>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>C0 </para>
              <para>No Env.</para>
            </TD>
            <TD>
              <para>C1</para>
              <para>Unallocated</para>
            </TD>
            <TD>
              <para>C2</para>
              <para>Allocated</para>
            </TD>
            <TD>
              <para>C3</para>
              <para>Need Data</para>
            </TD>
            <TD>
              <para>C4</para>
              <para>Connected</para>
            </TD>
            <TD>
              <para>C5</para>
              <para>Statement</para>
            </TD>
            <TD>
              <para>C6</para>
              <para>Transaction</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>(IH)</para>
            </TD>
            <TD>
              <para>(IH)</para>
            </TD>
            <TD>
              <para>(IH)</para>
            </TD>
            <TD>
              <para>(IH)</para>
            </TD>
            <TD>
              <para>(IH)</para>
            </TD>
            <TD>
              <para>--</para>
            </TD>
            <TD>
              <para>--[1] C5[2]</para>
            </TD>
          </tr>
        </tbody>
      </table>
      <para>[1]   The connection was in manual-commit mode.</para>
      <para>[2]   The connection was in auto-commit mode.</para>
    </content>
  </section>
  <section>
    <title>SQLColumnPrivileges, SQLColumns, SQLForeignKeys, SQLGetTypeInfo, SQLPrimaryKeys, SQLProcedureColumns, SQLProcedures, SQLSpecialColumns, SQLStatistics, SQLTablePrivileges, and SQLTables</title>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>C0 </para>
              <para>No Env.</para>
            </TD>
            <TD>
              <para>C1</para>
              <para>Unallocated</para>
            </TD>
            <TD>
              <para>C2</para>
              <para>Allocated</para>
            </TD>
            <TD>
              <para>C3</para>
              <para>Need Data</para>
            </TD>
            <TD>
              <para>C4</para>
              <para>Connected</para>
            </TD>
            <TD>
              <para>C5</para>
              <para>Statement</para>
            </TD>
            <TD>
              <para>C6</para>
              <para>Transaction</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>(IH)</para>
            </TD>
            <TD>
              <para>(IH)</para>
            </TD>
            <TD>
              <para>(IH)</para>
            </TD>
            <TD>
              <para>(IH)</para>
            </TD>
            <TD>
              <para>(IH)</para>
            </TD>
            <TD>
              <para>--[1] C6[2]</para>
            </TD>
            <TD>
              <para>--</para>
            </TD>
          </tr>
        </tbody>
      </table>
      <para>[1]   The connection was in auto-commit mode, or the data source did not begin a transaction.</para>
      <para>[2]   The connection was in manual-commit mode, and the data source began a transaction.</para>
    </content>
  </section>
  <section>
    <title>SQLConnect</title>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>C0 </para>
              <para>No Env.</para>
            </TD>
            <TD>
              <para>C1</para>
              <para>Unallocated</para>
            </TD>
            <TD>
              <para>C2</para>
              <para>Allocated</para>
            </TD>
            <TD>
              <para>C3</para>
              <para>Need Data</para>
            </TD>
            <TD>
              <para>C4</para>
              <para>Connected</para>
            </TD>
            <TD>
              <para>C5</para>
              <para>Statement</para>
            </TD>
            <TD>
              <para>C6</para>
              <para>Transaction</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>(IH)</para>
            </TD>
            <TD>
              <para>(IH)</para>
            </TD>
            <TD>
              <para>C4</para>
            </TD>
            <TD>
              <para>(08002)</para>
            </TD>
            <TD>
              <para>(08002)</para>
            </TD>
            <TD>
              <para>(08002)</para>
            </TD>
            <TD>
              <para>(08002)</para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <section>
    <title>SQLCopyDesc, SQLGetDescField, SQLGetDescRec, SQLSetDescField, and SQLSetDescRec</title>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>C0 </para>
              <para>No Env.</para>
            </TD>
            <TD>
              <para>C1</para>
              <para>Unallocated</para>
            </TD>
            <TD>
              <para>C2</para>
              <para>Allocated</para>
            </TD>
            <TD>
              <para>C3</para>
              <para>Need Data</para>
            </TD>
            <TD>
              <para>C4</para>
              <para>Connected</para>
            </TD>
            <TD>
              <para>C5</para>
              <para>Statement</para>
            </TD>
            <TD>
              <para>C6</para>
              <para>Transaction</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>(IH)</para>
            </TD>
            <TD>
              <para>(IH)</para>
            </TD>
            <TD>
              <para>(IH)</para>
            </TD>
            <TD>
              <para>(IH)</para>
            </TD>
            <TD>
              <para>--[1]</para>
            </TD>
            <TD>
              <para>--</para>
            </TD>
            <TD>
              <para>--</para>
            </TD>
          </tr>
        </tbody>
      </table>
      <para>[1]   In this state, the only descriptors available to the application are explicitly allocated descriptors.</para>
    </content>
  </section>
  <section>
    <title>SQLDataSources and SQLDrivers</title>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>C0 </para>
              <para>No Env.</para>
            </TD>
            <TD>
              <para>C1</para>
              <para>Unallocated</para>
            </TD>
            <TD>
              <para>C2</para>
              <para>Allocated</para>
            </TD>
            <TD>
              <para>C3</para>
              <para>Need Data</para>
            </TD>
            <TD>
              <para>C4</para>
              <para>Connected</para>
            </TD>
            <TD>
              <para>C5</para>
              <para>Statement</para>
            </TD>
            <TD>
              <para>C6</para>
              <para>Transaction</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>(IH)</para>
            </TD>
            <TD>
              <para>--</para>
            </TD>
            <TD>
              <para>--</para>
            </TD>
            <TD>
              <para>--</para>
            </TD>
            <TD>
              <para>--</para>
            </TD>
            <TD>
              <para>--</para>
            </TD>
            <TD>
              <para>--</para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <section>
    <title>SQLDisconnect</title>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>C0 </para>
              <para>No Env.</para>
            </TD>
            <TD>
              <para>C1</para>
              <para>Unallocated</para>
            </TD>
            <TD>
              <para>C2</para>
              <para>Allocated</para>
            </TD>
            <TD>
              <para>C3</para>
              <para>Need Data</para>
            </TD>
            <TD>
              <para>C4</para>
              <para>Connected</para>
            </TD>
            <TD>
              <para>C5</para>
              <para>Statement</para>
            </TD>
            <TD>
              <para>C6</para>
              <para>Transaction</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>(IH)</para>
            </TD>
            <TD>
              <para>(IH)</para>
            </TD>
            <TD>
              <para>(08003)</para>
            </TD>
            <TD>
              <para>C2</para>
            </TD>
            <TD>
              <para>C2</para>
            </TD>
            <TD>
              <para>C2</para>
            </TD>
            <TD>
              <para>25000</para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <section>
    <title>SQLDriverConnect</title>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>C0 </para>
              <para>No Env.</para>
            </TD>
            <TD>
              <para>C1</para>
              <para>Unallocated</para>
            </TD>
            <TD>
              <para>C2</para>
              <para>Allocated</para>
            </TD>
            <TD>
              <para>C3</para>
              <para>Need Data</para>
            </TD>
            <TD>
              <para>C4</para>
              <para>Connected</para>
            </TD>
            <TD>
              <para>C5</para>
              <para>Statement</para>
            </TD>
            <TD>
              <para>C6</para>
              <para>Transaction</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>(IH)</para>
            </TD>
            <TD>
              <para>(IH)</para>
            </TD>
            <TD>
              <para>C4 s -- n[f]</para>
            </TD>
            <TD>
              <para>(08002)</para>
            </TD>
            <TD>
              <para>(08002)</para>
            </TD>
            <TD>
              <para>(08002)</para>
            </TD>
            <TD>
              <para>(08002)</para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <section>
    <title>SQLEndTran</title>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>C0 </para>
              <para>No Env.</para>
            </TD>
            <TD>
              <para>C1</para>
              <para>Unallocated</para>
            </TD>
            <TD>
              <para>C2</para>
              <para>Allocated</para>
            </TD>
            <TD>
              <para>C3</para>
              <para>Need Data</para>
            </TD>
            <TD>
              <para>C4</para>
              <para>Connected</para>
            </TD>
            <TD>
              <para>C5</para>
              <para>Statement</para>
            </TD>
            <TD>
              <para>C6</para>
              <para>Transaction</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>(IH)[1]</para>
            </TD>
            <TD>
              <para>--[3]</para>
            </TD>
            <TD>
              <para>--[3]</para>
            </TD>
            <TD>
              <para>--[3]</para>
            </TD>
            <TD>
              <para>--</para>
            </TD>
            <TD>
              <para>--</para>
            </TD>
            <TD>
              <para>--[4] or ([5], [6], and [8]) C4[5] and [7] C5[5], [6], and [9]</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>(IH)[2]</para>
            </TD>
            <TD>
              <para>(IH)</para>
            </TD>
            <TD>
              <para>(08003)</para>
            </TD>
            <TD>
              <para>(08003)</para>
            </TD>
            <TD>
              <para>--</para>
            </TD>
            <TD>
              <para>--</para>
            </TD>
            <TD>
              <para>C5</para>
            </TD>
          </tr>
        </tbody>
      </table>
      <para>[1]   This row shows transitions when <legacyItalic>HandleType</legacyItalic> was SQL_HANDLE_ENV.</para>
      <para>[2]   This row shows transitions when <legacyItalic>HandleType</legacyItalic> was SQL_HANDLE_DBC.</para>
      <para>[3]   Because the connection is not in a connected state, it is unaffected by the transaction.</para>
      <para>[4]   The commit or rollback failed on the connection. The function returns SQL_ERROR in this case.</para>
      <para>[5]   The commit or rollback succeeded on the connection. The function returns SQL_ERROR if the commit or rollback failed on another connection, or the function returns SQL_SUCCESS if the commit or rollback succeeded on all connections.</para>
      <para>[6]   There was at least one statement allocated on the connection.</para>
      <para>[7]   There were no statements allocated on the connection.</para>
      <para>[8]   The connection had at least one statement for which there was an open cursor, and the data source preserves cursors when transactions are committed or rolled back, whichever applies (depending on whether <legacyItalic>CompletionType</legacyItalic> was SQL_COMMIT or SQL_ROLLBACK). For more information, see the SQL_CURSOR_COMMIT_BEHAVIOR and SQL_CURSOR_ROLLBACK_BEHAVIOR attributes in <legacyLink xlink:href="49dceccc-d816-4ada-808c-4c6138dccb64">SQLGetInfo</legacyLink>.</para>
      <para>[9]   If the connection had any statements for which there were open cursors, the cursors were not preserved when the transaction was committed or rolled back.</para>
    </content>
  </section>
  <section>
    <title>SQLExecDirect and SQLExecute</title>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>C0 </para>
              <para>No Env.</para>
            </TD>
            <TD>
              <para>C1</para>
              <para>Unallocated</para>
            </TD>
            <TD>
              <para>C2</para>
              <para>Allocated</para>
            </TD>
            <TD>
              <para>C3</para>
              <para>Need Data</para>
            </TD>
            <TD>
              <para>C4</para>
              <para>Connected</para>
            </TD>
            <TD>
              <para>C5</para>
              <para>Statement</para>
            </TD>
            <TD>
              <para>C6</para>
              <para>Transaction</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>(IH)</para>
            </TD>
            <TD>
              <para>(IH)</para>
            </TD>
            <TD>
              <para>(IH)</para>
            </TD>
            <TD>
              <para>(IH)</para>
            </TD>
            <TD>
              <para>(IH)</para>
            </TD>
            <TD>
              <para>--[1] C6[2] C6[3]</para>
            </TD>
            <TD>
              <para>--</para>
            </TD>
          </tr>
        </tbody>
      </table>
      <para>[1]   The connection was in auto-commit mode, and the statement executed was not a <legacyItalic>cursor</legacyItalic> <legacyItalic>specification</legacyItalic> (such as a SELECT statement); or the connection was in manual-commit mode, and the statement executed did not begin a transaction.</para>
      <para>[2]   The connection was in auto-commit mode, and the statement executed was a <legacyItalic>cursor</legacyItalic> <legacyItalic>specification</legacyItalic> (such as a SELECT statement). </para>
      <para>[3]   The connection was in manual-commit mode, and the data source began a transaction.</para>
    </content>
  </section>
  <section>
    <title>SQLFreeHandle</title>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>C0 </para>
              <para>No Env.</para>
            </TD>
            <TD>
              <para>C1</para>
              <para>Unallocated</para>
            </TD>
            <TD>
              <para>C2</para>
              <para>Allocated</para>
            </TD>
            <TD>
              <para>C3</para>
              <para>Need Data</para>
            </TD>
            <TD>
              <para>C4</para>
              <para>Connected</para>
            </TD>
            <TD>
              <para>C5</para>
              <para>Statement</para>
            </TD>
            <TD>
              <para>C6</para>
              <para>Transaction</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>(IH)[1]</para>
            </TD>
            <TD>
              <para>C0</para>
            </TD>
            <TD>
              <para>(HY010)</para>
            </TD>
            <TD>
              <para>(HY010)</para>
            </TD>
            <TD>
              <para>(HY010)</para>
            </TD>
            <TD>
              <para>(HY010)</para>
            </TD>
            <TD>
              <para>(HY010)</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>(IH)[2]</para>
            </TD>
            <TD>
              <para>(IH)</para>
            </TD>
            <TD>
              <para>(C1)</para>
            </TD>
            <TD>
              <para>(HY010)</para>
            </TD>
            <TD>
              <para>(HY010)</para>
            </TD>
            <TD>
              <para>(HY010)</para>
            </TD>
            <TD>
              <para>(HY010)</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>(IH)[3]</para>
            </TD>
            <TD>
              <para>(IH)</para>
            </TD>
            <TD>
              <para>(IH)</para>
            </TD>
            <TD>
              <para>(IH)</para>
            </TD>
            <TD>
              <para>(IH)</para>
            </TD>
            <TD>
              <para>C4[5] --[6]</para>
            </TD>
            <TD>
              <para>--[7] C4[5] and [8] C5[6] and [8]</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>(IH)[4]</para>
            </TD>
            <TD>
              <para>(IH)</para>
            </TD>
            <TD>
              <para>(IH)</para>
            </TD>
            <TD>
              <para>(IH)</para>
            </TD>
            <TD>
              <para>--</para>
            </TD>
            <TD>
              <para>--</para>
            </TD>
            <TD>
              <para>--</para>
            </TD>
          </tr>
        </tbody>
      </table>
      <para>[1]   This row shows transitions when <legacyItalic>HandleType</legacyItalic> was SQL_HANDLE_ENV.</para>
      <para>[2]   This row shows transitions when <legacyItalic>HandleType</legacyItalic> was SQL_HANDLE_DBC.</para>
      <para>[3]   This row shows transitions when <legacyItalic>HandleType</legacyItalic> was SQL_HANDLE_STMT.</para>
      <para>[4]   This row shows transitions when <legacyItalic>HandleType</legacyItalic> was SQL_HANDLE_DESC.</para>
      <para>[5]   There was only one statement allocated on the connection.</para>
      <para>[6]   There were multiple statements allocated on the connection.</para>
      <para>[7]   The connection was in manual-commit mode.</para>
      <para>[8]   The connection was in auto-commit mode.</para>
    </content>
  </section>
  <section>
    <title>SQLFreeStmt</title>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>C0 </para>
              <para>No Env.</para>
            </TD>
            <TD>
              <para>C1</para>
              <para>Unallocated</para>
            </TD>
            <TD>
              <para>C2</para>
              <para>Allocated</para>
            </TD>
            <TD>
              <para>C3</para>
              <para>Need Data</para>
            </TD>
            <TD>
              <para>C4</para>
              <para>Connected</para>
            </TD>
            <TD>
              <para>C5</para>
              <para>Statement</para>
            </TD>
            <TD>
              <para>C6</para>
              <para>Transaction</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>(IH)[1]</para>
            </TD>
            <TD>
              <para>(IH)</para>
            </TD>
            <TD>
              <para>(IH)</para>
            </TD>
            <TD>
              <para>(IH)</para>
            </TD>
            <TD>
              <para>(IH)</para>
            </TD>
            <TD>
              <para>--</para>
            </TD>
            <TD>
              <para>C5[3] --[4]</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>(IH)[2]</para>
            </TD>
            <TD>
              <para>(IH)</para>
            </TD>
            <TD>
              <para>(IH)</para>
            </TD>
            <TD>
              <para>(IH)</para>
            </TD>
            <TD>
              <para>(IH)</para>
            </TD>
            <TD>
              <para>--</para>
            </TD>
            <TD>
              <para>--</para>
            </TD>
          </tr>
        </tbody>
      </table>
      <para>[1]   This row shows transactions when the <legacyItalic>Option</legacyItalic> argument is SQL_CLOSE. </para>
      <para>[2]   This row shows transactions when the <legacyItalic>Option</legacyItalic> argument is SQL_UNBIND or SQL_RESET_PARAMS.</para>
      <para>[3]   The connection was in auto-commit mode, and no cursors were open on any statements except this one.</para>
      <para>[4]   The connection was in manual-commit mode, or it was in auto-commit mode and a cursor was open on at least one other statement.</para>
    </content>
  </section>
  <section>
    <title>SQLGetConnectAttr</title>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>C0 </para>
              <para>No Env.</para>
            </TD>
            <TD>
              <para>C1</para>
              <para>Unallocated</para>
            </TD>
            <TD>
              <para>C2</para>
              <para>Allocated</para>
            </TD>
            <TD>
              <para>C3</para>
              <para>Need Data</para>
            </TD>
            <TD>
              <para>C4</para>
              <para>Connected</para>
            </TD>
            <TD>
              <para>C5</para>
              <para>Statement</para>
            </TD>
            <TD>
              <para>C6</para>
              <para>Transaction</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>(IH)</para>
            </TD>
            <TD>
              <para>(IH)</para>
            </TD>
            <TD>
              <para>--[1] (08003)[2]</para>
            </TD>
            <TD>
              <para>(HY010)</para>
            </TD>
            <TD>
              <para>--</para>
            </TD>
            <TD>
              <para>--</para>
            </TD>
            <TD>
              <para>--</para>
            </TD>
          </tr>
        </tbody>
      </table>
      <para>[1]   The <legacyItalic>Attribute</legacyItalic> argument was SQL_ATTR_ACCESS_MODE, SQL_ATTR_AUTOCOMMIT, SQL_ATTR_LOGIN_TIMEOUT, SQL_ATTR_ODBC_CURSORS, SQL_ATTR_TRACE, or SQL_ATTR_TRACEFILE, or a value had been set for the connection attribute.</para>
      <para>[2]   The <legacyItalic>Attribute</legacyItalic> argument was not SQL_ATTR_ACCESS_MODE, SQL_ATTR_AUTOCOMMIT, SQL_ATTR_LOGIN_TIMEOUT, SQL_ATTR_ODBC_CURSORS, SQL_ATTR_TRACE, or SQL_ATTR_TRACEFILE, and a value had not been set for the connection attribute.</para>
    </content>
  </section>
  <section>
    <title>SQLGetDiagField and SQLGetDiagRec</title>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>C0 </para>
              <para>No Env.</para>
            </TD>
            <TD>
              <para>C1</para>
              <para>Unallocated</para>
            </TD>
            <TD>
              <para>C2</para>
              <para>Allocated</para>
            </TD>
            <TD>
              <para>C3</para>
              <para>Need Data</para>
            </TD>
            <TD>
              <para>C4</para>
              <para>Connected</para>
            </TD>
            <TD>
              <para>C5</para>
              <para>Statement</para>
            </TD>
            <TD>
              <para>C6</para>
              <para>Transaction</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>(IH)[1]</para>
            </TD>
            <TD>
              <para>--</para>
            </TD>
            <TD>
              <para>--</para>
            </TD>
            <TD>
              <para>--</para>
            </TD>
            <TD>
              <para>--</para>
            </TD>
            <TD>
              <para>--</para>
            </TD>
            <TD>
              <para>--</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>(IH)[2]</para>
            </TD>
            <TD>
              <para>(IH)</para>
            </TD>
            <TD>
              <para>--</para>
            </TD>
            <TD>
              <para>--</para>
            </TD>
            <TD>
              <para>--</para>
            </TD>
            <TD>
              <para>--</para>
            </TD>
            <TD>
              <para>--</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>(IH)[3]</para>
            </TD>
            <TD>
              <para>(IH)</para>
            </TD>
            <TD>
              <para>(IH)</para>
            </TD>
            <TD>
              <para>(IH)</para>
            </TD>
            <TD>
              <para>(IH)</para>
            </TD>
            <TD>
              <para>--</para>
            </TD>
            <TD>
              <para>--</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>(IH)[4]</para>
            </TD>
            <TD>
              <para>(IH)</para>
            </TD>
            <TD>
              <para>(IH)</para>
            </TD>
            <TD>
              <para>(IH)</para>
            </TD>
            <TD>
              <para>--</para>
            </TD>
            <TD>
              <para>--</para>
            </TD>
            <TD>
              <para>--</para>
            </TD>
          </tr>
        </tbody>
      </table>
      <para>[1]   This row shows transitions when <legacyItalic>HandleType</legacyItalic> was SQL_HANDLE_ENV.</para>
      <para>[2]   This row shows transitions when <legacyItalic>HandleType</legacyItalic> was SQL_HANDLE_DBC.</para>
      <para>[3]   This row shows transitions when <legacyItalic>HandleType</legacyItalic> was SQL_HANDLE_STMT.</para>
      <para>[4]   This row shows transitions when <legacyItalic>HandleType</legacyItalic> was SQL_HANDLE_DESC.</para>
    </content>
  </section>
  <section>
    <title>SQLGetEnvAttr</title>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>C0 </para>
              <para>No Env.</para>
            </TD>
            <TD>
              <para>C1</para>
              <para>Unallocated</para>
            </TD>
            <TD>
              <para>C2</para>
              <para>Allocated</para>
            </TD>
            <TD>
              <para>C3</para>
              <para>Need Data</para>
            </TD>
            <TD>
              <para>C4</para>
              <para>Connected</para>
            </TD>
            <TD>
              <para>C5</para>
              <para>Statement</para>
            </TD>
            <TD>
              <para>C6</para>
              <para>Transaction</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>(IH)</para>
            </TD>
            <TD>
              <para>--</para>
            </TD>
            <TD>
              <para>--</para>
            </TD>
            <TD>
              <para>--</para>
            </TD>
            <TD>
              <para>--</para>
            </TD>
            <TD>
              <para>--</para>
            </TD>
            <TD>
              <para>--</para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <section>
    <title>SQLGetFunctions</title>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>C0 </para>
              <para>No Env.</para>
            </TD>
            <TD>
              <para>C1</para>
              <para>Unallocated</para>
            </TD>
            <TD>
              <para>C2</para>
              <para>Allocated</para>
            </TD>
            <TD>
              <para>C3</para>
              <para>Need Data</para>
            </TD>
            <TD>
              <para>C4</para>
              <para>Connected</para>
            </TD>
            <TD>
              <para>C5</para>
              <para>Statement</para>
            </TD>
            <TD>
              <para>C6</para>
              <para>Transaction</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>(IH)</para>
            </TD>
            <TD>
              <para>(IH)</para>
            </TD>
            <TD>
              <para>(HY010)</para>
            </TD>
            <TD>
              <para>(HY010)</para>
            </TD>
            <TD>
              <para>--</para>
            </TD>
            <TD>
              <para>--</para>
            </TD>
            <TD>
              <para>--</para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <section>
    <title>SQLGetInfo</title>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>C0 </para>
              <para>No Env.</para>
            </TD>
            <TD>
              <para>C1</para>
              <para>Unallocated</para>
            </TD>
            <TD>
              <para>C2</para>
              <para>Allocated</para>
            </TD>
            <TD>
              <para>C3</para>
              <para>Need Data</para>
            </TD>
            <TD>
              <para>C4</para>
              <para>Connected</para>
            </TD>
            <TD>
              <para>C5</para>
              <para>Statement</para>
            </TD>
            <TD>
              <para>C6</para>
              <para>Transaction</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>(IH)</para>
            </TD>
            <TD>
              <para>(IH)</para>
            </TD>
            <TD>
              <para>--[1] (08003)[2]</para>
            </TD>
            <TD>
              <para>(08003)</para>
            </TD>
            <TD>
              <para>--</para>
            </TD>
            <TD>
              <para>--</para>
            </TD>
            <TD>
              <para>--</para>
            </TD>
          </tr>
        </tbody>
      </table>
      <para>[1]   The <legacyItalic>InfoType</legacyItalic> argument was SQL_ODBC_VER.</para>
      <para>[2]   The <legacyItalic>InfoType</legacyItalic> argument was not SQL_ODBC_VER.</para>
    </content>
  </section>
  <section>
    <title>SQLMoreResults</title>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>C0 </para>
              <para>No Env.</para>
            </TD>
            <TD>
              <para>C1</para>
              <para>Unallocated</para>
            </TD>
            <TD>
              <para>C2</para>
              <para>Allocated</para>
            </TD>
            <TD>
              <para>C3</para>
              <para>Need Data</para>
            </TD>
            <TD>
              <para>C4</para>
              <para>Connected</para>
            </TD>
            <TD>
              <para>C5</para>
              <para>Statement</para>
            </TD>
            <TD>
              <para>C6</para>
              <para>Transaction</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>(IH)</para>
            </TD>
            <TD>
              <para>(IH)</para>
            </TD>
            <TD>
              <para>(IH)</para>
            </TD>
            <TD>
              <para>(IH)</para>
            </TD>
            <TD>
              <para>(IH)</para>
            </TD>
            <TD>
              <para>--[1] C6[2]</para>
            </TD>
            <TD>
              <para>--[3] C5[1]</para>
            </TD>
          </tr>
        </tbody>
      </table>
      <para>[1]   The connection was in auto-commit mode, and the call to <legacyBold>SQLMoreResults</legacyBold> has not initialized the processing of a result set of a cursor specification.</para>
      <para>[2]   The connection was in auto-commit mode, and the call to <legacyBold>SQLMoreResults</legacyBold> has initialized the processing of a result set of a cursor specification.</para>
      <para>[3]   The connection was in manual-commit mode.</para>
    </content>
  </section>
  <section>
    <title>SQLNativeSql</title>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>C0 </para>
              <para>No Env.</para>
            </TD>
            <TD>
              <para>C1</para>
              <para>Unallocated</para>
            </TD>
            <TD>
              <para>C2</para>
              <para>Allocated</para>
            </TD>
            <TD>
              <para>C3</para>
              <para>Need Data</para>
            </TD>
            <TD>
              <para>C4</para>
              <para>Connected</para>
            </TD>
            <TD>
              <para>C5</para>
              <para>Statement</para>
            </TD>
            <TD>
              <para>C6</para>
              <para>Transaction</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>(IH)</para>
            </TD>
            <TD>
              <para>(IH)</para>
            </TD>
            <TD>
              <para>(08003)</para>
            </TD>
            <TD>
              <para>(08003)</para>
            </TD>
            <TD>
              <para>--</para>
            </TD>
            <TD>
              <para>--</para>
            </TD>
            <TD>
              <para>--</para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <section>
    <title>SQLPrepare</title>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>C0 </para>
              <para>No Env.</para>
            </TD>
            <TD>
              <para>C1</para>
              <para>Unallocated</para>
            </TD>
            <TD>
              <para>C2</para>
              <para>Allocated</para>
            </TD>
            <TD>
              <para>C3</para>
              <para>Need Data</para>
            </TD>
            <TD>
              <para>C4</para>
              <para>Connected</para>
            </TD>
            <TD>
              <para>C5</para>
              <para>Statement</para>
            </TD>
            <TD>
              <para>C6</para>
              <para>Transaction</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>(IH)</para>
            </TD>
            <TD>
              <para>(IH)</para>
            </TD>
            <TD>
              <para>(IH)</para>
            </TD>
            <TD>
              <para>(IH)</para>
            </TD>
            <TD>
              <para>(IH)</para>
            </TD>
            <TD>
              <para>--[1] C6[2]</para>
            </TD>
            <TD>
              <para>--</para>
            </TD>
          </tr>
        </tbody>
      </table>
      <para>[1]   The connection was in auto-commit mode, or the data source did not begin a transaction.</para>
      <para>[2]   The connection was in manual–commit mode, and the data source began a transaction.</para>
    </content>
  </section>
  <section>
    <title>SQLSetConnectAttr</title>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>C0 </para>
              <para>No Env.</para>
            </TD>
            <TD>
              <para>C1</para>
              <para>Unallocated</para>
            </TD>
            <TD>
              <para>C2</para>
              <para>Allocated</para>
            </TD>
            <TD>
              <para>C3</para>
              <para>Need Data</para>
            </TD>
            <TD>
              <para>C4</para>
              <para>Connected</para>
            </TD>
            <TD>
              <para>C5</para>
              <para>Statement</para>
            </TD>
            <TD>
              <para>C6</para>
              <para>Transaction</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>(IH)</para>
            </TD>
            <TD>
              <para>(IH)</para>
            </TD>
            <TD>
              <para>--[1] (08003)[2]</para>
            </TD>
            <TD>
              <para>(HY010)</para>
            </TD>
            <TD>
              <para>--[3] (08002)[4] HY011[5]</para>
            </TD>
            <TD>
              <para>--[3] (08002)[4] HY011[5]</para>
            </TD>
            <TD>
              <para>--[3] and [6] C5[8] (08002)[4] HY011[5] or [7]</para>
            </TD>
          </tr>
        </tbody>
      </table>
      <para>[1]   The <legacyItalic>Attribute</legacyItalic> argument was not SQL_ATTR_TRANSLATE_LIB or SQL_ATTR_TRANSLATE_OPTION.</para>
      <para>[2]   The <legacyItalic>Attribute</legacyItalic> argument was SQL_ATTR_TRANSLATE_LIB or SQL_ATTR_TRANSLATE_OPTION.</para>
      <para>[3]   The <legacyItalic>Attribute</legacyItalic> argument was not SQL_ATTR_ODBC_CURSORS or SQL_ATTR_PACKET_SIZE.</para>
      <para>[4]   The <legacyItalic>Attribute</legacyItalic> argument was SQL_ATTR_ODBC_CURSORS.</para>
      <para>[5]   The <legacyItalic>Attribute</legacyItalic> argument was SQL_ATTR_PACKET_SIZE.</para>
      <para>[6]   The <legacyItalic>Attribute</legacyItalic> argument was not SQL_ATTR_AUTOCOMMIT, or the <legacyItalic>Attribute</legacyItalic> argument was SQL_ATTR_AUTOCOMMIT and setting this attribute did not commit the transaction.</para>
      <para>[7]   The <legacyItalic>Attribute</legacyItalic> argument was SQL_ATTR_TXN_ISOLATION.</para>
      <para>[8]   The <legacyItalic>Attribute</legacyItalic> argument was SQL_ATTR_AUTOCOMMIT, and setting this attribute committed the transaction.</para>
    </content>
  </section>
  <section>
    <title>SQLSetEnvAttr</title>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>C0 </para>
              <para>No Env.</para>
            </TD>
            <TD>
              <para>C1</para>
              <para>Unallocated</para>
            </TD>
            <TD>
              <para>C2</para>
              <para>Allocated</para>
            </TD>
            <TD>
              <para>C3</para>
              <para>Need Data</para>
            </TD>
            <TD>
              <para>C4</para>
              <para>Connected</para>
            </TD>
            <TD>
              <para>C5</para>
              <para>Statement</para>
            </TD>
            <TD>
              <para>C6</para>
              <para>Transaction</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>(IH)</para>
            </TD>
            <TD>
              <para>--</para>
            </TD>
            <TD>
              <para>--</para>
            </TD>
            <TD>
              <para>(HY010)</para>
            </TD>
            <TD>
              <para>--</para>
            </TD>
            <TD>
              <para>--</para>
            </TD>
            <TD>
              <para>--</para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <section>
    <title>All Other ODBC Functions</title>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>C0 </para>
              <para>No Env.</para>
            </TD>
            <TD>
              <para>C1</para>
              <para>Unallocated</para>
            </TD>
            <TD>
              <para>C2</para>
              <para>Allocated</para>
            </TD>
            <TD>
              <para>C3</para>
              <para>Need Data</para>
            </TD>
            <TD>
              <para>C4</para>
              <para>Connected</para>
            </TD>
            <TD>
              <para>C5</para>
              <para>Statement</para>
            </TD>
            <TD>
              <para>C6</para>
              <para>Transaction</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>(IH)</para>
            </TD>
            <TD>
              <para>(IH)</para>
            </TD>
            <TD>
              <para>(IH)</para>
            </TD>
            <TD>
              <para>(IH)</para>
            </TD>
            <TD>
              <para>(IH)</para>
            </TD>
            <TD>
              <para>--</para>
            </TD>
            <TD>
              <para>--</para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>