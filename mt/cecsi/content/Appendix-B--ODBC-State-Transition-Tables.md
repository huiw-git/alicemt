---
title: Appendix B: ODBC State Transition Tables
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 15088dbe-896f-4296-b397-02bb3d0ac0fb
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Appendix B: ODBC State Transition Tables
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The tables in this appendix show how ODBC functions cause transitions of the environment, connection, statement, and descriptor states. The state of the environment, connection, statement, or descriptor usually dictates when functions that use the corresponding type of handle (environment, connection, statement, or descriptor) can be called. The environment, connection, statement, and descriptor states overlap roughly as shown in the following illustrations. For example, the exact overlap of connection states C5 and C6 and statement states S1 through S12 is data source–dependent, since transactions begin at different times on different data sources, and descriptor state D1i (implicitly allocated descriptor) depends on the state of the statement with which the descriptor is associated, while state D1e (explicitly allocated descriptor) is independent of the state of any statement. For a description of each state, see <legacyLink xlink:href="9d11b1ab-f4c8-48ca-9812-8c04303f939d">Environment Transitions</legacyLink>, <legacyLink xlink:href="6b6e1a47-4a52-41c8-bb9e-7ddeae09913e">Connection Transitions</legacyLink>, <legacyLink xlink:href="3d70e0e3-fe83-4b4d-beac-42c82495a05b">Statement Transitions</legacyLink>, and <legacyLink xlink:href="0cf24fe6-5e3c-45fa-81b8-4f52ddf8501d">Descriptor Transitions</legacyLink>, later in this appendix.</para>
    <para>The environment and connection states overlap as follows:</para>
    <mediaLink>
      <image xlink:href="829f2f45-92e9-44d6-925b-ad3f05ebc07f" />
    </mediaLink>
    <para>The connection and statement states overlap as follows:</para>
    <mediaLink>
      <image xlink:href="734863c5-0877-4d2c-968b-1962226b7138" />
    </mediaLink>
    <para>The statement and descriptor states overlap as follows:</para>
    <mediaLink>
      <image xlink:href="35ed9b4b-6014-4f6d-a668-5e5c1bf755c7" />
    </mediaLink>
    <para>The connection and descriptor states overlap as follows:</para>
    <mediaLink>
      <image xlink:href="ae124aad-1aea-4991-8283-6634eead6aa5" />
    </mediaLink>
    <para>Each entry in a transition table can be one of the following values:  </para>
    <list class="bullet">
      <listItem>
        <para>
          <legacyBold>-- </legacyBold>—The state is unchanged after executing the function.</para>
      </listItem>
      <listItem>
        <para>
          <legacyBold>E</legacyBold>
          <legacyBold>
            <legacyItalic>n</legacyItalic>
          </legacyBold>, <legacyBold>C</legacyBold><legacyBold><legacyItalic>n</legacyItalic></legacyBold>, <legacyBold>S</legacyBold><legacyBold><legacyItalic>n</legacyItalic></legacyBold>, or <legacyBold>D</legacyBold><legacyBold><legacyItalic>n</legacyItalic></legacyBold> — The environment, connection, statement, or descriptor state moves to the specified state. </para>
      </listItem>
      <listItem>
        <para>
          <legacyBold>(IH)</legacyBold> — An invalid handle was passed to the function. If the handle was a null handle or was a valid handle of the wrong type — for example, a connection handle was passed when a statement handle was required — the function returns SQL_INVALID_HANDLE; otherwise the behavior is undefined and probably fatal. This error is shown only when it is the only possible outcome of calling the function in the specified state. This error does not change the state and is always detected by the Driver Manager, as indicated by the parentheses.</para>
      </listItem>
      <listItem>
        <para>
          <legacyBold>NS</legacyBold> — Next State. The statement transition is the same as if the statement had not gone through the asynchronous states. For example, suppose a statement that creates a result set enters state S11 from state S1 because <legacyBold>SQLExecDirect</legacyBold> returned SQL_STILL_EXECUTING. The NS notation in state S11 means that the transitions for the statement are the same as those for a statement in state S1 that creates a result set. If <legacyBold>SQLExecDirect</legacyBold> returns an error, the statement remains in state S1; if it succeeds, the statement moves to state S5; if it needs data, the statement moves to state S8; and if it is still executing, it remains in state S11.</para>
      </listItem>
      <listItem>
        <para>
          <legacyBold>
            <legacyItalic>XXXXX</legacyItalic>
          </legacyBold>
          <legacyBold> </legacyBold>or <legacyBold>(</legacyBold><legacyBold><legacyItalic>XXXXX</legacyItalic></legacyBold><legacyBold>)</legacyBold> — An SQLSTATE that is related to the transition table; SQLSTATEs detected by the Driver Manager are enclosed in parentheses. The function returned SQL_ERROR and the specified SQLSTATE, but the state does not change. For example, if <legacyBold>SQLExecute</legacyBold> is called before <legacyBold>SQLPrepare</legacyBold>, it returns SQLSTATE HY010 (Function sequence error).</para>
      </listItem>
    </list>
    <alert class="note">
      <para>The tables do not show errors unrelated to the transition tables that do not change the state. For example, when <legacyBold>SQLAllocHandle</legacyBold> is called in environment state E1 and returns SQLSTATE HY001 (Memory allocation error), the environment remains in state E1; this is not shown in the environment transition table for <legacyBold>SQLAllocHandle</legacyBold>.</para>
    </alert>
    <para>If the environment, connection, statement, or descriptor can move to more than one state, each possible state is shown and one or more footnotes explain the conditions under which each transition takes place. The following footnotes may appear in any table.</para>
    <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
      <thead>
        <tr>
          <TD>
            <para>Footnote</para>
          </TD>
          <TD>
            <para>Meaning</para>
          </TD>
        </tr>
      </thead>
      <tbody>
        <tr>
          <TD>
            <para>b</para>
          </TD>
          <TD>
            <para>Before or after. The cursor was positioned before the start of the result set or after the end of the result set.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>c</para>
          </TD>
          <TD>
            <para>Current function. The current function was executing asynchronously.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>d</para>
          </TD>
          <TD>
            <para>Need data. The function returned SQL_NEED_DATA.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>e</para>
          </TD>
          <TD>
            <para>Error. The function returned SQL_ERROR.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>i</para>
          </TD>
          <TD>
            <para>Invalid row. The cursor was positioned on a row in the result set and either the row had been deleted or an error had occurred in an operation on the row. If the row status array existed, the value in the row status array for the row was SQL_ROW_DELETED or SQL_ROW_ERROR. (The row status array is pointed to by the SQL_ATTR_ROW_STATUS_PTR statement attribute.)</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>nf</para>
          </TD>
          <TD>
            <para>Not found. The function returned SQL_NO_DATA. This does not apply when <legacyBold>SQLExecDirect</legacyBold>, <legacyBold>SQLExecute</legacyBold>, or <legacyBold>SQLParamData</legacyBold> returns SQL_NO_DATA after executing a searched update or delete statement.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>np</para>
          </TD>
          <TD>
            <para>Not prepared. The statement was not prepared.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>nr</para>
          </TD>
          <TD>
            <para>No results. The statement will not or did not create a result set.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>o</para>
          </TD>
          <TD>
            <para>Other function. Another function was executing asynchronously.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>p</para>
          </TD>
          <TD>
            <para>Prepared. The statement was prepared.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>r</para>
          </TD>
          <TD>
            <para>Results. The statement will or did create a (possibly empty) result set.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>s</para>
          </TD>
          <TD>
            <para>Success. The function returned SQL_SUCCESS_WITH_INFO or SQL_SUCCESS.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>v</para>
          </TD>
          <TD>
            <para>Valid row. The cursor was positioned on a row in the result set, and the row had been successfully inserted, successfully updated, or another operation on the row had been successfully completed. If the row status array existed, the value in the row status array for the row was SQL_ROW_ADDED, SQL_ROW_SUCCESS, or SQL_ROW_UPDATED. (The row status array is pointed to by the SQL_ATTR_ROW_STATUS_PTR statement attribute.)</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>x</para>
          </TD>
          <TD>
            <para>Executing. The function returned SQL_STILL_EXECUTING.</para>
          </TD>
        </tr>
      </tbody>
    </table>
  </introduction>
  <section>
    <title>SQLFreeHandle</title>
    <content>
      <para>In this example, the row in the environment state transition table for <legacyBold>SQLFreeHandle</legacyBold> when <legacyItalic>HandleType</legacyItalic> is SQL_HANDLE_ENV is as follows.</para>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>E0</para>
              <para>Unallocated</para>
            </TD>
            <TD>
              <para>E1</para>
              <para>Allocated</para>
            </TD>
            <TD>
              <para>E2</para>
              <para>Connection</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>(IH)</para>
            </TD>
            <TD>
              <para>E0</para>
            </TD>
            <TD>
              <para>(HY010)</para>
            </TD>
          </tr>
        </tbody>
      </table>
      <para>If <legacyBold>SQLFreeHandle</legacyBold> is called in environment state E0 with <legacyItalic>HandleType</legacyItalic> set to SQL_HANDLE_ENV, the Driver Manager returns SQL_INVALID_HANDLE. If it is called in state E1 with <legacyItalic>HandleType</legacyItalic> set to SQL_HANDLE_ENV, the environment moves to state E0 if the function succeeds and remains in state E1 if the function fails. If it is called in state E2 with <legacyItalic>HandleType</legacyItalic> set to SQL_HANDLE_ENV, the Driver Manager always returns SQL_ERROR and SQLSTATE HY010 (Function sequence error) and the environment remains in state E2.</para>
      <para>To understand the state transition tables, it is necessary to understand which item (environment, connection, statement, or descriptor) they refer to. Suppose a function accepts the handle of an item of type X. The X state transition table for that function describes how calling the function, with the handle of an item of type X, affects that item. For example, <legacyBold>SQLDisconnect</legacyBold> accepts a connection handle. The connection state transition table for <legacyBold>SQLDisconnect</legacyBold> describes how <legacyBold>SQLDisconnect</legacyBold> affects the state of the connection for which it is called.</para>
      <para>Suppose a function accepts the handle of an item of type Y, where Y is not equal to X. The X state transition table for that function describes how calling the function, with a handle of type X that is associated with the item of type Y, affects the item of type Y. For example, the statement state transition table for <legacyBold>SQLDisconnect</legacyBold> describes how <legacyBold>SQLDisconnect</legacyBold> affects the state of a statement when called with the handle of the connection with which the statement is associated.</para>
      <para>This appendix contains the following topics.  </para>
      <list class="bullet">
        <listItem>
          <para>             <legacyLink xlink:href="9d11b1ab-f4c8-48ca-9812-8c04303f939d">Environment Transitions</legacyLink>           </para>
        </listItem>
        <listItem>
          <para>             <legacyLink xlink:href="6b6e1a47-4a52-41c8-bb9e-7ddeae09913e">Connection Transitions</legacyLink>           </para>
        </listItem>
        <listItem>
          <para>             <legacyLink xlink:href="3d70e0e3-fe83-4b4d-beac-42c82495a05b">Statement Transitions</legacyLink>           </para>
        </listItem>
        <listItem>
          <para>             <legacyLink xlink:href="0cf24fe6-5e3c-45fa-81b8-4f52ddf8501d">Descriptor Transitions</legacyLink>           </para>
        </listItem>
      </list>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>