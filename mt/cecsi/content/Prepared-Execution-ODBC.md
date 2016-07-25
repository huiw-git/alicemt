---
title: "Prepared Execution ODBC"
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f08c8a98-31ee-48b2-9dbf-6f31c2166dbb
caps.latest.revision: 5
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Prepared Execution ODBC
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Prepared execution is an efficient way to execute a statement more than once. The statement is first compiled, or <legacyItalic>prepared,</legacyItalic> into an access plan. The access plan is then executed one or more times at a later time. For more information about access plans, see <legacyLink xlink:href="96270c4f-2efd-4dc1-a985-ed7fd5658db2">Processing an SQL Statement</legacyLink>.</para>
    <para>Prepared execution is commonly used by vertical and custom applications to repeatedly execute the same, parameterized SQL statement. For example, the following code prepares a statement to update the prices of different parts. It then executes the statement multiple times with different parameter values each time.</para>
    <code>SQLREAL       Price;
SQLUINTEGER   PartID;
SQLINTEGER    PartIDInd = 0, PriceInd = 0;

// Prepare a statement to update salaries in the Employees table.
SQLPrepare(hstmt, "UPDATE Parts SET Price = ? WHERE PartID = ?", SQL_NTS);

// Bind Price to the parameter for the Price column and PartID to
// the parameter for the PartID column.
SQLBindParameter(hstmt, 1, SQL_PARAM_INPUT, SQL_C_FLOAT, SQL_REAL, 7, 0,
                  &amp;Price, 0, &amp;PriceInd);
SQLBindParameter(hstmt, 2, SQL_PARAM_INPUT, SQL_C_ULONG, SQL_INTEGER, 10, 0,
                  &amp;PartID, 0, &amp;PartIDInd);

// Repeatedly execute the statement.
while (GetPrice(&amp;PartID, &amp;Price)) {
   SQLExecute(hstmt);
}</code>
    <para>Prepared execution is faster than direct execution for statements executed more than once, primarily because the statement is compiled only once; statements executed directly are compiled each time they are executed. Prepared execution also can provide a reduction in network traffic because the driver can send an access plan identifier to the data source each time the statement is executed, rather than an entire SQL statement, if the data source supports access plan identifiers.</para>
    <para>The application can retrieve the metadata for the result set after the statement is prepared and before it is executed. However, returning metadata for prepared, unexecuted statements is expensive for some drivers and should be avoided by interoperable applications if possible. For more information, see <legacyLink xlink:href="6d134515-e34d-4563-96d7-8ad7714818fd">Result Set Metadata</legacyLink>.</para>
    <para>Prepared execution should not be used for statements executed a single time. For such statements, it is slightly slower than direct execution because it requires an additional ODBC function call.</para>
    <alert class="important">
      <para>Committing or rolling back a transaction, either by explicitly calling <legacyBold>SQLEndTran</legacyBold> or by working in auto-commit mode, causes some data sources to delete the access plans for all statements on a connection. For more information, see the SQL_CURSOR_COMMIT_BEHAVIOR and SQL_CURSOR_ROLLBACK_BEHAVIOR options in the <legacyLink xlink:href="49dceccc-d816-4ada-808c-4c6138dccb64">SQLGetInfo</legacyLink> function description.</para>
    </alert>
    <para>To prepare and execute a statement, the application:  </para>
    <list class="ordered">
      <listItem>
        <para>Calls <legacyBold>SQLPrepare</legacyBold> and passes it a string containing the SQL statement.</para>
      </listItem>
      <listItem>
        <para>Sets the values of any parameters. Parameters can actually be set before or after preparing the statement. For more information, see <legacyLink xlink:href="58d5b166-2578-4699-a560-1f1e6d86c49a">Statement Parameters</legacyLink>, later in this section.</para>
      </listItem>
      <listItem>
        <para>Calls <legacyBold>SQLExecute</legacyBold> and does any additional processing that is necessary, such as fetching data.</para>
      </listItem>
      <listItem>
        <para>Repeats steps 2 and 3 as necessary.</para>
      </listItem>
      <listItem>
        <para>When <legacyBold>SQLPrepare</legacyBold> is called, the driver: </para>
        <list class="bullet">
          <listItem>
            <para>Modifies the SQL statement to use the data source's SQL grammar without parsing the statement. This includes replacing the escape sequences discussed in <legacyLink xlink:href="cf229f21-6c38-4b5b-aca8-f1be0dfeb3d0">Escape Sequences in ODBC</legacyLink>. The application can retrieve the modified form of an SQL statement by calling <legacyBold>SQLNativeSql</legacyBold>. Escape sequences are not replaced if the SQL_ATTR_NOSCAN statement attribute is set.</para>
          </listItem>
          <listItem>
            <para>Sends the statement to the data source for preparation.</para>
          </listItem>
          <listItem>
            <para>Stores the returned access plan identifier for later execution (if the preparation succeeded) or returns any errors (if the preparation failed). Errors include syntactic errors such as SQLSTATE 42000 (Syntax error or access violation) and semantic errors such as SQLSTATE 42S02 (Base table or view not found). </para>
            <alert class="note">
              <para>Some drivers do not return errors at this point but instead return them when the statement is executed or when catalog functions are called. Thus, <legacyBold>SQLPrepare</legacyBold> might appear to have succeeded when in fact it has failed.</para>
            </alert>
          </listItem>
        </list>
      </listItem>
      <listItem>
        <para>When <legacyBold>SQLExecute</legacyBold> is called, the driver: </para>
        <list class="bullet">
          <listItem>
            <para>Retrieves the current parameter values and converts them as necessary. For more information, see <legacyLink xlink:href="58d5b166-2578-4699-a560-1f1e6d86c49a">Statement Parameters</legacyLink>, later in this section.</para>
          </listItem>
          <listItem>
            <para>Sends the access plan identifier and converted parameter values to the data source.</para>
          </listItem>
          <listItem>
            <para>Returns any errors. These are generally run-time errors such as SQLSTATE 24000 (Invalid cursor state). However, some drivers return syntactic and semantic errors at this point.</para>
          </listItem>
        </list>
      </listItem>
    </list>
    <para>If the data source does not support statement preparation, the driver must emulate it to the extent possible. For example, the driver might do nothing when <legacyBold>SQLPrepare</legacyBold> is called and then perform direct execution of the statement when <legacyBold>SQLExecute</legacyBold> is called.</para>
    <para>If the data source supports syntax checking without execution, the driver might submit the statement for checking when <legacyBold>SQLPrepare</legacyBold> is called and submit the statement for execution when <legacyBold>SQLExecute</legacyBold> is called.</para>
    <para>If the driver cannot emulate statement preparation, it stores the statement when <legacyBold>SQLPrepare</legacyBold> is called and submits it for execution when <legacyBold>SQLExecute</legacyBold> is called.</para>
    <para>Because emulated statement preparation is not perfect, <legacyBold>SQLExecute</legacyBold> can return any errors normally returned by <legacyBold>SQLPrepare</legacyBold>.</para>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>