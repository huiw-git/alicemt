---
title: Step 3: Build and Execute an SQL Statement
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 133b8bd4-a3c8-4f7e-93c5-c05283c8e96f
manager:jhubbard
translation.priority.ht: 
  - en-gb
---
# Step 3: Build and Execute an SQL Statement
<?xml version="1.0" encoding="utf-8"?>
<developerWalkthroughDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The third step is to build and execute an SQL statement, as shown in the following illustration. The methods used to perform this step are likely to vary tremendously. The application might prompt the user to enter an SQL statement, build an SQL statement based on user input, or use a hard-coded SQL statement. For more information, see <legacyLink xlink:href="ee9cd360-07e5-4f8a-804b-ad95aecae3e4">Constructing SQL Statements</legacyLink>.</para>
    <mediaLink>
      <image xlink:href="97ae2c14-982a-4a1a-b2bc-3695a7dd0e87" />
    </mediaLink>
  </introduction>
  <section>
    <content>
      <para>If the SQL statement contains parameters, the application binds them to application variables by calling <legacyBold>SQLBindParameter</legacyBold> for each parameter. For more information, see <legacyLink xlink:href="58d5b166-2578-4699-a560-1f1e6d86c49a">Statement Parameters</legacyLink>.</para>
      <para>After the SQL statement is built and any parameters are bound, the statement is executed with <legacyBold>SQLExecDirect</legacyBold>. If the statement will be executed multiple times, it can be prepared with <legacyBold>SQLPrepare</legacyBold> and executed with <legacyBold>SQLExecute</legacyBold>. For more information, see <legacyLink xlink:href="e5f0d2ee-0453-4faf-b007-12978dd300a1">Executing a Statement</legacyLink>.</para>
      <para>The application might also forgo executing an SQL statement altogether and instead call a function to return a result set containing catalog information, such as the available columns or tables. For more information, see <legacyLink xlink:href="d5915d0c-eec3-4382-850e-bd863763c99a">Uses of Catalog Data</legacyLink>.</para>
      <para>The application's next action depends on the type of SQL statement executed.</para>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>Type of SQL statement</para>
            </TD>
            <TD>
              <para>Proceed to</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>               <legacyBold>SELECT</legacyBold> or catalog function</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="77d30142-c774-473c-96fb-b364bb92ac60">Step 4a: Fetch the Results</legacyLink>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>               <legacyBold>UPDATE</legacyBold>, <legacyBold>DELETE</legacyBold>, or <legacyBold>INSERT</legacyBold></para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="3af481b1-d694-446e-948d-e3a5edcad050">Step 4b: Fetch the Row Count</legacyLink>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>All other SQL statements</para>
            </TD>
            <TD>
              <para>Step 3: Build and Execute an SQL Statement (this topic) or <legacyLink xlink:href="311685e2-f7b5-4ddc-8020-59380cd2f035">Step 5: Commit the Transaction</legacyLink></para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <relatedTopics />
</developerWalkthroughDocument>