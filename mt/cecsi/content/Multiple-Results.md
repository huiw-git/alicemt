---
title: "Multiple Results"
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a3c32e4b-8fe7-4a33-ae39-ae664001f315
caps.latest.revision: 4
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Multiple Results
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>A <legacyItalic>result</legacyItalic> is something returned by the data source after a statement is executed. ODBC has two types of results: result sets and row counts. <legacyItalic>Row counts</legacyItalic> are the number of rows affected by an update, delete, or insert statement. Batches, described in <legacyLink xlink:href="766488cc-450c-434c-9c88-467f6c57e17c">Batches of SQL Statements</legacyLink>, can generate multiple results.</para>
    <para>The following table lists the <legacyBold>SQLGetInfo</legacyBold> options an application uses to determine whether a data source returns multiple results for each different type of batch. In particular, a data source can return a single row count for the entire batch of statements or individual row counts for each statement in the batch. In the case of a result set–generating statement executed with an array of parameters, the data source can return a single result set for all sets of parameters or individual result sets for each set of parameters.</para>
    <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
      <thead>
        <tr>
          <TD>
            <para>Batch type</para>
          </TD>
          <TD>
            <para>Row counts</para>
          </TD>
          <TD>
            <para>Result sets</para>
          </TD>
        </tr>
      </thead>
      <tbody>
        <tr>
          <TD>
            <para>Explicit batch</para>
          </TD>
          <TD>
            <para>SQL_BATCH_ROW_COUNT[a]</para>
          </TD>
          <TD>
            <para>--[b]</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>Procedure</para>
          </TD>
          <TD>
            <para>SQL_BATCH_ROW_COUNT[a]</para>
          </TD>
          <TD>
            <para>--[b]</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>Arrays of parameters</para>
          </TD>
          <TD>
            <para>SQL_PARAM_ARRAYS_ROW_COUNTS</para>
          </TD>
          <TD>
            <para>SQL_PARAM_ARRAYS_SELECTS</para>
          </TD>
        </tr>
      </tbody>
    </table>
    <para>[a]   Row count–generating statements in a batch may be supported, yet the return of the row counts not supported. The SQL_BATCH_SUPPORT option in <legacyBold>SQLGetInfo </legacyBold>indicates whether row count–generating statements are allowed in batches; the SQL_BATCH_ROW_COUNTS option indicates whether these row counts are returned to the application.</para>
    <para>[b]   Explicit batches and procedures always return multiple result sets when they include multiple result set–generating statements.</para>
    <alert class="note">
      <para>The SQL_MULT_RESULT_SETS option introduced in ODBC 1.0 provides only general information about whether multiple result sets can be returned. In particular, it is set to "Y" if the SQL_BS_SELECT_EXPLICIT or SQL_BS_SELECT_PROC bits are returned for SQL_BATCH_SUPPORT or if SQL_PAS_BATCH is returned for SQL_PARAM_ARRAYS_SELECT.</para>
    </alert>
    <para>To process multiple results, an application calls <legacyBold>SQLMoreResults</legacyBold>. This function discards the current result and makes the next result available. It returns SQL_NO_DATA when no more results are available. For example, suppose the following statements are executed as a batch:</para>
    <code>SELECT * FROM Parts WHERE Price &gt; 100.00;
UPDATE Parts SET Price = 0.9 * Price WHERE Price &gt; 100.00</code>
    <para>After these statements are executed, the application fetches rows from the result set created by the <legacyBold>SELECT</legacyBold> statement. When it is done fetching rows, it calls <legacyBold>SQLMoreResults</legacyBold> to make available the number of parts that were repriced. If necessary, <legacyBold>SQLMoreResults</legacyBold> discards unfetched rows and closes the cursor. The application then calls <legacyBold>SQLRowCount</legacyBold> to determine how many parts were repriced by the <legacyBold>UPDATE </legacyBold>statement.</para>
    <para>It is driver-specific whether the entire batch statement is executed before any results are available. In some implementations, this is the case; in others, calling <legacyBold>SQLMoreResults</legacyBold> triggers the execution of the next statement in the batch.</para>
    <para>If one of the statements in a batch fails, <legacyBold>SQLMoreResults</legacyBold> will return either SQL_ERROR or SQL_SUCCESS_WITH_INFO. If the batch was aborted when the statement failed or the failed statement was the last statement in the batch, <legacyBold>SQLMoreResults</legacyBold> will return SQL_ERROR. If the batch was not aborted when the statement failed and the failed statement was not the last statement in the batch, <legacyBold>SQLMoreResults</legacyBold> will return SQL_SUCCESS_WITH_INFO. SQL_SUCCESS_WITH_INFO indicates that at least one result set or count was generated and that the batch was not aborted.</para>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>