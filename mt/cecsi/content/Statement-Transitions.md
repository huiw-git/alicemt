---
title: Statement Transitions
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3d70e0e3-fe83-4b4d-beac-42c82495a05b
translation.priority.ht: 
  - en-gb
---
# Statement Transitions
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>ODBC statements have the following states.</para>
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
            <para>S0</para>
          </TD>
          <TD>
            <para>Unallocated statement. (The connection state must be C4, C5, or C6. For more information, see <legacyLink xlink:href="6b6e1a47-4a52-41c8-bb9e-7ddeae09913e">Connection Transitions</legacyLink>.)</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>S1</para>
          </TD>
          <TD>
            <para>Allocated statement.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>S2</para>
          </TD>
          <TD>
            <para>Prepared statement. No result set will be created.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>S3</para>
          </TD>
          <TD>
            <para>Prepared statement. A (possibly empty) result set will be created.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>S4</para>
          </TD>
          <TD>
            <para>Statement executed and no result set was created.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>S5</para>
          </TD>
          <TD>
            <para>Statement executed and a (possibly empty) result set was created. The cursor is open and positioned before the first row of the result set.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>S6</para>
          </TD>
          <TD>
            <para>Cursor positioned with <legacyBold>SQLFetch</legacyBold> or <legacyBold>SQLFetchScroll</legacyBold>.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>S7</para>
          </TD>
          <TD>
            <para>Cursor positioned with <legacyBold>SQLExtendedFetch</legacyBold>.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>S8</para>
          </TD>
          <TD>
            <para>Function needs data. <legacyBold>SQLParamData</legacyBold> has not been called.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>S9</para>
          </TD>
          <TD>
            <para>Function needs data. <legacyBold>SQLPutData</legacyBold> has not been called.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>S10</para>
          </TD>
          <TD>
            <para>Function needs data. <legacyBold>SQLPutData</legacyBold> has been called.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>S11</para>
          </TD>
          <TD>
            <para>Still executing. A statement is left in this state after a function that is executed asynchronously returns SQL_STILL_EXECUTING. A statement is temporarily in this state while any function that accepts a statement handle is executing. Temporary residence in state S11 is not shown in any state tables except the state table for <legacyBold>SQLCancel</legacyBold>. While a statement is temporarily in state S11, the function can be canceled by calling <legacyBold>SQLCancel</legacyBold> from another thread.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>S12</para>
          </TD>
          <TD>
            <para>Asynchronous execution canceled. In S12, an application must call the canceled function until it returns a value other than SQL_STILL_EXECUTING. The function was canceled successfully only if the function returns SQL_ERROR and SQLSTATE HY008 (Operation canceled). If it returns any other value, such as SQL_SUCCESS, the cancel operation failed and the function executed normally.</para>
          </TD>
        </tr>
      </tbody>
    </table>
    <para>States S2 and S3 are known as the prepared states, states S5 through S7 as the cursor states, states S8 through S10 as the need data states, and states S11 and S12 as the asynchronous states. In each of these groups, the transitions are shown separately only when they are different for each state in the group; in most cases, the transitions for each state in each a group are the same.</para>
    <para>The following tables show how each ODBC function affects the statement state.</para>
  </introduction>
  <section>
    <title>SQLAllocHandle</title>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>S0 </para>
              <para>Unallocated</para>
            </TD>
            <TD>
              <para>S1</para>
              <para>Allocated</para>
            </TD>
            <TD>
              <para>S2–S3</para>
              <para>Prepared</para>
            </TD>
            <TD>
              <para>S4</para>
              <para>Executed</para>
            </TD>
            <TD>
              <para>S5–S7</para>
              <para>Cursor</para>
            </TD>
            <TD>
              <para>S8–S10</para>
              <para>Need Data</para>
            </TD>
            <TD>
              <para>S11–S12</para>
              <para>Async</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>--[1], [5], [6]</para>
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
              <para>--[2], [5]</para>
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
              <para>S1[3]</para>
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
              <para>--[4], [5]</para>
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
        </tbody>
      </table>
      <para>[1]   This row shows transitions when <legacyItalic>HandleType</legacyItalic> was SQL_HANDLE_ENV.</para>
      <para>[2]   This row shows transitions when <legacyItalic>HandleType</legacyItalic> was SQL_HANDLE_DBC.</para>
      <para>[3]   This row shows transitions when <legacyItalic>HandleType</legacyItalic> was SQL_HANDLE_STMT.</para>
      <para>[4]   This row shows transitions when <legacyItalic>HandleType</legacyItalic> was SQL_HANDLE_DESC.</para>
      <para>[5]   Calling <legacyBold>SQLAllocHandle</legacyBold> with <legacyItalic>OutputHandlePtr</legacyItalic> pointing to a valid handle overwrites that handle without regard for the previous contents to that handle and might cause problems for ODBC drivers. It is incorrect ODBC application programming to call <legacyBold>SQLAllocHandle</legacyBold> twice with the same application variable defined for <legacyItalic>*OutputHandlePtr</legacyItalic> without calling <legacyBold>SQLFreeHandle</legacyBold> to free the handle before reallocating it. Overwriting ODBC handles in such a manner might lead to inconsistent behavior or errors on the part of ODBC drivers.</para>
    </content>
  </section>
  <section>
    <title>SQLBindCol</title>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>S0 </para>
              <para>Unallocated</para>
            </TD>
            <TD>
              <para>S1</para>
              <para>Allocated</para>
            </TD>
            <TD>
              <para>S2–S3</para>
              <para>Prepared</para>
            </TD>
            <TD>
              <para>S4</para>
              <para>Executed</para>
            </TD>
            <TD>
              <para>S5–S7</para>
              <para>Cursor</para>
            </TD>
            <TD>
              <para>S8–S10</para>
              <para>Need Data</para>
            </TD>
            <TD>
              <para>S11–S12</para>
              <para>Async</para>
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
              <para>(HY010)</para>
            </TD>
            <TD>
              <para>(HY010)</para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <section>
    <title>SQLBindParameter</title>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>S0 </para>
              <para>Unallocated</para>
            </TD>
            <TD>
              <para>S1</para>
              <para>Allocated</para>
            </TD>
            <TD>
              <para>S2–S3</para>
              <para>Prepared</para>
            </TD>
            <TD>
              <para>S4</para>
              <para>Executed</para>
            </TD>
            <TD>
              <para>S5–S7</para>
              <para>Cursor</para>
            </TD>
            <TD>
              <para>S8–S10</para>
              <para>Need Data</para>
            </TD>
            <TD>
              <para>S11–S12</para>
              <para>Async</para>
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
              <para>(HY010)</para>
            </TD>
            <TD>
              <para>(HY010)</para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <section>
    <title>SQLBrowseConnect, SQLConnect, and SQLDriverConnect</title>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>S0 </para>
              <para>Unallocated</para>
            </TD>
            <TD>
              <para>S1</para>
              <para>Allocated</para>
            </TD>
            <TD>
              <para>S2–S3</para>
              <para>Prepared</para>
            </TD>
            <TD>
              <para>S4</para>
              <para>Executed</para>
            </TD>
            <TD>
              <para>S5–S7</para>
              <para>Cursor</para>
            </TD>
            <TD>
              <para>S8–S10</para>
              <para>Need Data</para>
            </TD>
            <TD>
              <para>S11–S12</para>
              <para>Async</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
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
    <title>SQLBulkOperations</title>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>S0 </para>
              <para>Unallocated</para>
            </TD>
            <TD>
              <para>S1</para>
              <para>Allocated</para>
            </TD>
            <TD>
              <para>S2–S3</para>
              <para>Prepared</para>
            </TD>
            <TD>
              <para>S4</para>
              <para>Executed</para>
            </TD>
            <TD>
              <para>S5–S7</para>
              <para>Cursor</para>
            </TD>
            <TD>
              <para>S8–S10</para>
              <para>Need Data</para>
            </TD>
            <TD>
              <para>S11–S12</para>
              <para>Async</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
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
              <para>24000</para>
            </TD>
            <TD>
              <para>See next table</para>
            </TD>
            <TD>
              <para>(HY010)</para>
            </TD>
            <TD>
              <para>NS [c] (HY010) o</para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <section>
    <title>SQLBulkOperations (Cursor States)</title>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>S5</para>
              <para>Opened</para>
            </TD>
            <TD>
              <para>S6</para>
              <para>SQLFetch or SQLFetchScroll</para>
            </TD>
            <TD>
              <para>S7</para>
              <para>SQLExtendedFetch</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>-- [s] S8 [d] S11 [x]</para>
            </TD>
            <TD>
              <para>-- [s] S8 [d] S11 [x]</para>
            </TD>
            <TD>
              <para>(HY010)</para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <section>
    <title>SQLCancel</title>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>S0 </para>
              <para>Unallocated</para>
            </TD>
            <TD>
              <para>S1</para>
              <para>Allocated</para>
            </TD>
            <TD>
              <para>S2–S3</para>
              <para>Prepared</para>
            </TD>
            <TD>
              <para>S4</para>
              <para>Executed</para>
            </TD>
            <TD>
              <para>S5–S7</para>
              <para>Cursor</para>
            </TD>
            <TD>
              <para>S8–S10</para>
              <para>Need Data</para>
            </TD>
            <TD>
              <para>S11–S12</para>
              <para>Async</para>
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
              <para>S1[1] S2 [nr] and [2] S3 [r]and [2] S5[3] and [5] S6([3] or [4]) and [6] S7[4] and [7]</para>
            </TD>
            <TD>
              <para>See next table</para>
            </TD>
          </tr>
        </tbody>
      </table>
      <para>[1]   <legacyBold>SQLExecDirect</legacyBold> returned SQL_NEED_DATA.</para>
      <para>[2]   <legacyBold>SQLExecute</legacyBold> returned SQL_NEED_DATA.</para>
      <para>[3]   <legacyBold>SQLBulkOperations</legacyBold> returned SQL_NEED_DATA.</para>
      <para>[4]   <legacyBold>SQLSetPos</legacyBold> returned SQL_NEED_DATA.</para>
      <para>[5]   <legacyBold>SQLFetch</legacyBold>, <legacyBold>SQLFetchScroll</legacyBold>, or <legacyBold>SQLExtendedFetch</legacyBold> had not been called.</para>
      <para>[6]   <legacyBold>SQLFetch</legacyBold> or <legacyBold>SQLFetchScroll</legacyBold> had been called.</para>
      <para>[7]   <legacyBold>SQLExtendedFetch</legacyBold> had been called.</para>
    </content>
  </section>
  <section>
    <title>SQLCancel (Asynchronous States)</title>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>S11 </para>
              <para>Still executing</para>
            </TD>
            <TD>
              <para>S12</para>
              <para>Asynch canceled</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>NS[1] S12[2]</para>
            </TD>
            <TD>
              <para>S12</para>
            </TD>
          </tr>
        </tbody>
      </table>
      <para>[1]   The statement was temporarily in state S11 while a function was executing. <legacyBold>SQLCancel</legacyBold> was called from a different thread.</para>
      <para>[2]   The statement was in state S11 because a function called asynchronously returned SQL_STILL_EXECUTING.</para>
    </content>
  </section>
  <section>
    <title>SQLCloseCursor</title>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>S0 </para>
              <para>Unallocated</para>
            </TD>
            <TD>
              <para>S1</para>
              <para>Allocated</para>
            </TD>
            <TD>
              <para>S2–S3</para>
              <para>Prepared</para>
            </TD>
            <TD>
              <para>S4</para>
              <para>Executed</para>
            </TD>
            <TD>
              <para>S5–S7</para>
              <para>Cursor</para>
            </TD>
            <TD>
              <para>S8–S10</para>
              <para>Need Data</para>
            </TD>
            <TD>
              <para>S11–S12</para>
              <para>Async</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>(IH)</para>
            </TD>
            <TD>
              <para>24000</para>
            </TD>
            <TD>
              <para>24000</para>
            </TD>
            <TD>
              <para>24000</para>
            </TD>
            <TD>
              <para>S1 [np] S3 [p]</para>
            </TD>
            <TD>
              <para>(HY010)</para>
            </TD>
            <TD>
              <para>(HY010)</para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <section>
    <title>SQLColAttribute</title>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>S0 </para>
              <para>Unallocated</para>
            </TD>
            <TD>
              <para>S1</para>
              <para>Allocated</para>
            </TD>
            <TD>
              <para>S2–S3</para>
              <para>Prepared</para>
            </TD>
            <TD>
              <para>S4</para>
              <para>Executed</para>
            </TD>
            <TD>
              <para>S5–S7</para>
              <para>Cursor</para>
            </TD>
            <TD>
              <para>S8–S10</para>
              <para>Need Data</para>
            </TD>
            <TD>
              <para>S11–S12</para>
              <para>Async</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>(IH)</para>
            </TD>
            <TD>
              <para>(HY010)</para>
            </TD>
            <TD>
              <para>See next table</para>
            </TD>
            <TD>
              <para>24000</para>
            </TD>
            <TD>
              <para>-- [s] S11 [x]</para>
            </TD>
            <TD>
              <para>(HY010)</para>
            </TD>
            <TD>
              <para>NS [c] (HY010) o</para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <section>
    <title>SQLColAttribute (Prepared States)</title>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>S2 </para>
              <para>No Results</para>
            </TD>
            <TD>
              <para>S3</para>
              <para>Results</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>--[1] 07005[2]</para>
            </TD>
            <TD>
              <para>-- [s] S11 x </para>
            </TD>
          </tr>
        </tbody>
      </table>
      <para>[1]   <legacyItalic>FieldIdentifier</legacyItalic> was SQL_DESC_COUNT.</para>
      <para>[2]   <legacyItalic>FieldIdentifier</legacyItalic> was not SQL_DESC_COUNT.</para>
    </content>
  </section>
  <section>
    <title>SQLColumnPrivileges, SQLColumns, SQLForeignKeys, SQLGetTypeInfo, SQLPrimaryKeys, SQLProcedureColumns, SQLProcedures, SQLSpecialColumns, SQLStatistics, SQLTablePrivileges, and SQLTables</title>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>S0 </para>
              <para>Unallocated</para>
            </TD>
            <TD>
              <para>S1</para>
              <para>Allocated</para>
            </TD>
            <TD>
              <para>S2–S3</para>
              <para>Prepared</para>
            </TD>
            <TD>
              <para>S4</para>
              <para>Executed</para>
            </TD>
            <TD>
              <para>S5–S7</para>
              <para>Cursor</para>
            </TD>
            <TD>
              <para>S8–S10</para>
              <para>Need Data</para>
            </TD>
            <TD>
              <para>S11–S12</para>
              <para>Async</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>(IH)</para>
            </TD>
            <TD>
              <para>S5 [s]  S11 [x]</para>
            </TD>
            <TD>
              <para>S1 [e] S5 [s]  S11 [x] </para>
            </TD>
            <TD>
              <para>S1 [e] and [1] S5 [s] and [1] S11 [x] and [1] 24000[2]</para>
            </TD>
            <TD>
              <para>See next table</para>
            </TD>
            <TD>
              <para>(HY010)</para>
            </TD>
            <TD>
              <para>NS [c] (HY010) o</para>
            </TD>
          </tr>
        </tbody>
      </table>
      <para>[1]   The current result is the last or only result, or there are no current results. For more information about multiple results, see <legacyLink xlink:href="a3c32e4b-8fe7-4a33-ae39-ae664001f315">Multiple Results</legacyLink>.</para>
      <para>[2]   The current result is not the last result.</para>
    </content>
  </section>
  <section>
    <title>SQLColumnPrivileges, SQLColumns, SQLForeignKeys, SQLGetTypeInfo, SQLPrimaryKeys, SQLProcedureColumns, SQLProcedures, SQLSpecialColumns, SQLStatistics, SQLTablePrivileges, and SQLTables (Cursor States)</title>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>S5</para>
              <para>Opened</para>
            </TD>
            <TD>
              <para>S6</para>
              <para>SQLFetch or SQLFetchScroll</para>
            </TD>
            <TD>
              <para>S7</para>
              <para>SQLExtendedFetch</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>24000</para>
            </TD>
            <TD>
              <para>(24000)[1]</para>
            </TD>
            <TD>
              <para>(24000)</para>
            </TD>
          </tr>
        </tbody>
      </table>
      <para>[1]   This error is returned by the Driver Manager if <legacyBold>SQLFetch </legacyBold>or <legacyBold>SQLFetchScroll </legacyBold>has not returned SQL_NO_DATA and is returned by the driver if <legacyBold>SQLFetch </legacyBold>or <legacyBold>SQLFetchScroll </legacyBold>has returned SQL_NO_DATA.</para>
    </content>
  </section>
  <section>
    <title>SQLCopyDesc</title>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>S0 </para>
              <para>Unallocated</para>
            </TD>
            <TD>
              <para>S1</para>
              <para>Allocated</para>
            </TD>
            <TD>
              <para>S2–S3</para>
              <para>Prepared</para>
            </TD>
            <TD>
              <para>S4</para>
              <para>Executed</para>
            </TD>
            <TD>
              <para>S5–S7</para>
              <para>Cursor</para>
            </TD>
            <TD>
              <para>S8–S10</para>
              <para>Need Data</para>
            </TD>
            <TD>
              <para>S11–S12</para>
              <para>Async</para>
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
              <para>(HY010)</para>
            </TD>
            <TD>
              <para>NS [c] and [3] (HY010) [o] or [4]</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>(IH)[2]</para>
            </TD>
            <TD>
              <para>(HY010)</para>
            </TD>
            <TD>
              <para>See next table</para>
            </TD>
            <TD>
              <para>24000</para>
            </TD>
            <TD>
              <para>-- [s]  S11 x</para>
            </TD>
            <TD>
              <para>(HY010)</para>
            </TD>
            <TD>
              <para>NS [c] and [3] (HY010) [o] or [4]</para>
            </TD>
          </tr>
        </tbody>
      </table>
      <para>[1]   This row shows transitions when the <legacyItalic>SourceDescHandle</legacyItalic> argument was an ARD, APD, or IPD.</para>
      <para>[2]   This row shows transitions when the <legacyItalic>SourceDescHandle</legacyItalic> argument was an IRD.</para>
      <para>[3]   The <legacyItalic>SourceDescHandle</legacyItalic> and <legacyItalic>TargetDescHandle</legacyItalic> arguments were the same as in the <legacyBold>SQLCopyDesc</legacyBold> function that is running asynchronously.</para>
      <para>[4]   Either the <legacyItalic>SourceDescHandle</legacyItalic> argument or the <legacyItalic>TargetDescHandle</legacyItalic> argument (or both) were different than in the <legacyBold>SQLCopyDesc</legacyBold> function that is running asynchronously.</para>
    </content>
  </section>
  <section>
    <title>SQLCopyDesc (Prepared States)</title>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>S2 </para>
              <para>No Results</para>
            </TD>
            <TD>
              <para>S3</para>
              <para>Results</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>24000[1]</para>
            </TD>
            <TD>
              <para>-- [s]  S11 [x]</para>
            </TD>
          </tr>
        </tbody>
      </table>
      <para>[1]<legacyBold>   </legacyBold>This row shows transitions when the <legacyItalic>SourceDescHandle</legacyItalic> argument was an IRD.</para>
    </content>
  </section>
  <section>
    <title>SQLDataSources and SQLDrivers</title>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>S0 </para>
              <para>Unallocated</para>
            </TD>
            <TD>
              <para>S1</para>
              <para>Allocated</para>
            </TD>
            <TD>
              <para>S2–S3</para>
              <para>Prepared</para>
            </TD>
            <TD>
              <para>S4</para>
              <para>Executed</para>
            </TD>
            <TD>
              <para>S5–S7</para>
              <para>Cursor</para>
            </TD>
            <TD>
              <para>S8–S10</para>
              <para>Need Data</para>
            </TD>
            <TD>
              <para>S11–S12</para>
              <para>Async</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
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
            <TD>
              <para>--</para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <section>
    <title>SQLDescribeCol</title>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>S0 </para>
              <para>Unallocated</para>
            </TD>
            <TD>
              <para>S1</para>
              <para>Allocated</para>
            </TD>
            <TD>
              <para>S2–S3</para>
              <para>Prepared</para>
            </TD>
            <TD>
              <para>S4</para>
              <para>Executed</para>
            </TD>
            <TD>
              <para>S5–S7</para>
              <para>Cursor</para>
            </TD>
            <TD>
              <para>S8–S10</para>
              <para>Need Data</para>
            </TD>
            <TD>
              <para>S11–S12</para>
              <para>Async</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>(IH)</para>
            </TD>
            <TD>
              <para>(HY010)</para>
            </TD>
            <TD>
              <para>See next table</para>
            </TD>
            <TD>
              <para>24000</para>
            </TD>
            <TD>
              <para>-- [s]  S11 [x] </para>
            </TD>
            <TD>
              <para>(HY010)</para>
            </TD>
            <TD>
              <para>NS [c] (HY010) o</para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <section>
    <title>SQLDescribeCol (Prepared States)</title>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>S2 </para>
              <para>No Results</para>
            </TD>
            <TD>
              <para>S3</para>
              <para>Results</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>07005</para>
            </TD>
            <TD>
              <para>-- [s]  S11 [x] </para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <section>
    <title>SQLDescribeParam</title>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>S0 </para>
              <para>Unallocated</para>
            </TD>
            <TD>
              <para>S1</para>
              <para>Allocated</para>
            </TD>
            <TD>
              <para>S2–S3</para>
              <para>Prepared</para>
            </TD>
            <TD>
              <para>S4</para>
              <para>Executed</para>
            </TD>
            <TD>
              <para>S5–S7</para>
              <para>Cursor</para>
            </TD>
            <TD>
              <para>S8–S10</para>
              <para>Need Data</para>
            </TD>
            <TD>
              <para>S11–S12</para>
              <para>Async</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>(IH)</para>
            </TD>
            <TD>
              <para>(HY010)</para>
            </TD>
            <TD>
              <para>-- [s]  S11 [x] </para>
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
              <para>NS [c] (HY010) [o]</para>
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
              <para>S0 </para>
              <para>Unallocated</para>
            </TD>
            <TD>
              <para>S1</para>
              <para>Allocated</para>
            </TD>
            <TD>
              <para>S2–S3</para>
              <para>Prepared</para>
            </TD>
            <TD>
              <para>S4</para>
              <para>Executed</para>
            </TD>
            <TD>
              <para>S5–S7</para>
              <para>Cursor</para>
            </TD>
            <TD>
              <para>S8–S10</para>
              <para>Need Data</para>
            </TD>
            <TD>
              <para>S11–S12</para>
              <para>Async</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>--[1]</para>
            </TD>
            <TD>
              <para>S0[1]</para>
            </TD>
            <TD>
              <para>S0[1]</para>
            </TD>
            <TD>
              <para>S0[1]</para>
            </TD>
            <TD>
              <para>S0[1]</para>
            </TD>
            <TD>
              <para>(HY010)</para>
            </TD>
            <TD>
              <para>(HY010)</para>
            </TD>
          </tr>
        </tbody>
      </table>
      <para>[1]   Calling <legacyBold>SQLDisconnect</legacyBold> frees all statements associated with the connection. Furthermore, this returns the connection state to C2; the connection state must be C4 before the statement state is S0.</para>
    </content>
  </section>
  <section>
    <title>SQLEndTran</title>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>S0 </para>
              <para>Unallocated</para>
            </TD>
            <TD>
              <para>S1</para>
              <para>Allocated</para>
            </TD>
            <TD>
              <para>S2–S3</para>
              <para>Prepared</para>
            </TD>
            <TD>
              <para>S4</para>
              <para>Executed</para>
            </TD>
            <TD>
              <para>S5–S7</para>
              <para>Cursor</para>
            </TD>
            <TD>
              <para>S8–S10</para>
              <para>Need Data</para>
            </TD>
            <TD>
              <para>S11–S12</para>
              <para>Async</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>--</para>
            </TD>
            <TD>
              <para>--</para>
            </TD>
            <TD>
              <para>--[2] or [3] S1[1]</para>
            </TD>
            <TD>
              <para>--[3]  S1 [np] and ([1] or [2]) S1 [p] and [1] S2 [p] and [2]</para>
            </TD>
            <TD>
              <para>--[3]  S1 [np] and ([1] or [2]) S1 [p] and [1] S3 [p] and [2]</para>
            </TD>
            <TD>
              <para>(HY010)</para>
            </TD>
            <TD>
              <para>(HY010)</para>
            </TD>
          </tr>
        </tbody>
      </table>
      <para>[1]   The <legacyItalic>CompletionType</legacyItalic> argument is SQL_COMMIT and <legacyBold>SQLGetInfo</legacyBold> returns SQL_CB_DELETE for the SQL_CURSOR_COMMIT_BEHAVIOR information type, or the <legacyItalic>CompletionType</legacyItalic> argument is SQL_ROLLBACK and <legacyBold>SQLGetInfo</legacyBold> returns SQL_CB_DELETE for the SQL_CURSOR_ROLLBACK_BEHAVIOR information type.</para>
      <para>[2]   The <legacyItalic>CompletionType</legacyItalic> argument is SQL_COMMIT and <legacyBold>SQLGetInfo</legacyBold> returns SQL_CB_CLOSE for the SQL_CURSOR_COMMIT_BEHAVIOR information type, or the <legacyItalic>CompletionType</legacyItalic> argument is SQL_ROLLBACK and <legacyBold>SQLGetInfo</legacyBold> returns SQL_CB_CLOSE for the SQL_CURSOR_ROLLBACK_BEHAVIOR information type.</para>
      <para>[3]   The <legacyItalic>CompletionType</legacyItalic> argument is SQL_COMMIT and <legacyBold>SQLGetInfo</legacyBold> returns SQL_CB_PRESERVE for the SQL_CURSOR_COMMIT_BEHAVIOR information type, or the <legacyItalic>CompletionType</legacyItalic> argument is SQL_ROLLBACK and <legacyBold>SQLGetInfo</legacyBold> returns SQL_CB_PRESERVE for the SQL_CURSOR_ROLLBACK_BEHAVIOR information type.</para>
    </content>
  </section>
  <section>
    <title>SQLExecDirect</title>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>S0 </para>
              <para>Unallocated</para>
            </TD>
            <TD>
              <para>S1</para>
              <para>Allocated</para>
            </TD>
            <TD>
              <para>S2–S3</para>
              <para>Prepared</para>
            </TD>
            <TD>
              <para>S4</para>
              <para>Executed</para>
            </TD>
            <TD>
              <para>S5–S7</para>
              <para>Cursor</para>
            </TD>
            <TD>
              <para>S8–S10</para>
              <para>Need Data</para>
            </TD>
            <TD>
              <para>S11–S12</para>
              <para>Async</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>(IH)</para>
            </TD>
            <TD>
              <para>S4 [s] and [nr] S5 [s] and [r] S8 [d]  S11 [x] </para>
            </TD>
            <TD>
              <para>-- [e] and [1] S1 [e] and [2] S4 [s] and [nr] S5 [s] and [r] S8 [d]  S11 [x] </para>
            </TD>
            <TD>
              <para>-- [e], [1], and [3] S1 [e], [2], and [3] S4 [s], [nr], and [3] S5 [s], [r], and [3] S8 [d] and [3] S11 [x] and [3] 24000 [4]</para>
            </TD>
            <TD>
              <para>See next table</para>
            </TD>
            <TD>
              <para>(HY010)</para>
            </TD>
            <TD>
              <para>NS [c] (HY010) [o]</para>
            </TD>
          </tr>
        </tbody>
      </table>
      <para>[1]   The error was returned by the Driver Manager.</para>
      <para>[2]   The error was not returned by the Driver Manager.</para>
      <para>[3]   The current result is the last or only result, or there are no current results. For more information about multiple results, see <legacyLink xlink:href="a3c32e4b-8fe7-4a33-ae39-ae664001f315">Multiple Results</legacyLink>.</para>
      <para>[4]   The current result is not the last result.</para>
    </content>
  </section>
  <section>
    <title>SQLExecDirect (Cursor States)</title>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>S5</para>
              <para>Opened</para>
            </TD>
            <TD>
              <para>S6</para>
              <para>SQLFetch or SQLFetchScroll</para>
            </TD>
            <TD>
              <para>S7</para>
              <para>SQLExtendedFetch</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>24000</para>
            </TD>
            <TD>
              <para>(24000) [1]</para>
            </TD>
            <TD>
              <para>(24000)</para>
            </TD>
          </tr>
        </tbody>
      </table>
      <para>[1]   This error is returned by the Driver Manager if <legacyBold>SQLFetch</legacyBold> or <legacyBold>SQLFetchScroll</legacyBold> has not returned SQL_NO_DATA, and is returned by the driver if <legacyBold>SQLFetch</legacyBold> or <legacyBold>SQLFetchScroll</legacyBold> has returned SQL_NO_DATA.</para>
    </content>
  </section>
  <section>
    <title>SQLExecute</title>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>S0 </para>
              <para>Unallocated</para>
            </TD>
            <TD>
              <para>S1</para>
              <para>Allocated</para>
            </TD>
            <TD>
              <para>S2–S3</para>
              <para>Prepared</para>
            </TD>
            <TD>
              <para>S4</para>
              <para>Executed</para>
            </TD>
            <TD>
              <para>S5–S7</para>
              <para>Cursor</para>
            </TD>
            <TD>
              <para>S8–S10</para>
              <para>Need Data</para>
            </TD>
            <TD>
              <para>S11–S12</para>
              <para>Async</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>(IH)</para>
            </TD>
            <TD>
              <para>(HY010)</para>
            </TD>
            <TD>
              <para>See next table</para>
            </TD>
            <TD>
              <para>S2 [e], p, and [1]  S4 [s], [p], [nr], and [1] S5 [s], [p], [r], and [1] S8 [d], [p], and [1]  S11 [x], [p], and [1] 24000 [p] and [2] (HY010) [np]</para>
            </TD>
            <TD>
              <para>See cursor states table</para>
            </TD>
            <TD>
              <para>(HY010)</para>
            </TD>
            <TD>
              <para>NS [c] (HY010) [o]</para>
            </TD>
          </tr>
        </tbody>
      </table>
      <para>[1]   The current result is the last or only result, or there are no current results. For more information about multiple results, see <legacyLink xlink:href="a3c32e4b-8fe7-4a33-ae39-ae664001f315">Multiple Results</legacyLink>.</para>
      <para>[2]   The current result is not the last result.</para>
    </content>
  </section>
  <section>
    <title>SQLExecute (Prepared States)</title>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>S2 </para>
              <para>No Results</para>
            </TD>
            <TD>
              <para>S3</para>
              <para>Results</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>S4 [s]  S8 [d]  S11 [x] </para>
            </TD>
            <TD>
              <para>S5 [s]  S8 [d]  S11 [x] </para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <section>
    <title>SQLExecute (Cursor States)</title>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>S5</para>
              <para>Opened</para>
            </TD>
            <TD>
              <para>S6</para>
              <para>SQLFetch or SQLFetchScroll</para>
            </TD>
            <TD>
              <para>S7</para>
              <para>SQLExtendedFetch</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>24000 [p]  (HY010) [np] </para>
            </TD>
            <TD>
              <para>(24000) [p], [1] (HY010) [np] </para>
            </TD>
            <TD>
              <para>(24000) [p]  (HY010) [np] </para>
            </TD>
          </tr>
        </tbody>
      </table>
      <para>[1]   This error is returned by the Driver Manager if <legacyBold>SQLFetch</legacyBold> or <legacyBold>SQLFetchScroll</legacyBold> has not returned SQL_NO_DATA, and is returned by the driver if <legacyBold>SQLFetch</legacyBold> or <legacyBold>SQLFetchScroll</legacyBold> has returned SQL_NO_DATA.</para>
    </content>
  </section>
  <section>
    <title>SQLExtendedFetch</title>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>S0 </para>
              <para>Unallocated</para>
            </TD>
            <TD>
              <para>S1</para>
              <para>Allocated</para>
            </TD>
            <TD>
              <para>S2–S3</para>
              <para>Prepared</para>
            </TD>
            <TD>
              <para>S4</para>
              <para>Executed</para>
            </TD>
            <TD>
              <para>S5–S7</para>
              <para>Cursor</para>
            </TD>
            <TD>
              <para>S8–S10</para>
              <para>Need Data</para>
            </TD>
            <TD>
              <para>S11–S12</para>
              <para>Async</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>(IH)</para>
            </TD>
            <TD>
              <para>(S1010)</para>
            </TD>
            <TD>
              <para>(S1010)</para>
            </TD>
            <TD>
              <para>24000</para>
            </TD>
            <TD>
              <para>See next table</para>
            </TD>
            <TD>
              <para>(S1010)</para>
            </TD>
            <TD>
              <para>NS [c] (S1010) [o]</para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <section>
    <title>SQLExtendedFetch (Cursor States)</title>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>S5</para>
              <para>Opened</para>
            </TD>
            <TD>
              <para>S6</para>
              <para>SQLFetch or SQLFetchScroll</para>
            </TD>
            <TD>
              <para>S7</para>
              <para>SQLExtendedFetch</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>S7 [s] or [nf]  S11 [x] </para>
            </TD>
            <TD>
              <para>(S1010)</para>
            </TD>
            <TD>
              <para>-- [s] or [nf]  S11 [x] </para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <section>
    <title>SQLFetch and SQLFetchScroll</title>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>S0 </para>
              <para>Unallocated</para>
            </TD>
            <TD>
              <para>S1</para>
              <para>Allocated</para>
            </TD>
            <TD>
              <para>S2–S3</para>
              <para>Prepared</para>
            </TD>
            <TD>
              <para>S4</para>
              <para>Executed</para>
            </TD>
            <TD>
              <para>S5–S7</para>
              <para>Cursor</para>
            </TD>
            <TD>
              <para>S8–S10</para>
              <para>Need Data</para>
            </TD>
            <TD>
              <para>S11–S12</para>
              <para>Async</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
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
              <para>24000</para>
            </TD>
            <TD>
              <para>See next table</para>
            </TD>
            <TD>
              <para>(HY010)</para>
            </TD>
            <TD>
              <para>NS [c] (HY010) [o]</para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <section>
    <title>SQLFetch and SQLFetchScroll (Cursor states)</title>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>S5</para>
              <para>Opened</para>
            </TD>
            <TD>
              <para>S6</para>
              <para>SQLFetch or SQLFetchScroll</para>
            </TD>
            <TD>
              <para>S7</para>
              <para>SQLExtendedFetch</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>S6 [s] or [nf]  S11 [x] </para>
            </TD>
            <TD>
              <para>-- [s] or [nf]  S11 [x] </para>
            </TD>
            <TD>
              <para>(HY010)</para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <section>
    <title>SQLFreeHandle</title>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>S0 </para>
              <para>Unallocated</para>
            </TD>
            <TD>
              <para>S1</para>
              <para>Allocated</para>
            </TD>
            <TD>
              <para>S2–S3</para>
              <para>Prepared</para>
            </TD>
            <TD>
              <para>S4</para>
              <para>Executed</para>
            </TD>
            <TD>
              <para>S5–S7</para>
              <para>Cursor</para>
            </TD>
            <TD>
              <para>S8–S10</para>
              <para>Need Data</para>
            </TD>
            <TD>
              <para>S11–S12</para>
              <para>Async</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>-- [1]</para>
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
            <TD>
              <para>(HY010)</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>(IH) [2]</para>
            </TD>
            <TD>
              <para>S0</para>
            </TD>
            <TD>
              <para>S0</para>
            </TD>
            <TD>
              <para>S0</para>
            </TD>
            <TD>
              <para>S0</para>
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
              <para>-- [3]</para>
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
      <para>[1]   This row shows transitions when <legacyItalic>HandleType</legacyItalic> was SQL_HANDLE_ENV or SQL_HANDLE_DBC.</para>
      <para>[2]   This row shows transitions when <legacyItalic>HandleType</legacyItalic> was SQL_HANDLE_STMT.</para>
      <para>[3]   This row shows transitions when <legacyItalic>HandleType</legacyItalic> was SQL_HANDLE_DESC and the descriptor was explicitly allocated.</para>
    </content>
  </section>
  <section>
    <title>SQLFreeStmt</title>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>S0 </para>
              <para>Unallocated</para>
            </TD>
            <TD>
              <para>S1</para>
              <para>Allocated</para>
            </TD>
            <TD>
              <para>S2–S3</para>
              <para>Prepared</para>
            </TD>
            <TD>
              <para>S4</para>
              <para>Executed</para>
            </TD>
            <TD>
              <para>S5–S7</para>
              <para>Cursor</para>
            </TD>
            <TD>
              <para>S8–S10</para>
              <para>Need Data</para>
            </TD>
            <TD>
              <para>S11–S12</para>
              <para>Async</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>(IH) [1]</para>
            </TD>
            <TD>
              <para>--</para>
            </TD>
            <TD>
              <para>--</para>
            </TD>
            <TD>
              <para>S1 [np]  S2 [p] </para>
            </TD>
            <TD>
              <para>S1 [np]  S3 [p] </para>
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
              <para>(IH) [2]</para>
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
              <para>(HY010)</para>
            </TD>
            <TD>
              <para>(HY010)</para>
            </TD>
          </tr>
        </tbody>
      </table>
      <para>[1]   This row shows transitions when <legacyItalic>Option</legacyItalic> was SQL_CLOSE.</para>
      <para>[2]   This row shows transitions when <legacyItalic>Option</legacyItalic> was SQL_UNBIND or SQL_RESET_PARAMS. If the <legacyItalic>Option</legacyItalic> argument was SQL_DROP and the underlying driver is an ODBC 3<legacyItalic>.x</legacyItalic> driver, the Driver Manager maps this to a call to <legacyBold>SQLFreeHandle</legacyBold> with <legacyItalic>HandleType</legacyItalic> set to SQL_HANDLE_STMT. For more information, see the transition table for <legacyLink xlink:href="17a6fcdc-b05a-4de7-be93-a316f39696a1">SQLFreeHandle</legacyLink>.</para>
    </content>
  </section>
  <section>
    <title>SQLGetConnectAttr</title>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>S0 </para>
              <para>Unallocated</para>
            </TD>
            <TD>
              <para>S1</para>
              <para>Allocated</para>
            </TD>
            <TD>
              <para>S2–S3</para>
              <para>Prepared</para>
            </TD>
            <TD>
              <para>S4</para>
              <para>Executed</para>
            </TD>
            <TD>
              <para>S5–S7</para>
              <para>Cursor</para>
            </TD>
            <TD>
              <para>S8–S10</para>
              <para>Need Data</para>
            </TD>
            <TD>
              <para>S11–S12</para>
              <para>Async</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
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
            <TD>
              <para>--</para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <section>
    <title>SQLGetCursorName</title>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>S0 </para>
              <para>Unallocated</para>
            </TD>
            <TD>
              <para>S1</para>
              <para>Allocated</para>
            </TD>
            <TD>
              <para>S2–S3</para>
              <para>Prepared</para>
            </TD>
            <TD>
              <para>S4</para>
              <para>Executed</para>
            </TD>
            <TD>
              <para>S5–S7</para>
              <para>Cursor</para>
            </TD>
            <TD>
              <para>S8–S10</para>
              <para>Need Data</para>
            </TD>
            <TD>
              <para>S11–S12</para>
              <para>Async</para>
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
              <para>(HY010)</para>
            </TD>
            <TD>
              <para>(HY010)</para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <section>
    <title>SQLGetData</title>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>S0 </para>
              <para>Unallocated</para>
            </TD>
            <TD>
              <para>S1</para>
              <para>Allocated</para>
            </TD>
            <TD>
              <para>S2–S3</para>
              <para>Prepared</para>
            </TD>
            <TD>
              <para>S4</para>
              <para>Executed</para>
            </TD>
            <TD>
              <para>S5–S7</para>
              <para>Cursor</para>
            </TD>
            <TD>
              <para>S8–S10</para>
              <para>Need Data</para>
            </TD>
            <TD>
              <para>S11–S12</para>
              <para>Async</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
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
              <para>(24000)</para>
            </TD>
            <TD>
              <para>See next table</para>
            </TD>
            <TD>
              <para>(HY010)</para>
            </TD>
            <TD>
              <para>NS [c] (HY010) [o]</para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <section>
    <title>SQLGetData (Cursor States)</title>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>S5</para>
              <para>Opened</para>
            </TD>
            <TD>
              <para>S6</para>
              <para>SQLFetch or SQLFetchScroll</para>
            </TD>
            <TD>
              <para>S7</para>
              <para>SQLExtendedFetch</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>(24000)</para>
            </TD>
            <TD>
              <para>-- [s] or [nf]  S11 [x]  24000 [b]  HY109 [i]</para>
            </TD>
            <TD>
              <para>-- [s] or [nf]  S11 [x]  24000 [b]  HY109 [i]</para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <section>
    <title>SQLGetDescField and SQLGetDescRec</title>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>S0 </para>
              <para>Unallocated</para>
            </TD>
            <TD>
              <para>S1</para>
              <para>Allocated</para>
            </TD>
            <TD>
              <para>S2–S3</para>
              <para>Prepared</para>
            </TD>
            <TD>
              <para>S4</para>
              <para>Executed</para>
            </TD>
            <TD>
              <para>S5–S7</para>
              <para>Cursor</para>
            </TD>
            <TD>
              <para>S8–S10</para>
              <para>Need Data</para>
            </TD>
            <TD>
              <para>S11–S12</para>
              <para>Async</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>(IH)</para>
            </TD>
            <TD>
              <para>-- [1] or [2] (HY010) [3] </para>
            </TD>
            <TD>
              <para>See next table</para>
            </TD>
            <TD>
              <para>-- [1] or [2] 24000 [3] </para>
            </TD>
            <TD>
              <para>-- [1], [2], or [3] S11 [3] and [x] </para>
            </TD>
            <TD>
              <para>(HY010)</para>
            </TD>
            <TD>
              <para>NS [c] or [4] (HY010) [o] and [5]</para>
            </TD>
          </tr>
        </tbody>
      </table>
      <para>[1]   The <legacyItalic>DescriptorHandle</legacyItalic> argument was an APD or ARD. </para>
      <para>[2]   The <legacyItalic>DescriptorHandle</legacyItalic> argument was an IPD.</para>
      <para>[3]   The <legacyItalic>DescriptorHandle</legacyItalic> argument was an IRD.</para>
      <para>[4]   The <legacyItalic>DescriptorHandle</legacyItalic> argument was the same as the <legacyItalic>DescriptorHandle</legacyItalic> argument in the <legacyBold>SQLGetDescField</legacyBold> or <legacyBold>SQLGetDescRec</legacyBold> function that is running asynchronously.</para>
      <para>[5]   The <legacyItalic>DescriptorHandle</legacyItalic> argument was different than the <legacyItalic>DescriptorHandle</legacyItalic> argument in the <legacyBold>SQLGetDescField</legacyBold> or <legacyBold>SQLGetDescRec</legacyBold> function that is running asynchronously.</para>
    </content>
  </section>
  <section>
    <title>SQLGetDescField and SQLGetDescRec (Prepared States)</title>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>S2 </para>
              <para>No Results</para>
            </TD>
            <TD>
              <para>S3</para>
              <para>Results</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>--[1], [2], or [3] S11[2] and [x]</para>
            </TD>
            <TD>
              <para>--[1], [2], or [3] S11 [x]</para>
            </TD>
          </tr>
        </tbody>
      </table>
      <para>[1]   The <legacyItalic>DescriptorHandle</legacyItalic> argument was an APD or ARD. </para>
      <para>[2]   The <legacyItalic>DescriptorHandle</legacyItalic> argument was an IPD.</para>
      <para>[3]   The <legacyItalic>DescriptorHandle</legacyItalic> argument was an IRD. Note that these functions always return SQL_NO_DATA in state S2 when <legacyItalic>DescriptorHandle</legacyItalic> was an IRD.</para>
    </content>
  </section>
  <section>
    <title>SQLGetDiagField and SQLGetDiagRec</title>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>S0 </para>
              <para>Unallocated</para>
            </TD>
            <TD>
              <para>S1</para>
              <para>Allocated</para>
            </TD>
            <TD>
              <para>S2–S3</para>
              <para>Prepared</para>
            </TD>
            <TD>
              <para>S4</para>
              <para>Executed</para>
            </TD>
            <TD>
              <para>S5–S7</para>
              <para>Cursor</para>
            </TD>
            <TD>
              <para>S8–S10</para>
              <para>Need Data</para>
            </TD>
            <TD>
              <para>S11–S12</para>
              <para>Async</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>--[1]</para>
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
              <para>--[3]</para>
            </TD>
            <TD>
              <para>--[3]</para>
            </TD>
          </tr>
        </tbody>
      </table>
      <para>[1]   This row shows transitions when <legacyItalic>HandleType</legacyItalic> was SQL_HANDLE_ENV, SQL_HANDLE_DBC, or SQL_HANDLE_DESC.</para>
      <para>[2]   This row shows transitions when <legacyItalic>HandleType</legacyItalic> was SQL_HANDLE_STMT.</para>
      <para>[3]   <legacyBold>SQLGetDiagField</legacyBold> always returns an error in this state when <legacyItalic>DiagIdentifier</legacyItalic> is SQL_DIAG_ROW_COUNT.</para>
    </content>
  </section>
  <section>
    <title>SQLGetEnvAttr</title>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>S0 </para>
              <para>Unallocated</para>
            </TD>
            <TD>
              <para>S1</para>
              <para>Allocated</para>
            </TD>
            <TD>
              <para>S2–S3</para>
              <para>Prepared</para>
            </TD>
            <TD>
              <para>S4</para>
              <para>Executed</para>
            </TD>
            <TD>
              <para>S5–S7</para>
              <para>Cursor</para>
            </TD>
            <TD>
              <para>S8–S10</para>
              <para>Need Data</para>
            </TD>
            <TD>
              <para>S11–S12</para>
              <para>Async</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
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
              <para>S0 </para>
              <para>Unallocated</para>
            </TD>
            <TD>
              <para>S1</para>
              <para>Allocated</para>
            </TD>
            <TD>
              <para>S2–S3</para>
              <para>Prepared</para>
            </TD>
            <TD>
              <para>S4</para>
              <para>Executed</para>
            </TD>
            <TD>
              <para>S5–S7</para>
              <para>Cursor</para>
            </TD>
            <TD>
              <para>S8–S10</para>
              <para>Need Data</para>
            </TD>
            <TD>
              <para>S11–S12</para>
              <para>Async</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
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
              <para>S0 </para>
              <para>Unallocated</para>
            </TD>
            <TD>
              <para>S1</para>
              <para>Allocated</para>
            </TD>
            <TD>
              <para>S2–S3</para>
              <para>Prepared</para>
            </TD>
            <TD>
              <para>S4</para>
              <para>Executed</para>
            </TD>
            <TD>
              <para>S5–S7</para>
              <para>Cursor</para>
            </TD>
            <TD>
              <para>S8–S10</para>
              <para>Need Data</para>
            </TD>
            <TD>
              <para>S11–S12</para>
              <para>Async</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
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
            <TD>
              <para>--</para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <section>
    <title>SQLGetStmtAttr</title>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>S0 </para>
              <para>Unallocated</para>
            </TD>
            <TD>
              <para>S1</para>
              <para>Allocated</para>
            </TD>
            <TD>
              <para>S2–S3</para>
              <para>Prepared</para>
            </TD>
            <TD>
              <para>S4</para>
              <para>Executed</para>
            </TD>
            <TD>
              <para>S5–S7</para>
              <para>Cursor</para>
            </TD>
            <TD>
              <para>S8–S10</para>
              <para>Need Data</para>
            </TD>
            <TD>
              <para>S11–S12</para>
              <para>Async</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>(IH)</para>
            </TD>
            <TD>
              <para>--[1] (24000)[2]</para>
            </TD>
            <TD>
              <para>--[1] (24000)[2]</para>
            </TD>
            <TD>
              <para>--[1] (24000)[2]</para>
            </TD>
            <TD>
              <para>See next table</para>
            </TD>
            <TD>
              <para>(HY010)</para>
            </TD>
            <TD>
              <para>(HY010)</para>
            </TD>
          </tr>
        </tbody>
      </table>
      <para>[1]   The statement attribute was not SQL_ATTR_ROW_NUMBER.</para>
      <para>[2]   The statement attribute was SQL_ATTR_ROW_NUMBER.</para>
    </content>
  </section>
  <section>
    <title>SQLGetStmtAttr (Cursor States)</title>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>S5</para>
              <para>Opened</para>
            </TD>
            <TD>
              <para>S6</para>
              <para>SQLFetch or SQLFetchScroll</para>
            </TD>
            <TD>
              <para>S7</para>
              <para>SQLExtendedFetch</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>--[1] (24000)[2]</para>
            </TD>
            <TD>
              <para>--[1] or ([v] and [2]) 24000 [b] and [2] HY109 [i] and [2]</para>
            </TD>
            <TD>
              <para>-- [i] or ([v] and [2]) 24000 [b] and [2] HY109[1] and [2]</para>
            </TD>
          </tr>
        </tbody>
      </table>
      <para>[1]   The <legacyItalic>Attribute</legacyItalic> argument was not SQL_ATTR_ROW_NUMBER.</para>
      <para>[2]   The <legacyItalic>Attribute</legacyItalic> argument was SQL_ATTR_ROW_NUMBER.</para>
    </content>
  </section>
  <section>
    <title>SQLMoreResults</title>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>S0 </para>
              <para>Unallocated</para>
            </TD>
            <TD>
              <para>S1</para>
              <para>Allocated</para>
            </TD>
            <TD>
              <para>S2–S3</para>
              <para>Prepared</para>
            </TD>
            <TD>
              <para>S4</para>
              <para>Executed</para>
            </TD>
            <TD>
              <para>S5–S7</para>
              <para>Cursor</para>
            </TD>
            <TD>
              <para>S8–S10</para>
              <para>Need Data</para>
            </TD>
            <TD>
              <para>S11–S12</para>
              <para>Async</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>(IH)</para>
            </TD>
            <TD>
              <para>--[1]</para>
            </TD>
            <TD>
              <para>--[1]</para>
            </TD>
            <TD>
              <para>-- [s] and [2] S1 [nf], [np], and [4] S2 [nf], [p], and [4] S5 [s] and [3] S11 [x]</para>
            </TD>
            <TD>
              <para>S1 [nf], [np], and [4] S3 [nf], [p] and [4] S4 [s] and [2] S5 [s] and [3] S11 [x]</para>
            </TD>
            <TD>
              <para>(HY010)</para>
            </TD>
            <TD>
              <para>NS [c] (HY010) [o]</para>
            </TD>
          </tr>
        </tbody>
      </table>
      <para>[1]   The function always returns SQL_NO_DATA in this state.</para>
      <para>[2]   The next result is a row count.</para>
      <para>[3]   The next result is a result set.</para>
      <para>[4]   The current result is the last result.</para>
    </content>
  </section>
  <section>
    <title>SQLNativeSql</title>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>S0 </para>
              <para>Unallocated</para>
            </TD>
            <TD>
              <para>S1</para>
              <para>Allocated</para>
            </TD>
            <TD>
              <para>S2–S3</para>
              <para>Prepared</para>
            </TD>
            <TD>
              <para>S4</para>
              <para>Executed</para>
            </TD>
            <TD>
              <para>S5–S7</para>
              <para>Cursor</para>
            </TD>
            <TD>
              <para>S8–S10</para>
              <para>Need Data</para>
            </TD>
            <TD>
              <para>S11–S12</para>
              <para>Async</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
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
            <TD>
              <para>--</para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <section>
    <title>SQLNumParams</title>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>S0 </para>
              <para>Unallocated</para>
            </TD>
            <TD>
              <para>S1</para>
              <para>Allocated</para>
            </TD>
            <TD>
              <para>S2–S3</para>
              <para>Prepared</para>
            </TD>
            <TD>
              <para>S4</para>
              <para>Executed</para>
            </TD>
            <TD>
              <para>S5–S7</para>
              <para>Cursor</para>
            </TD>
            <TD>
              <para>S8–S10</para>
              <para>Need Data</para>
            </TD>
            <TD>
              <para>S11–S12</para>
              <para>Async</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>(IH)</para>
            </TD>
            <TD>
              <para>(HY010)</para>
            </TD>
            <TD>
              <para>-- [s]  S11 [x] </para>
            </TD>
            <TD>
              <para>-- [s]  S11 [x] </para>
            </TD>
            <TD>
              <para>-- [s]  S11 [x] </para>
            </TD>
            <TD>
              <para>(HY010)</para>
            </TD>
            <TD>
              <para>NS [c] (HY010) [o]</para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <section>
    <title>SQLNumResultCols</title>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>S0 </para>
              <para>Unallocated</para>
            </TD>
            <TD>
              <para>S1</para>
              <para>Allocated</para>
            </TD>
            <TD>
              <para>S2–S3</para>
              <para>Prepared</para>
            </TD>
            <TD>
              <para>S4</para>
              <para>Executed</para>
            </TD>
            <TD>
              <para>S5–S7</para>
              <para>Cursor</para>
            </TD>
            <TD>
              <para>S8–S10</para>
              <para>Need Data</para>
            </TD>
            <TD>
              <para>S11–S12</para>
              <para>Async</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>(IH)</para>
            </TD>
            <TD>
              <para>(HY010)</para>
            </TD>
            <TD>
              <para>-- [s]  S11 [x] </para>
            </TD>
            <TD>
              <para>-- [s]  S11 [x] </para>
            </TD>
            <TD>
              <para>-- [s]  S11 [x] </para>
            </TD>
            <TD>
              <para>(HY010)</para>
            </TD>
            <TD>
              <para>NS [c] (HY010) [o]</para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <section>
    <title>SQLParamData</title>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>S0 </para>
              <para>Unallocated</para>
            </TD>
            <TD>
              <para>S1</para>
              <para>Allocated</para>
            </TD>
            <TD>
              <para>S2–S3</para>
              <para>Prepared</para>
            </TD>
            <TD>
              <para>S4</para>
              <para>Executed</para>
            </TD>
            <TD>
              <para>S5–S7</para>
              <para>Cursor</para>
            </TD>
            <TD>
              <para>S8–S10</para>
              <para>Need Data</para>
            </TD>
            <TD>
              <para>S11–S12</para>
              <para>Async</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
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
              <para>(HY010)</para>
            </TD>
            <TD>
              <para>(HY010)</para>
            </TD>
            <TD>
              <para>See next table</para>
            </TD>
            <TD>
              <para>NS [c] (HY010) [o]</para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <section>
    <title>SQLParamData (Need Data States)</title>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>S8</para>
              <para>Need Data</para>
            </TD>
            <TD>
              <para>S9</para>
              <para>Must Put</para>
            </TD>
            <TD>
              <para>S10</para>
              <para>Can Put</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>S1 [e] and [1] S2 [e], [nr], and [2] S3 [e], [r], and [2] S5 [e] and [4] S6 [e] and [5] S7 [e] and [3] S9 [d]  S11 [x] </para>
            </TD>
            <TD>
              <para>HY010</para>
            </TD>
            <TD>
              <para>S1 [e] and [1] S2 [e], [nr], and [2] S3 [e], [r], and [2] S4 [s], [nr], and ([1] or [2]) S5 [s], [r], and ([1] or [2]) S5 ([s] or [e]) and [4] S6 ([s] or [e]) and [5] S7 ([s] or [e]) and [3] S9 [d]  S11 [x] </para>
            </TD>
          </tr>
        </tbody>
      </table>
      <para>[1]   <legacyBold>SQLExecDirect</legacyBold> returned SQL_NEED_DATA.</para>
      <para>[2]   <legacyBold>SQLExecute</legacyBold> returned SQL_NEED_DATA.</para>
      <para>[3]   <legacyBold>SQLSetPos</legacyBold> had been called from state S7 and returned SQL_NEED_DATA.</para>
      <para>[4]   <legacyBold>SQLBulkOperations</legacyBold> had been called from state S5 and returned SQL_NEED_DATA.</para>
      <para>[5]   <legacyBold>SQLSetPos</legacyBold> or <legacyBold>SQLBulkOperations</legacyBold> had been called from state S6 and returned SQL_NEED_DATA.</para>
    </content>
  </section>
  <section>
    <title>SQLPrepare</title>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>S0 </para>
              <para>Unallocated</para>
            </TD>
            <TD>
              <para>S1</para>
              <para>Allocated</para>
            </TD>
            <TD>
              <para>S2–S3</para>
              <para>Prepared</para>
            </TD>
            <TD>
              <para>S4</para>
              <para>Executed</para>
            </TD>
            <TD>
              <para>S5–S7</para>
              <para>Cursor</para>
            </TD>
            <TD>
              <para>S8–S10</para>
              <para>Need Data</para>
            </TD>
            <TD>
              <para>S11–S12</para>
              <para>Async</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>(IH)</para>
            </TD>
            <TD>
              <para>S2 [s] and [nr] S3 [s] and [r] S11 [x] </para>
            </TD>
            <TD>
              <para>-- [s] or ([e] and [1]) S1 [e] and [2] S11 [x] </para>
            </TD>
            <TD>
              <para>S1 [e] and [3] S2 [s], [nr], and [3] S3 [s], [r], and [3] S11 [x] and [3] 24000[4]</para>
            </TD>
            <TD>
              <para>See next table</para>
            </TD>
            <TD>
              <para>(HY010)</para>
            </TD>
            <TD>
              <para>NS [c] (HY010) [o]</para>
            </TD>
          </tr>
        </tbody>
      </table>
      <para>[1]   The preparation fails for a reason other than validating the statement (the SQLSTATE was HY009 [Invalid argument value] or HY090 [Invalid string or buffer length]).</para>
      <para>[2]   The preparation fails while validating the statement (the SQLSTATE was not HY009 [Invalid argument value] or HY090 [Invalid string or buffer length]). </para>
      <para>[3]   The current result is the last or only result, or there are no current results. For more information about multiple results, see <legacyLink xlink:href="a3c32e4b-8fe7-4a33-ae39-ae664001f315">Multiple Results</legacyLink>.</para>
      <para>[4]   The current result is not the last result.</para>
    </content>
  </section>
  <section>
    <title>SQLPrepare (Cursor States)</title>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>S5</para>
              <para>Opened</para>
            </TD>
            <TD>
              <para>S6</para>
              <para>SQLFetch or SQLFetchScroll</para>
            </TD>
            <TD>
              <para>S7</para>
              <para>SQLExtendedFetch</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>24000</para>
            </TD>
            <TD>
              <para>(24000)</para>
            </TD>
            <TD>
              <para>(24000)</para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <section>
    <title>SQLPutData</title>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>S0 </para>
              <para>Unallocated</para>
            </TD>
            <TD>
              <para>S1</para>
              <para>Allocated</para>
            </TD>
            <TD>
              <para>S2–S3</para>
              <para>Prepared</para>
            </TD>
            <TD>
              <para>S4</para>
              <para>Executed</para>
            </TD>
            <TD>
              <para>S5–S7</para>
              <para>Cursor</para>
            </TD>
            <TD>
              <para>S8–S10</para>
              <para>Need Data</para>
            </TD>
            <TD>
              <para>S11–S12</para>
              <para>Async</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
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
              <para>(HY010)</para>
            </TD>
            <TD>
              <para>(HY010)</para>
            </TD>
            <TD>
              <para>See next table</para>
            </TD>
            <TD>
              <para>NS [c] (HY010) [o]</para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <section>
    <title>SQLPutData (Need Data States)</title>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>S8</para>
              <para>Need Data</para>
            </TD>
            <TD>
              <para>S9</para>
              <para>Must Put</para>
            </TD>
            <TD>
              <para>S10</para>
              <para>Can Put</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>HY010</para>
            </TD>
            <TD>
              <para>S1 [e] and [1] S2 [e], [nr], and [2] S3 [e], [r], and [2] S5 [e] and [4] S6 [e] and [5] S7 [e] and [3] S10 [s]  S11 [x] </para>
            </TD>
            <TD>
              <para>-- [s]  S1 [e] and [1] S2 [e], [nr], and [2] S3 [e], [r], and [2] S5 [e] and [4] S6 [e] and [5] S7 [e] and [3] S11 [x]  HY011[6]</para>
            </TD>
          </tr>
        </tbody>
      </table>
      <para>[1]   <legacyBold>SQLExecDirect </legacyBold>returned SQL_NEED_DATA.</para>
      <para>[2]   <legacyBold>SQLExecute</legacyBold> returned SQL_NEED_DATA.</para>
      <para>[3]   <legacyBold>SQLSetPos</legacyBold> had been called from state S7 and returned SQL_NEED_DATA.</para>
      <para>[4]   <legacyBold>SQLBulkOperations</legacyBold> had been called from state S5 and returned SQL_NEED_DATA.</para>
      <para>[5]   <legacyBold>SQLSetPos</legacyBold> or <legacyBold>SQLBulkOperations</legacyBold> had been called from state S6 and returned SQL_NEED_DATA.</para>
      <para>[6]   One or more calls to <legacyBold>SQLPutData</legacyBold> for a single parameter returned SQL_SUCCESS, and then a call to <legacyBold>SQLPutData</legacyBold> was made for the same parameter with <legacyItalic>StrLen_or_Ind</legacyItalic> set to SQL_NULL_DATA. </para>
    </content>
  </section>
  <section>
    <title>SQLRowCount</title>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>S0 </para>
              <para>Unallocated</para>
            </TD>
            <TD>
              <para>S1</para>
              <para>Allocated</para>
            </TD>
            <TD>
              <para>S2–S3</para>
              <para>Prepared</para>
            </TD>
            <TD>
              <para>S4</para>
              <para>Executed</para>
            </TD>
            <TD>
              <para>S5–S7</para>
              <para>Cursor</para>
            </TD>
            <TD>
              <para>S8–S10</para>
              <para>Need Data</para>
            </TD>
            <TD>
              <para>S11–S12</para>
              <para>Async</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
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
              <para>(HY010)</para>
            </TD>
            <TD>
              <para>(HY010)</para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <section>
    <title>SQLSetConnectAttr</title>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>S0 </para>
              <para>Unallocated</para>
            </TD>
            <TD>
              <para>S1</para>
              <para>Allocated</para>
            </TD>
            <TD>
              <para>S2–S3</para>
              <para>Prepared</para>
            </TD>
            <TD>
              <para>S4</para>
              <para>Executed</para>
            </TD>
            <TD>
              <para>S5–S7</para>
              <para>Cursor</para>
            </TD>
            <TD>
              <para>S8–S10</para>
              <para>Need Data</para>
            </TD>
            <TD>
              <para>S11–S12</para>
              <para>Async</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>--[1]</para>
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
              <para>--[2] 24000[3]</para>
            </TD>
            <TD>
              <para>(HY010)</para>
            </TD>
            <TD>
              <para>(HY010)</para>
            </TD>
          </tr>
        </tbody>
      </table>
      <para>[1]   This row shows transitions when <legacyItalic>Attribute</legacyItalic> was a connection attribute. For transitions when <legacyItalic>Attribute</legacyItalic> was a statement attribute, see the statement transition table for <legacyBold>SQLSetStmtAttr</legacyBold>.</para>
      <para>[2]   The <legacyItalic>Attribute</legacyItalic> argument was not SQL_ATTR_CURRENT_CATALOG.</para>
      <para>[3]   The <legacyItalic>Attribute</legacyItalic> argument was SQL_ATTR_CURRENT_CATALOG.</para>
    </content>
  </section>
  <section>
    <title>SQLSetCursorName</title>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>S0 </para>
              <para>Unallocated</para>
            </TD>
            <TD>
              <para>S1</para>
              <para>Allocated</para>
            </TD>
            <TD>
              <para>S2–S3</para>
              <para>Prepared</para>
            </TD>
            <TD>
              <para>S4</para>
              <para>Executed</para>
            </TD>
            <TD>
              <para>S5–S7</para>
              <para>Cursor</para>
            </TD>
            <TD>
              <para>S8–S10</para>
              <para>Need Data</para>
            </TD>
            <TD>
              <para>S11–S12</para>
              <para>Async</para>
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
              <para>(24000)</para>
            </TD>
            <TD>
              <para>(24000)</para>
            </TD>
            <TD>
              <para>(HY010)</para>
            </TD>
            <TD>
              <para>(HY010)</para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <section>
    <title>SQLSetDescField and SQLSetDescRec</title>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>S0 </para>
              <para>Unallocated</para>
            </TD>
            <TD>
              <para>S1</para>
              <para>Allocated</para>
            </TD>
            <TD>
              <para>S2–S3</para>
              <para>Prepared</para>
            </TD>
            <TD>
              <para>S4</para>
              <para>Executed</para>
            </TD>
            <TD>
              <para>S5–S7</para>
              <para>Cursor</para>
            </TD>
            <TD>
              <para>S8–S10</para>
              <para>Need Data</para>
            </TD>
            <TD>
              <para>S11–S12</para>
              <para>Async</para>
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
              <para>(HY010)</para>
            </TD>
            <TD>
              <para>(HY010)</para>
            </TD>
          </tr>
        </tbody>
      </table>
      <para>[1]   This row shows transitions where the <legacyItalic>DescriptorHandle</legacyItalic> argument is an ARD, APD, IPD, or (for <legacyBold>SQLSetDescField</legacyBold>) an IRD when the <legacyItalic>FieldIdentifier</legacyItalic> argument is SQL_DESC_ARRAY_STATUS_PTR or SQL_DESC_ROWS_PROCESSED_PTR. It is an error to call <legacyBold>SQLSetDescField</legacyBold> for an IRD when <legacyItalic>FieldIdentifier</legacyItalic> is any other value.</para>
    </content>
  </section>
  <section>
    <title>SQLSetEnvAttr</title>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>S0 </para>
              <para>Unallocated</para>
            </TD>
            <TD>
              <para>S1</para>
              <para>Allocated</para>
            </TD>
            <TD>
              <para>S2–S3</para>
              <para>Prepared</para>
            </TD>
            <TD>
              <para>S4</para>
              <para>Executed</para>
            </TD>
            <TD>
              <para>S5–S7</para>
              <para>Cursor</para>
            </TD>
            <TD>
              <para>S8–S10</para>
              <para>Need Data</para>
            </TD>
            <TD>
              <para>S11–S12</para>
              <para>Async</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>(HY011)</para>
            </TD>
            <TD>
              <para>(HY011)</para>
            </TD>
            <TD>
              <para>(HY011)</para>
            </TD>
            <TD>
              <para>(HY011)</para>
            </TD>
            <TD>
              <para>(HY011)</para>
            </TD>
            <TD>
              <para>(HY011)</para>
            </TD>
            <TD>
              <para>(HY011)</para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <section>
    <title>SQLSetPos</title>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>S0 </para>
              <para>Unallocated</para>
            </TD>
            <TD>
              <para>S1</para>
              <para>Allocated</para>
            </TD>
            <TD>
              <para>S2–S3</para>
              <para>Prepared</para>
            </TD>
            <TD>
              <para>S4</para>
              <para>Executed</para>
            </TD>
            <TD>
              <para>S5–S7</para>
              <para>Cursor</para>
            </TD>
            <TD>
              <para>S8–S10</para>
              <para>Need Data</para>
            </TD>
            <TD>
              <para>S11–S12</para>
              <para>Async</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
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
              <para>(24000)</para>
            </TD>
            <TD>
              <para>See next table</para>
            </TD>
            <TD>
              <para>(HY010)</para>
            </TD>
            <TD>
              <para>NS [c] (HY010) [o]</para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <section>
    <title>SQLSetPos (Cursor States)</title>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>S5</para>
              <para>Opened</para>
            </TD>
            <TD>
              <para>S6</para>
              <para>SQLFetch or SQLFetchScroll</para>
            </TD>
            <TD>
              <para>S7</para>
              <para>SQLExtendedFetch</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>(24000)</para>
            </TD>
            <TD>
              <para> -- [s]  S8 [d]  S11 [x]  24000 [b]  HY109 [i]</para>
            </TD>
            <TD>
              <para>-- [s]  S8 [d]  S11 [x]  24000 [b]  HY109 [i]</para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <section>
    <title>SQLSetStmtAttr</title>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>S0 </para>
              <para>Unallocated</para>
            </TD>
            <TD>
              <para>S1</para>
              <para>Allocated</para>
            </TD>
            <TD>
              <para>S2–S3</para>
              <para>Prepared</para>
            </TD>
            <TD>
              <para>S4</para>
              <para>Executed</para>
            </TD>
            <TD>
              <para>S5–S7</para>
              <para>Cursor</para>
            </TD>
            <TD>
              <para>S8–S10</para>
              <para>Need Data</para>
            </TD>
            <TD>
              <para>S11–S12</para>
              <para>Async</para>
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
              <para>--[1] (HY011)[2]</para>
            </TD>
            <TD>
              <para>--[1] (24000)[2]</para>
            </TD>
            <TD>
              <para>--[1] (24000)[2]</para>
            </TD>
            <TD>
              <para>(HY010) [np] or [1] (HY011) [p] and [2]</para>
            </TD>
            <TD>
              <para>(HY010) [np] or [1] (HY011) [p] and [2]</para>
            </TD>
          </tr>
        </tbody>
      </table>
      <para>[1]   The <legacyItalic>Attribute</legacyItalic> argument was not SQL_ATTR_CONCURRENCY, SQL_ATTR_CURSOR_TYPE, SQL_ATTR_SIMULATE_CURSOR, SQL_ATTR_USE_BOOKMARKS, SQL_ATTR_CURSOR_SCROLLABLE, or SQL_ATTR_CURSOR_SENSITIVITY.</para>
      <para>[2]   The <legacyItalic>Attribute</legacyItalic> argument was SQL_ATTR_CONCURRENCY, SQL_ATTR_CURSOR_TYPE, SQL_ATTR_SIMULATE_CURSOR, SQL_ATTR_USE_BOOKMARKS, SQL_ATTR_CURSOR_SCROLLABLE, or SQL_ATTR_CURSOR_SENSITIVITY.</para>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>