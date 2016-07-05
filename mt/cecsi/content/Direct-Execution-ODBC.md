---
title: Direct Execution ODBC
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: dd00a535-b136-494f-913b-410838e3de7e
translation.priority.ht: 
  - en-gb
---
# Direct Execution ODBC
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Direct execution is the simplest way to execute a statement. When the statement is submitted for execution, the data source compiles it into an access plan and then executes that access plan.</para>
    <para>Direct execution is commonly used by generic applications that build and execute statements at run time. For example, the following code builds an SQL statement and executes it a single time:</para>
    <code>SQLCHAR *SQLStatement;

// Build an SQL statement.
BuildStatement(SQLStatement);

// Execute the statement.
SQLExecDirect(hstmt, SQLStatement, SQL_NTS);</code>
    <para>Direct execution works best for statements that will be executed a single time. Its major drawback is that the SQL statement is parsed every time it is executed. In addition, the application cannot retrieve information about the result set created by the statement (if any) until after the statement is executed; this is possible if the statement is prepared and executed in two separate steps.</para>
    <para>To execute a statement directly, the application performs the following actions:  </para>
    <list class="ordered">
      <listItem>
        <para>Sets the values of any parameters. For more information, see <legacyLink xlink:href="58d5b166-2578-4699-a560-1f1e6d86c49a">Statement Parameters</legacyLink>, later in this section.</para>
      </listItem>
      <listItem>
        <para>Calls <legacyBold>SQLExecDirect</legacyBold> and passes it a string containing the SQL statement.</para>
      </listItem>
      <listItem>
        <para>When <legacyBold>SQLExecDirect</legacyBold> is called, the driver: </para>
        <list class="bullet">
          <listItem>
            <para>Modifies the SQL statement to use the data source's SQL grammar without parsing the statement; this includes replacing the escape sequences discussed in <legacyLink xlink:href="cf229f21-6c38-4b5b-aca8-f1be0dfeb3d0">Escape Sequences in ODBC</legacyLink>. The application can retrieve the modified form of an SQL statement by calling <legacyBold>SQLNativeSql</legacyBold>. Escape sequences are not replaced if the SQL_ATTR_NOSCAN statement attribute is set.</para>
          </listItem>
          <listItem>
            <para>Retrieves the current parameter values and converts them as necessary. For more information, see <legacyLink xlink:href="58d5b166-2578-4699-a560-1f1e6d86c49a">Statement Parameters</legacyLink>, later in this section.</para>
          </listItem>
          <listItem>
            <para>Sends the statement and converted parameter values to the data source for execution.</para>
          </listItem>
          <listItem>
            <para>Returns any errors. These include sequencing or state diagnostics such as SQLSTATE 24000 (Invalid cursor state), syntactic errors such as SQLSTATE 42000 (Syntax error or access violation), and semantic errors such as SQLSTATE 42S02 (Base table or view not found).</para>
          </listItem>
        </list>
      </listItem>
    </list>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>