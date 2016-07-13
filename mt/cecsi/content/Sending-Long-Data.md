---
title: Sending Long Data
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ea989084-a8e6-4737-892e-9ec99dd49caf
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Sending Long Data
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>DBMSs define <legacyItalic>long data</legacyItalic> as any character or binary data over a certain size, such as 254 characters. It might not be possible to store an entire item of long data in memory, such as when the item represents a long text document or a bitmap. Because such data cannot be stored in a single buffer, the data source sends it to the driver in parts with <legacyBold>SQLPutData</legacyBold> when the statement is executed. Parameters for which data is sent at execution time are known as <legacyItalic>data-at-execution parameters</legacyItalic>.</para>
    <alert class="note">
      <para>An application can actually send any type of data at execution time with <legacyBold>SQLPutData</legacyBold>, although only character and binary data can be sent in parts. However, if the data is small enough to fit in a single buffer, there is generally no reason to use <legacyBold>SQLPutData</legacyBold>. It is much easier to bind the buffer and let the driver retrieve the data from the buffer.</para>
    </alert>
    <para>To send data at execution time, the application performs the following actions:  </para>
    <list class="ordered">
      <listItem>
        <para>Passes a 32-bit value that identifies the parameter in the <legacyItalic>ParameterValuePtr</legacyItalic> argument in <legacyBold>SQLBindParameter</legacyBold> rather than passing the address of a buffer. This value is not analyzed by the driver. It will be returned to the application later, so it should mean something to the application. For example, it might be the number of the parameter or the handle of a file containing data.</para>
      </listItem>
      <listItem>
        <para>Passes the address of a length/indicator buffer in the <legacyItalic>StrLen_or_IndPtr</legacyItalic> argument of <legacyBold>SQLBindParameter</legacyBold>.</para>
      </listItem>
      <listItem>
        <para>Stores SQL_DATA_AT_EXEC or the result of the SQL_LEN_DATA_AT_EXEC(<legacyItalic>length</legacyItalic>) macro in the length/indicator buffer. Both of these values indicate to the driver that the data for the parameter will be sent with <legacyBold>SQLPutData</legacyBold>. SQL_LEN_DATA_AT_EXEC(<legacyItalic>length</legacyItalic>) is used when sending long data to a data source that needs to know how many bytes of long data will be sent so that it can preallocate space. To determine if a data source requires this value, the application calls <legacyBold>SQLGetInfo</legacyBold> with the SQL_NEED_LONG_DATA_LEN option. All drivers must support this macro; if the data source does not require the byte length, the driver can ignore it.</para>
      </listItem>
      <listItem>
        <para>Calls <legacyBold>SQLExecute</legacyBold> or <legacyBold>SQLExecDirect</legacyBold>. The driver discovers that a length/indicator buffer contains the value SQL_DATA_AT_EXEC or the result of the SQL_LEN_DATA_AT_EXEC(<legacyItalic>length</legacyItalic>) macro and returns SQL_NEED_DATA as the return value of the function.</para>
      </listItem>
      <listItem>
        <para>Calls <legacyBold>SQLParamData</legacyBold> in response to the SQL_NEED_DATA return value. If long data needs to be sent, <legacyBold>SQLParamData</legacyBold> returns SQL_NEED_DATA. In the buffer pointed to by the <legacyItalic>ValuePtrPtr</legacyItalic> argument, the driver returns the value that identifies the data-at-execution parameter. If there is more than one data-at-execution parameter, the application must use this value to determine which parameter to send data for; the driver is not required to request data for data-at-execution parameters in any particular order.</para>
      </listItem>
      <listItem>
        <para>Calls <legacyBold>SQLPutData</legacyBold> to send the parameter data to the driver. If the parameter data does not fit into a single buffer, as is often the case with long data, the application calls <legacyBold>SQLPutData</legacyBold> repeatedly to send the data in parts; it is up to the driver and data source to reassemble the data. If the application passes null-terminated string data, the driver or data source must remove the null-termination character as part of the reassembly process.</para>
      </listItem>
      <listItem>
        <para>Calls <legacyBold>SQLParamData</legacyBold> again to indicate that it has sent all of the data for the parameter. If there are any data-at-execution parameters for which data has not been sent, the driver returns SQL_NEED_DATA and the value that identifies the next parameter; the application returns to step 6. If data has been sent for all data-at-execution parameters, the statement is executed. <legacyBold>SQLParamData</legacyBold> returns SQL_SUCCESS or SQL_SUCCESS_WITH_INFO and can return any return value or diagnostic that <legacyBold>SQLExecute</legacyBold> or <legacyBold>SQLExecDirect</legacyBold> can return.</para>
      </listItem>
    </list>
    <para>After <legacyBold>SQLExecute</legacyBold> or <legacyBold>SQLExecDirect</legacyBold> returns SQL_NEED_DATA and before data has been completely sent for the last data-at-execution parameter, the statement is in a Need Data state. While a statement is in a Need Data state, the application can call only <legacyBold>SQLPutData</legacyBold>, <legacyBold>SQLParamData</legacyBold>, <legacyBold>SQLCancel</legacyBold>,<legacyBold> SQLGetDiagField</legacyBold>, or<legacyBold> SQLGetDiagRec</legacyBold>; all other functions return SQLSTATE HY010 (Function sequence error). Calling <legacyBold>SQLCancel</legacyBold> cancels execution of the statement and returns it to its previous state. For more information, see <legacyLink xlink:href="15088dbe-896f-4296-b397-02bb3d0ac0fb">Appendix B: ODBC State Transition Tables</legacyLink>.</para>
    <para>For an example of sending data at execution time, see the <legacyLink xlink:href="9a60f004-1477-4c54-a20c-7378e1116713">SQLPutData</legacyLink> function description.</para>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>