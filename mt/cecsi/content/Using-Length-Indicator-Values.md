---
title: Using Length/Indicator Values
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 849792f1-cb1e-4bc2-b568-c0aff0b66199
translation.priority.ht: 
  - en-gb
---
# Using Length/Indicator Values
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The length/indicator buffer is used to pass the byte length of the data in the data buffer or a special indicator such as SQL_NULL_DATA, which indicates that the data is NULL. Depending on the function in which it is used, a length/indicator buffer is defined to be an SQLINTEGER or an SQLSMALLINT. Therefore, a single argument is needed to describe it. If the data buffer is a nondeferred input buffer, this argument contains the byte length of the data itself or an indicator value. It is often named <legacyItalic>StrLen_or_Ind</legacyItalic> or a similar name. For example, the following code calls <legacyBold>SQLPutData</legacyBold> to pass a buffer full of data; the byte length (<legacyItalic>ValueLen</legacyItalic>) is passed directly because the data buffer (<legacyItalic>ValuePtr</legacyItalic>) is an input buffer.</para>
    <code>SQLCHAR      ValuePtr[50];
SQLINTEGER   ValueLen;

// Call local function to place data in ValuePtr. In ValueLen, return the
// number of bytes of data placed in ValuePtr. If there is not enough
// data, this will be less than 50.
FillBuffer(ValuePtr, sizeof(ValuePtr), &amp;ValueLen);

// Call SQLPutData to send the data to the driver.
SQLPutData(hstmt, ValuePtr, ValueLen);</code>
    <para>If the data buffer is a deferred input buffer, a nondeferred output buffer, or an output buffer, the argument contains the address of the length/indicator buffer. It is often named <legacyItalic>StrLen_or_IndPtr</legacyItalic> or a similar name. For example, the following code calls <legacyBold>SQLGetData</legacyBold> to retrieve a buffer full of data; the byte length is returned to the application in the length/indicator buffer (<legacyItalic>ValueLenOrInd</legacyItalic>), whose address is passed to <legacyBold>SQLGetData</legacyBold> because the corresponding data buffer (<legacyItalic>ValuePtr</legacyItalic>) is a nondeferred output buffer.</para>
    <code>SQLCHAR      ValuePtr[50];
SQLINTEGER   ValueLenOrInd;
SQLGetData(hstmt, 1, SQL_C_CHAR, ValuePtr, sizeof(ValuePtr), &amp;ValueLenOrInd);</code>
    <para>Unless it is specifically prohibited, a length/indicator buffer argument can be 0 (if nondeferred input) or a null pointer (if output or deferred input). For input buffers, this causes the driver to ignore the byte length of the data. This returns an error when passing variable-length data but is common when passing non-null, fixed-length data, because neither a length nor an indicator value is needed. For output buffers, this causes the driver to not return the byte length of the data or an indicator value. This is an error if the data returned by the driver is NULL but is common when retrieving fixed-length, non-nullable data, because neither a length nor an indicator value is needed.</para>
    <para>As when the address of a deferred data buffer is passed to the driver, the address of a deferred length/indicator buffer must remain valid until the buffer is unbound.</para>
    <para>The following lengths are valid as length/indicator values:  </para>
    <list class="bullet">
      <listItem>
        <para>             <legacyItalic>n</legacyItalic>, where <legacyItalic>n</legacyItalic> &gt; 0.</para>
      </listItem>
      <listItem>
        <para>0.</para>
      </listItem>
      <listItem>
        <para>SQL_NTS. A string sent to the driver in the corresponding data buffer is null-terminated; this is a convenient way for C programmers to pass strings without having to calculate their byte length. This value is legal only when the application sends data to the driver. When the driver returns data to the application, it always returns the actual byte length of the data.</para>
      </listItem>
    </list>
    <para>The following values are valid as length/indicator values. SQL_NULL_DATA is stored in the SQL_DESC_INDICATOR_PTR descriptor field; all other values are stored in the SQL_DESC_OCTET_LENGTH_PTR descriptor field.  </para>
    <list class="bullet">
      <listItem>
        <para>SQL_NULL_DATA. The data is a NULL data value, and the value in the corresponding data buffer is ignored. This value is legal only for SQL data sent to or retrieved from the driver.</para>
      </listItem>
      <listItem>
        <para>SQL_DATA_AT_EXEC. The data buffer does not contain any data. Instead, the data will be sent with <legacyBold>SQLPutData</legacyBold> when the statement is executed or when <legacyBold>SQLBulkOperations</legacyBold> or <legacyBold>SQLSetPos</legacyBold> is called. This value is legal only for SQL data sent to the driver. For more information, see <legacyLink xlink:href="38349d4b-be03-46f9-9d6a-e50dd144e225">SQLBindParameter</legacyLink>, <legacyLink xlink:href="7029d0da-b0f2-44e6-9114-50bd96f47196">SQLBulkOperations</legacyLink>, and <legacyLink xlink:href="80190ee7-ae3b-45e5-92a9-693eb558f322">SQLSetPos</legacyLink>.</para>
      </listItem>
      <listItem>
        <para>Result of the SQL_LEN_DATA_AT_EXEC(<legacyItalic>length</legacyItalic>) macro. This value is similar to SQL_DATA_AT_EXEC. For more information, see <legacyLink xlink:href="ea989084-a8e6-4737-892e-9ec99dd49caf">Sending Long Data</legacyLink>.</para>
      </listItem>
      <listItem>
        <para>SQL_NO_TOTAL. The driver cannot determine the number of bytes of long data still available to return in an output buffer. This value is legal only for SQL data retrieved from the driver.</para>
      </listItem>
      <listItem>
        <para>SQL_DEFAULT_PARAM. A procedure is to use the default value of an input parameter in a procedure instead of the value in the corresponding data buffer.</para>
      </listItem>
      <listItem>
        <para>SQL_COLUMN_IGNORE. <legacyBold>SQLBulkOperations</legacyBold> or<legacyBold> SQLSetPos</legacyBold> is to ignore the value in the data buffer. When updating a row of data by a call to <legacyBold>SQLBulkOperations</legacyBold> or<legacyBold> SQLSetPos,</legacyBold> the column value is not changed. When inserting a new row of data by a call to <legacyBold>SQLBulkOperations</legacyBold>, the column value is set to its default or, if the column does not have a default, to NULL.</para>
      </listItem>
    </list>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>