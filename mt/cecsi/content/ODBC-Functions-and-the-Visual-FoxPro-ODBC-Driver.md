---
title: "ODBC Functions and the Visual FoxPro ODBC Driver"
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 512f9cee-ffad-439b-b612-b49c34c32658
caps.latest.revision: 5
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# ODBC Functions and the Visual FoxPro ODBC Driver
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The topics in this section provide a brief summary of ODBC API functions and any Visual FoxPro–specific details. </para>
    <alert class="note">
      <para>For general information about ODBC functions, see <legacyLink xlink:href="b7a49774-f458-44ce-9a04-a0457501405b">ODBC API Reference</legacyLink> in "ODBC Programmer's Guide".</para>
    </alert>
    <para>The ODBC API functions have been divided into three main categories here: Core Level API functions, Level 1 API functions, and Level 2 API functions.</para>
    <alert class="note">
      <para>Several of the functions behave differently depending on whether the data source is defined as a connection to a directory of <legacyLink xlink:href="a379b3cb-0393-46e7-b03b-724a56d8f31c">free tables</legacyLink> (.dbf files) or to a Visual FoxPro <legacyLink xlink:href="a379b3cb-0393-46e7-b03b-724a56d8f31c">database</legacyLink> (.dbc file). Certain operations are supported only for database connections.</para>
    </alert>
  </introduction>
  <section>
    <title>Core Level API Support</title>
    <content>
      <para>The ODBC Core Level API functions are listed in the following table. All of these functions are supported by the Visual FoxPro ODBC Driver.</para>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <tbody>
          <tr>
            <TD>
              <para>               <legacyLink xlink:href="70d48b12-def5-475c-b8e1-654a55fdfe0f">SQLAllocConnect</legacyLink>             </para>
            </TD>
            <TD>
              <para>               <legacyLink xlink:href="cce0c25f-fa85-4cf5-bfee-4b7a9401f585">SQLExecute</legacyLink>             </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>               <legacyLink xlink:href="a21c3782-273f-40b3-b239-47beaf8df462">SQLAllocEnv</legacyLink>             </para>
            </TD>
            <TD>
              <para>               <legacyLink xlink:href="6198a006-6f25-4328-8403-2aba29b7041f">SQLFetch</legacyLink>             </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>               <legacyLink xlink:href="ba973025-18c8-481b-a383-6ed935237894">SQLAllocStmt</legacyLink>             </para>
            </TD>
            <TD>
              <para>               <legacyLink xlink:href="5ecfbbed-43f6-4875-a6a7-732f36431e91">SQLFreeConnect</legacyLink>             </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>               <legacyLink xlink:href="984d6605-39ba-4d33-ac94-22625bfa6107">SQLBindCol</legacyLink>             </para>
            </TD>
            <TD>
              <para>               <legacyLink xlink:href="83011775-e31d-4663-b68b-999113a20d5b">SQLFreeEnv</legacyLink>             </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>               <legacyLink xlink:href="4f7baa1d-37ef-4051-ae13-7dc38033af16">SQLCancel</legacyLink>             </para>
            </TD>
            <TD>
              <para>               <legacyLink xlink:href="a5320226-a6fc-4999-9b3b-2fdee6bdf7eb">SQLFreeStmt</legacyLink>             </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>               <legacyLink xlink:href="d403dfa0-c26d-47d4-91d9-2f29aa387399">SQLColAttributes</legacyLink>             </para>
            </TD>
            <TD>
              <para>               <legacyLink xlink:href="8b1c5233-950e-4173-ae15-dfc46be6ed09">SQLGetCursorName</legacyLink>             </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>               <legacyLink xlink:href="49cbfafa-b21e-4e89-b248-9c7098f46b20">SQLConnect</legacyLink>             </para>
            </TD>
            <TD>
              <para>               <legacyLink xlink:href="a83d826c-6908-4115-b6e6-4d0615ff1738">SQLNumResultCols</legacyLink>             </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>               <legacyLink xlink:href="a8d06507-8376-42b5-b09f-338a77cea131">SQLDescribeCol</legacyLink>             </para>
            </TD>
            <TD>
              <para>               <legacyLink xlink:href="0c4cb5a4-9729-4b2e-a0c6-52027b92e8fc">SQLPrepare</legacyLink>             </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>               <legacyLink xlink:href="78ae1695-b53e-48ff-be49-ecff1f599e61">SQLDisconnect</legacyLink>             </para>
            </TD>
            <TD>
              <para>               <legacyLink xlink:href="9d851f8d-94ca-47ae-a4ad-53863be2d404">SQLRowCount</legacyLink>             </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>               <legacyLink xlink:href="8315ec16-1c22-447a-a577-39bd94f61070">SQLError</legacyLink>             </para>
            </TD>
            <TD>
              <para>               <legacyLink xlink:href="2ac5a8b5-f084-405b-b0d7-546284dfa111">SQLSetCursorName</legacyLink>             </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>               <legacyLink xlink:href="5004060f-8510-4018-87a4-d41789e69d3e">SQLExecDirect</legacyLink>             </para>
            </TD>
            <TD>
              <para>               <legacyLink xlink:href="92cf86c0-f7a8-44d7-b59f-a1342677440b">SQLTransact</legacyLink>             </para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <section>
    <title>Level 1 API Support</title>
    <content>
      <para>The ODBC Level 1 API functions are listed in the following table. All of these functions are fully or partially supported by the Visual FoxPro ODBC Driver.</para>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <tbody>
          <tr>
            <TD>
              <para>               <legacyLink xlink:href="8a69fda2-8903-451a-b030-851bf05aa074">SQLBindParameter</legacyLink>             </para>
            </TD>
            <TD>
              <para>               <legacyLink xlink:href="5f25e20b-a4ef-42da-aeb6-00e0510fb1cc">SQLGetTypeInfo</legacyLink>             </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>               <legacyLink xlink:href="b588a875-0153-43a0-9b76-f89e728cfa65">SQLColumns</legacyLink>             </para>
            </TD>
            <TD>
              <para>               <legacyLink xlink:href="a2308f6c-2fa1-47e9-903f-37c2a03c723a">SQLParamData</legacyLink>             </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>               <legacyLink xlink:href="10492c8f-3a18-4971-9db8-879e878083b9">SQLDriverConnect</legacyLink>             </para>
            </TD>
            <TD>
              <para>               <legacyLink xlink:href="8c79e9ba-afa0-4e20-9c53-371cc42b4a97">SQLPutData</legacyLink>             </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>               <legacyLink xlink:href="5703eb39-f3b2-4f3a-8676-a5625ae29a41">SQLGetConnectOption</legacyLink>             </para>
            </TD>
            <TD>
              <para>               <legacyLink xlink:href="5a35449e-4694-4ee5-9fa1-45d5a8fe7823">SQLSetConnectOption</legacyLink>             </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>               <legacyLink xlink:href="fbf1b1eb-ecab-43d6-9099-3d627344e0fe">SQLGetData</legacyLink>             </para>
            </TD>
            <TD>
              <para>               <legacyLink xlink:href="76b813e3-c7dc-4bb2-a710-d2aa9dcfdc36">SQLSetStmtOption</legacyLink>             </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>               <legacyLink xlink:href="8102932a-88b3-49d8-bf7a-c766f54878c0">SQLGetFunctions</legacyLink>             </para>
            </TD>
            <TD>
              <para>               <legacyLink xlink:href="b72a978d-6a60-475a-b7d9-c424d77bbe30">SQLSpecialColumns</legacyLink>             </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>               <legacyLink xlink:href="fbc39e3d-67d9-4331-bf5f-76dbd74c4c45">SQLGetInfo</legacyLink>             </para>
            </TD>
            <TD>
              <para>               <legacyLink xlink:href="bb48c22f-1fd5-47b4-8eaa-ff69cd431cf9">SQLStatistics</legacyLink>             </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>               <legacyLink xlink:href="984a8b1d-f12c-420c-8be4-f555114c764b">SQLGetStmtOption</legacyLink>             </para>
            </TD>
            <TD>
              <para>               <legacyLink xlink:href="69e2a038-5def-423f-91aa-8756e069dd2a">SQLTables</legacyLink>             </para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <section>
    <title>Level 2 API Support</title>
    <content>
      <para>The following ODBC Level 2 API functions are fully or partially supported:  </para>
      <list class="bullet">
        <listItem>
          <para>             <legacyLink xlink:href="033f8d37-b2dd-4a4e-b93a-70c25b25b72e">SQLDataSources</legacyLink>           </para>
        </listItem>
        <listItem>
          <para>             <legacyLink xlink:href="179b11e0-665f-45a2-b926-c3d870a0dab8">SQLDrivers</legacyLink>           </para>
        </listItem>
        <listItem>
          <para>             <legacyLink xlink:href="b28af112-fb47-4143-b11e-3b743b2ae1b8">SQLExtendedFetch</legacyLink>           </para>
        </listItem>
        <listItem>
          <para>             <legacyLink xlink:href="dc59b1dd-c158-4b45-ab46-638be1fa49b8">SQLMoreResults</legacyLink>           </para>
        </listItem>
        <listItem>
          <para>             <legacyLink xlink:href="4fe4eec8-6a65-4b1f-aac3-25b14fe4ea94">SQLNumParams</legacyLink>           </para>
        </listItem>
        <listItem>
          <para>             <legacyLink xlink:href="7f94a6e2-9c34-405c-b2b0-304d94269715">SQLParamOptions</legacyLink>           </para>
        </listItem>
        <listItem>
          <para>             <legacyLink xlink:href="8dbe2903-efdc-45e0-a079-9e357c5fd81b">SQLPrimaryKeys</legacyLink>           </para>
        </listItem>
        <listItem>
          <para>             <legacyLink xlink:href="ec8e5a9d-7aac-4e7f-a75f-cf670c036f33">SQLSetPos</legacyLink>           </para>
        </listItem>
        <listItem>
          <para>             <legacyLink xlink:href="693e6e28-a845-41b1-9622-5058b0d87229">SQLSetScrollOptions</legacyLink> (partial support)</para>
        </listItem>
      </list>
      <para>The following Level 2 API functions are not supported:  </para>
      <list class="bullet">
        <listItem>
          <para>SQLBrowseConnect</para>
        </listItem>
        <listItem>
          <para>SQLColumnPrivileges</para>
        </listItem>
        <listItem>
          <para>SQLDescribeParam</para>
        </listItem>
        <listItem>
          <para>SQLForeignKeys</para>
        </listItem>
        <listItem>
          <para>SQLNativeSql</para>
        </listItem>
        <listItem>
          <para>SQLProcedureColumns</para>
        </listItem>
        <listItem>
          <para>SQLProcedures</para>
        </listItem>
        <listItem>
          <para>SQLTablePrivileges</para>
        </listItem>
      </list>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>