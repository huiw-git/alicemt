---
title: Long Data and SQLSetPos and SQLBulkOperations
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e2fdf842-5e4c-46ca-bb21-4625c3324f28
translation.priority.ht: 
  - en-gb
---
# Long Data and SQLSetPos and SQLBulkOperations
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>As is the case with parameters in SQL statements, long data can be sent when updating rows with <legacyBold>SQLBulkOperations</legacyBold> or <legacyBold>SQLSetPos</legacyBold> or when inserting rows with <legacyBold>SQLBulkOperations</legacyBold>. The data is sent in parts, with multiple calls to <legacyBold>SQLPutData</legacyBold>. Columns for which data is sent at execution time are known as <legacyItalic>data-at-execution columns</legacyItalic>.</para>
    <alert class="note">
      <para>An application actually can send any type of data at execution time with <legacyBold>SQLPutData</legacyBold>, although only character and binary data can be sent in parts. However, if the data is small enough to fit in a single buffer, there is generally no reason to use <legacyBold>SQLPutData</legacyBold>. It is much easier to bind the buffer and let the driver retrieve the data from the buffer.</para>
    </alert>
    <para>Because long data columns typically are not bound, the application must bind the column before calling <legacyBold>SQLBulkOperations</legacyBold> or <legacyBold>SQLSetPos</legacyBold> and unbind it after calling <legacyBold>SQLBulkOperations</legacyBold> or <legacyBold>SQLSetPos</legacyBold>. The column must be bound because <legacyBold>SQLBulkOperations</legacyBold> or <legacyBold>SQLSetPos</legacyBold> operates only on bound columns and must be unbound so that <legacyBold>SQLGetData</legacyBold> can be used to retrieve data from the column.</para>
    <para>To send data at execution time, the application does the following:  </para>
    <list class="ordered">
      <listItem>
        <para>Places a 32-bit value in the rowset buffer instead of a data value. This value will be returned to the application later, so the application should set it to a meaningful value, such as the number of the column or the handle of a file containing data.</para>
      </listItem>
      <listItem>
        <para>Sets the value in the length/indicator buffer to the result of the SQL_LEN_DATA_AT_EXEC(<legacyItalic>length</legacyItalic>) macro. This value indicates to the driver that the data for the parameter will be sent with <legacyBold>SQLPutData</legacyBold>. The <legacyItalic>length</legacyItalic> value is used when sending long data to a data source that needs to know how many bytes of long data will be sent so that it can preallocate space. To determine whether a data source requires this value, the application calls <legacyBold>SQLGetInfo</legacyBold> with the SQL_NEED_LONG_DATA_LEN option. All drivers must support this macro; if the data source does not require the byte length, the driver can ignore it.</para>
      </listItem>
      <listItem>
        <para>Calls <legacyBold>SQLBulkOperations</legacyBold> or <legacyBold>SQLSetPos</legacyBold>. The driver discovers that a length/indicator buffer contains the result of the SQL_LEN_DATA_AT_EXEC(<legacyItalic>length</legacyItalic>) macro and returns SQL_NEED_DATA as the return value of the function.</para>
      </listItem>
      <listItem>
        <para>Calls <legacyBold>SQLParamData</legacyBold> in response to the SQL_NEED_DATA return value. If long data needs to be sent, <legacyBold>SQLParamData</legacyBold> returns SQL_NEED_DATA. In the buffer pointed to by the <legacyItalic>ValuePtrPtr</legacyItalic> argument, the driver returns the unique value that the application placed in the rowset buffer. If there is more than one data-at-execution column, the application uses this value to determine which column to send data for; the driver is not required to request data for data-at-execution columns in any particular order.</para>
      </listItem>
      <listItem>
        <para>Calls <legacyBold>SQLPutData</legacyBold> to send the column data to the driver. If the column data does not fit in a single buffer, as is often the case with long data, the application calls <legacyBold>SQLPutData</legacyBold> repeatedly to send the data in parts; it is up to the driver and data source to reassemble the data. If the application passes null-terminated string data, the driver or data source must remove the null-termination character as part of the reassembly process.</para>
      </listItem>
      <listItem>
        <para>Calls <legacyBold>SQLParamData</legacyBold> again to indicate that it has sent all of the data for the column. If there are any data-at-execution columns for which data has not been sent, the driver returns SQL_NEED_DATA and the unique value for the next data-at-execution column; the application returns to step 5. If data has been sent for all data-at-execution columns, the data for the row is sent to the data source. <legacyBold>SQLParamData</legacyBold> then returns SQL_SUCCESS or SQL_SUCCESS_WITH_INFO and can return any SQLSTATE that <legacyBold>SQLBulkOperations</legacyBold> or <legacyBold>SQLSetPos</legacyBold> can return.</para>
      </listItem>
    </list>
    <para>After <legacyBold>SQLBulkOperations</legacyBold> or <legacyBold>SQLSetPos</legacyBold> returns SQL_NEED_DATA and before data has been completely sent for the last data-at-execution column, the statement is in a Need Data state. In this state, the application can call only <legacyBold>SQLPutData</legacyBold>, <legacyBold>SQLParamData</legacyBold>, <legacyBold>SQLCancel</legacyBold>, <legacyBold>SQLGetDiagField</legacyBold>, or <legacyBold>SQLGetDiagRec</legacyBold>; all other functions return SQLSTATE HY010 (Function sequence error). Calling <legacyBold>SQLCancel</legacyBold> cancels execution of the statement and returns it to its previous state. For more information, see <legacyLink xlink:href="15088dbe-896f-4296-b397-02bb3d0ac0fb">Appendix B: ODBC State Transition Tables</legacyLink>.</para>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>