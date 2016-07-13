---
title: ODBC 64-Bit Information
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ed9851ce-44ee-4c8e-b626-1d0b52da30fe
manager:jhubbard
translation.priority.ht: 
  - en-gb
---
# ODBC 64-Bit Information
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Beginning with Windows Server 2003, Microsoft operating systems have supported the 64-bit ODBC libraries. The ODBC headers and libraries first shipped with MDAC 2.7 SDK contain changes to allow programmers to easily write code for the new 64 bit platforms. By ensuring that your code uses the ODBC defined types listed below, you can compile the same source code both for 64-bit and 32-bit platforms based on the <legacyBold>_WIN64</legacyBold> or <legacyBold>WIN32</legacyBold> macros.</para>
    <para>There are several points to keep in mind when programming for a 64-bit processor:   </para>
    <list class="bullet">
      <listItem>
        <para>Although the size of a pointer has changed from 4 bytes to 8 bytes, integers and longs are still 4 byte values. The types <legacyBold>INT64</legacyBold> and <legacyBold>UINT64</legacyBold> have been defined for 8 byte integers. The new ODBC types <legacyBold>SQLLEN</legacyBold> and <legacyBold>SQLULEN</legacyBold> are defined in the ODBC header file as <legacyBold>INT64</legacyBold> and <legacyBold>UINT64</legacyBold> when <legacyBold>_WIN64</legacyBold> has been defined.</para>
      </listItem>
      <listItem>
        <para>Several functions in ODBC are declared as taking a pointer parameter. In 32-bit ODBC, parameters defined as pointers were frequently used to pass either an integer value or a pointer to a buffer depending on the context of the call. This was, of course, possible due to the fact that pointers and integers had the same size. In 64-bit Windows, this is not the case.</para>
      </listItem>
      <listItem>
        <para>Some ODBC functions that were previously defined with <legacyBold>SQLINTEGER</legacyBold> and <legacyBold>SQLUINTEGER</legacyBold> parameters have been changed where appropriate to use the new <legacyBold>SQLLEN</legacyBold> and <legacyBold>SQLULEN</legacyBold> typedefs. These changes are listed in the next section, Function Declaration Changes.</para>
      </listItem>
      <listItem>
        <para>Some of the descriptor fields that can be set through the various <legacyBold>SQLSet</legacyBold> and <legacyBold>SQLGet</legacyBold> functions have been changed to accommodate 64-bit values while others are still 32-bit values. Make sure that you use the appropriate sized variable when setting and retrieving these fields. Specifics of which descriptor fields have changed are listed under Function Declaration Changes.</para>
      </listItem>
    </list>
  </introduction>
  <section>
    <title>Function Declaration Changes</title>
    <content>
      <para>The following function signatures have changed for 64-bit programming. The items in bold text are the specific parameters that are different.</para>
      <code>SQLBindCol (SQLHSTMT StatementHandle, SQLUSMALLINT ColumnNumber,
   SQLSMALLINT TargetType, SQLPOINTER TargetValuePtr, <codeFeaturedElement>SQLLEN BufferLength,</codeFeaturedElement>
<codeFeaturedElement>   SQLLEN * StrLen_or_Ind</codeFeaturedElement>);

SQLBindParam (SQLHSTMT StatementHandle, SQLUSMALLINT ParameterNumber,
   SQLSMALLINT ValueType, SQLSMALLINT ParameterType, 
   <codeFeaturedElement>SQLULEN ColumnSize</codeFeaturedElement>, SQLSMALLINT DecimalDigits, 
   SQLPOINTER ParameterValuePtr, <codeFeaturedElement>SQLLEN *StrLen_or_Ind</codeFeaturedElement>);

SQLBindParameter (SQLHSTMT StatementHandle, SQLUSMALLINT ParameterNumber, 
   SQLSMALLINT InputOutputType, SQLSMALLINT ValueType, 
   SQLSMALLINT ParameterType, <codeFeaturedElement>SQLULEN ColumnSize</codeFeaturedElement>, SQLSMALLINT DecimalDigits, 
   SQLPOINTER ParameterValuePtr, <codeFeaturedElement>SQLLEN BufferLength, SQLLEN *StrLen_or_IndPtr</codeFeaturedElement>);

SQLColAttribute (SQLHSTMT StatementHandle, SQLUSMALLINT ColumnNumber,
    SQLUSMALLINT FieldIdentifier, SQLPOINTER CharacterAttributePtr, 
   SQLSMALLINT BufferLength, SQLSMALLINT * StringLengthPtr, 
   <codeFeaturedElement>SQLLEN* NumericAttributePtr</codeFeaturedElement>)

SQLColAttributes (SQLHSTMT hstmt, SQLUSMALLINT icol, 
   SQLUSMALLINT fDescType, SQLPOINTER rgbDesc, 
   SQLSMALLINT cbDescMax, SQLSMALLINT *pcbDesc, <codeFeaturedElement>SQLLEN * pfDesc</codeFeaturedElement>);

SQLDescribeCol (SQLHSTMT StatementHandle, SQLUSMALLINT ColumnNumber, 
   SQLCHAR *ColumnName, SQLSMALLINT BufferLength, 
   SQLSMALLINT *NameLengthPtr, SQLSMALLINT *DataTypePtr, <codeFeaturedElement>SQLULEN *ColumnSizePtr</codeFeaturedElement>, 
   SQLSMALLINT *DecimalDigitsPtr, SQLSMALLINT *NullablePtr);

SQLDescribeParam (SQLHSTMT StatementHandle, SQLUSMALLINT ParameterNumber, 
   SQLSMALLINT *DataTypePtr, <codeFeaturedElement>SQLULEN *ParameterSizePtr</codeFeaturedElement>, SQLSMALLINT *DecimalDigitsPtr, 
   SQLSMALLINT *NullablePtr);

SQLExtendedFetch(SQLHSTMT StatementHandle, SQLUSMALLINT FetchOrientation, <codeFeaturedElement>SQLLEN FetchOffset</codeFeaturedElement>, 
   <codeFeaturedElement>SQLULEN * RowCountPtr</codeFeaturedElement>, SQLUSMALLINT * RowStatusArray);

SQLFetchScroll (SQLHSTMT StatementHandle, SQLSMALLINT FetchOrientation, 
   <codeFeaturedElement>SQLLEN FetchOffset</codeFeaturedElement>);

SQLGetData (SQLHSTMT StatementHandle, SQLUSMALLINT ColumnNumber, 
   SQLSMALLINT TargetType, SQLPOINTER TargetValuePtr, <codeFeaturedElement>SQLLEN BufferLength, </codeFeaturedElement>
<codeFeaturedElement>   SQLLEN *StrLen_or_Ind</codeFeaturedElement>);

SQLGetDescRec (SQLHDESC DescriptorHandle, SQLSMALLINT RecNumber, 
   SQLCHAR *Name, SQLSMALLINT BufferLength, 
   SQLSMALLINT *StringLengthPtr, SQLSMALLINT *TypePtr, 
   SQLSMALLINT *SubTypePtr, <codeFeaturedElement>SQLLEN *LengthPtr</codeFeaturedElement>, 
   SQLSMALLINT *PrecisionPtr, SQLSMALLINT *ScalePtr, 
   SQLSMALLINT *NullablePtr);

SQLParamOptions(SQLHSTMT hstmt, <codeFeaturedElement>SQLULEN crow, SQLULEN * pirow</codeFeaturedElement>);

SQLPutData (SQLHSTMT StatementHandle, SQLPOINTER DataPtr, 
   <codeFeaturedElement>SQLLEN StrLen_or_Ind</codeFeaturedElement>);

SQLRowCount (SQLHSTMT StatementHandle, <codeFeaturedElement>SQLLEN* RowCountPtr</codeFeaturedElement>);

SQLSetConnectOption(SQLHDBC ConnectHandle, SQLUSMALLINT Option, 
   <codeFeaturedElement>SQLULEN Value</codeFeaturedElement>);

SQLSetPos (SQLHSTMT StatementHandle, <codeFeaturedElement>SQLSETPOSIROW RowNumber</codeFeaturedElement>, SQLUSMALLINT Operation,
   SQLUSMALLINT LockType);

SQLSetParam (SQLHSTMT StatementHandle, SQLUSMALLINT ParameterNumber, 
   SQLSMALLINT ValueType, SQLSMALLINT ParameterType, 
   <codeFeaturedElement>SQLULEN LengthPrecision</codeFeaturedElement>, SQLSMALLINT ParameterScale, 
   SQLPOINTER ParameterValue, <codeFeaturedElement>SQLLEN *StrLen_or_Ind</codeFeaturedElement>);

SQLSetDescRec (SQLHDESC DescriptorHandle, SQLSMALLINT RecNumber, 
   SQLSMALLINT Type, SQLSMALLINT SubType, <codeFeaturedElement>SQLLEN Length</codeFeaturedElement>, 
   SQLSMALLINT Precision, SQLSMALLINT Scale, SQLPOINTER DataPtr, 
   <codeFeaturedElement>SQLLEN *StringLengthPtr</codeFeaturedElement>,<codeFeaturedElement> SQLLEN *IndicatorPtr</codeFeaturedElement>);

SQLSetScrollOptions (SQLHSTMT hstmt, SQLUSMALLINT fConcurrency, 
   <codeFeaturedElement>SQLLEN crowKeyset</codeFeaturedElement>, SQLUSMALLINT crowRowset);

SQLSetStmtOption (SQLHSTMT StatementHandle, SQLUSMALLINT Option, 
   <codeFeaturedElement>SQLULEN Value</codeFeaturedElement>);</code>
    </content>
  </section>
  <section>
    <title>Changes in SQL Data Types</title>
    <content>
      <para>The following four SQL types are still supported on 32-bit only; they are not defined for 64-bit compilers. These types are no longer used for any parameters in MDAC 2.7; use of these types will cause compiler failures on 64-bit platforms.</para>
      <code>#ifdef WIN32 
typedef SQLULEN SQLROWCOUNT; 
typedef SQLULEN SQLROWSETSIZE; 
typedef SQLULEN SQLTRANSID; 
typedef SQLLEN SQLROWOFFSET; 
#endif</code>
      <para>The definition of SQLSETPOSIROW has changed for both 32-bit and 64-bit compilers:</para>
      <code>#ifdef _WIN64 
typedef UINT64 SQLSETPOSIROW; 
#else 
#define SQLSETPOSIROW SQLUSMALLINT 
#endif</code>
      <para>The definitions of SQLLEN and SQLULEN have changed for 64-bit compilers:</para>
      <code>#ifdef _WIN64 
typedef INT64 SQLLEN; 
typedef UINT64 SQLULEN; 
#else 
#define SQLLEN SQLINTEGER 
#define SQLULEN SQLUINTEGER 
#endif</code>
      <para>Although SQL_C_BOOKMARK is deprecated in ODBC 3.0, for 64-bit compilers on 2.0 clients, this value has changed:</para>
      <code>#ifdef _WIN64 
#define SQL_C_BOOKMARK SQL_C_UBIGINT 
#else 
#define SQL_C_BOOKMARK SQL_C_ULONG 
#endif</code>
      <para>The BOOKMARK type is defined differently in the newer headers:</para>
      <code>typedef SQLULEN BOOKMARK;</code>
    </content>
  </section>
  <section>
    <title>Values Returned from ODBC API Calls Through Pointers</title>
    <content>
      <para>The following ODBC function calls take as an input parameter a pointer to a buffer in which data is returned from the driver. The context and meaning of the data returned is determined by other input parameters for the functions. In some cases, these methods may now return 64-bit (8-byte integer) values instead of the typical 32-bit (4-byte) integer values. These cases are as follows:</para>
      <para>
        <embeddedLabel>SQLColAttribute</embeddedLabel>
      </para>
      <para>When the <parameterReference>FieldIdentifier</parameterReference> parameter has one of the following values, a 64-bit value is returned in *<parameterReference>NumericAttribute</parameterReference>:</para>
      <para>SQL_DESC_AUTO_UNIQUE_VALUE</para>
      <para>SQL_DESC_CASE_SENSITIVE</para>
      <para>SQL_DESC_CONCISE_TYPE</para>
      <para>SQL_DESC_COUNT</para>
      <para>SQL_DESC_DISPLAY_SIZE</para>
      <para>SQL_DESC_FIXED_PREC_SCALE</para>
      <para>SQL_DESC_LENGTH</para>
      <para>SQL_DESC_NULLABLE</para>
      <para>SQL_DESC_NUM_PREC_RADIX</para>
      <para>SQL_DESC_OCTET_LENGTH</para>
      <para>SQL_DESC_PRECISION</para>
      <para>SQL_DESC_SCALE</para>
      <para>SQL_DESC_SEARCHABLE</para>
      <para>SQL_DESC_TYPE</para>
      <para>SQL_DESC_UNNAMED</para>
      <para>SQL_DESC_UNSIGNED</para>
      <para>SQL_DESC_UPDATABLE</para>
      <para>
        <embeddedLabel>SQLColAttributes</embeddedLabel>
      </para>
      <para>When the <parameterReference>fDescType</parameterReference> parameter has one of the following values, a 64-bit value is returned in *<parameterReference>pfDesc</parameterReference>:</para>
      <para>SQL_COLUMN_COUNT</para>
      <para>SQL_COLUMN_DISPLAY_SIZE</para>
      <para>SQL_COLUMN_LENGTH</para>
      <para>SQL_DESC_AUTO_UNIQUE_VALUE</para>
      <para>SQL_DESC_CASE_SENSITIVE</para>
      <para>SQL_DESC_CONCISE_TYPE</para>
      <para>SQL_DESC_FIXED_PREC_SCALE</para>
      <para>SQL_DESC_SEARCHABLE</para>
      <para>SQL_DESC_UNSIGNED</para>
      <para>SQL_DESC_UPDATABLE</para>
      <para>
        <embeddedLabel>SQLGetConnectAttr</embeddedLabel>
      </para>
      <para>When the <parameterReference>Attribute</parameterReference> parameter has one of the following values, a 64-bit value is returned in <parameterReference>Value</parameterReference>:</para>
      <para>SQL_ATTR_ASYNC_ENABLE</para>
      <para>SQL_ATTR_ENLIST_IN_DTC</para>
      <para>SQL_ATTR_ODBC_CURSORS</para>
      <para>SQL_ATTR_QUIET_MODE</para>
      <para>
        <embeddedLabel>SQLGetConnectOption</embeddedLabel>
      </para>
      <para>When the <parameterReference>Attribute</parameterReference> parameter has one of the following values, a 64-bit value is returned in <parameterReference>Value</parameterReference>:</para>
      <para>SQL_ATTR_QUIET_MODE</para>
      <para>
        <embeddedLabel>SQLGetDescField</embeddedLabel>
      </para>
      <para>When the <parameterReference>FieldIdentifier</parameterReference> parameter has one of the following values, a 64-bit value is returned in *<parameterReference>ValuePtr</parameterReference>:</para>
      <para>SQL_DESC_ARRAY_SIZE</para>
      <para>SQL_DESC_ARRAY_STATUS_PTR</para>
      <para>SQL_DESC_BIND_OFFSET_PTR</para>
      <para>SQL_DESC_DATA_PTR</para>
      <para>SQL_DESC_DISPLAY_SIZE</para>
      <para>SQL_DESC_INDICATOR_PTR</para>
      <para>SQL_DESC_LENGTH</para>
      <para>SQL_DESC_OCTET_LENGTH</para>
      <para>SQL_DESC_OCTET_LENGTH_PTR</para>
      <para>SQL_DESC_ROWS_PROCESSED_PTR</para>
      <para>
        <embeddedLabel>SQLGetDiagField</embeddedLabel>
      </para>
      <para>When the <parameterReference>DiagIdentifier</parameterReference> parameter has one of the following values, a 64-bit value is returned in *<parameterReference>DiagInfoPtr</parameterReference>:</para>
      <para>SQL_DIAG_CURSOR_ROW_COUNT</para>
      <para>SQL_DIAG_ROW_COUNT</para>
      <para>SQL_DIAG_ROW_NUMBER</para>
      <para>
        <embeddedLabel>SQLGetInfo</embeddedLabel>
      </para>
      <para>When the <parameterReference>InfoType</parameterReference> parameter has one of the following values, a 64-bit value is returned in *<parameterReference>InfoValuePtr</parameterReference>:</para>
      <para>SQL_DRIVER_HDBC</para>
      <para>SQL_DRIVER_HENV</para>
      <para>SQL_DRIVER_HLIB</para>
      <para>When <parameterReference>InfoType</parameterReference> has either of the following 2 values *<parameterReference>InfoValuePtr</parameterReference> is 64-bits on both input and ouput:</para>
      <para>SQL_DRIVER_HDESC</para>
      <para>SQL_DRIVER_HSTMT</para>
      <para>
        <embeddedLabel>SQLGetStmtAttr</embeddedLabel>
      </para>
      <para>When the <parameterReference>Attribute</parameterReference> parameter has one of the following values, a 64-bit value is returned in *<parameterReference>ValuePtr</parameterReference>:</para>
      <para>SQL_ATTR_APP_PARAM_DESC</para>
      <para>SQL_ATTR_APP_ROW_DESC</para>
      <para>SQL_ATTR_ASYNC_ENABLE</para>
      <para>SQL_ATTR_CONCURRENCY</para>
      <para>SQL_ATTR_CURSOR_SCROLLABLE</para>
      <para>SQL_ATTR_CURSOR_SENSITIVITY</para>
      <para>SQL_ATTR_CURSOR_TYPE</para>
      <para>SQL_ATTR_ENABLE_AUTO_IPD</para>
      <para>SQL_ATTR_FETCH_BOOKMARK_PTR</para>
      <para>SQL_ATTR_ROWS_FETCHED_PTR</para>
      <para>SQL_ATTR_IMP_PARAM_DESC</para>
      <para>SQL_ATTR_IMP_ROW_DESC</para>
      <para>SQL_ATTR_KEYSET_SIZE</para>
      <para>SQL_ATTR_MAX_LENGTH</para>
      <para>SQL_ATTR_MAX_ROWS</para>
      <para>SQL_ATTR_METADATA_ID</para>
      <para>SQL_ATTR_NOSCAN</para>
      <para>SQL_ATTR_PARAM_BIND_OFFSET_PTR</para>
      <para>SQL_ATTR_PARAM_BIND_TYPE</para>
      <para>SQL_ATTR_PARAM_OPERATION_PTR</para>
      <para>SQL_ATTR_PARAM_STATUS_PTR</para>
      <para>SQL_ATTR_PARAMS_PROCESSED_PTR</para>
      <para>SQL_ATTR_PARAMSET_SIZE</para>
      <para>SQL_ATTR_QUERY_TIMEOUT</para>
      <para>SQL_ATTR_RETRIEVE_DATA</para>
      <para>SQL_ATTR_ROW_ARRAY_SIZE</para>
      <para>SQL_ATTR_ROW_BIND_OFFSET_PTR</para>
      <para>SQL_ATTR_ROW_NUMBER</para>
      <para>SQL_ATTR_ROW_OPERATION_PTR</para>
      <para>SQL_ATTR_ROW_STATUS_PTR</para>
      <para>SQL_ATTR_SIMULATE_CURSOR</para>
      <para>SQL_ATTR_USE_BOOKMARKS</para>
      <para>
        <embeddedLabel>SQLGetStmtOption</embeddedLabel>
      </para>
      <para>When the <parameterReference>Option</parameterReference> parameter has one of the following values, a 64-bit value is returned in *<parameterReference>Value</parameterReference>:</para>
      <para>SQL_KEYSET_SIZE</para>
      <para>SQL_MAX_LENGTH</para>
      <para>SQL_MAX_ROWS</para>
      <para>SQL_ROWSET_SIZE</para>
      <para>
        <embeddedLabel>SQLSetConnectAttr</embeddedLabel>
      </para>
      <para>When the <parameterReference>Attribute</parameterReference> parameter has one of the following values, a 64-bit value is passed in <parameterReference>Value</parameterReference>:</para>
      <para>SQL_ATTR_ASYNC_ENABLE</para>
      <para>SQL_ATTR_ENLIST_IN_DTC</para>
      <para>SQL_ATTR_ODBC_CURSORS</para>
      <para>SQL_ATTR_QUIET_MODE</para>
      <para>
        <embeddedLabel>SQLSetConnectOption</embeddedLabel>
      </para>
      <para>When the <parameterReference>Attribute</parameterReference> parameter has one of the following values, a 64-bit value is passed in <parameterReference>Value</parameterReference>:</para>
      <para>SQL_ATTR_QUIET_MODE</para>
      <para>
        <embeddedLabel>SQLSetDescField</embeddedLabel>
      </para>
      <para>When the <parameterReference>FieldIdentifier</parameterReference> parameter has one of the following values, a 64-bit value is passed in *<parameterReference>ValuePtr</parameterReference>:</para>
      <para>SQL_DESC_ARRAY_SIZE</para>
      <para>SQL_DESC_ARRAY_STATUS_PTR</para>
      <para>SQL_DESC_BIND_OFFSET_PTR</para>
      <para>SQL_DESC_DATA_PTR</para>
      <para>SQL_DESC_DISPLAY_SIZE</para>
      <para>SQL_DESC_INDICATOR_PTR</para>
      <para>SQL_DESC_LENGTH</para>
      <para>SQL_DESC_OCTET_LENGTH</para>
      <para>SQL_DESC_OCTET_LENGTH_PTR</para>
      <para>SQL_DESC_ROWS_PROCESSED_PTR</para>
      <para>
        <embeddedLabel>SQLSetStmtAttr</embeddedLabel>
      </para>
      <para>When the <parameterReference>Attribute</parameterReference> parameter has one of the following values, a 64-bit value is passed in *<parameterReference>ValuePtr</parameterReference>:</para>
      <para>SQL_ATTR_APP_PARAM_DESC</para>
      <para>SQL_ATTR_APP_ROW_DESC</para>
      <para>SQL_ATTR_ASYNC_ENABLE</para>
      <para>SQL_ATTR_CONCURRENCY</para>
      <para>SQL_ATTR_CURSOR_SCROLLABLE</para>
      <para>SQL_ATTR_CURSOR_SENSITIVITY</para>
      <para>SQL_ATTR_CURSOR_TYPE</para>
      <para>SQL_ATTR_ENABLE_AUTO_IPD</para>
      <para>SQL_ATTR_FETCH_BOOKMARK_PTR</para>
      <para>SQL_ATTR_IMP_PARAM_DESC</para>
      <para>SQL_ATTR_IMP_ROW_DESC</para>
      <para>SQL_ATTR_KEYSET_SIZE</para>
      <para>SQL_ATTR_MAX_LENGTH</para>
      <para>SQL_ATTR_MAX_ROWS</para>
      <para>SQL_ATTR_METADATA_ID</para>
      <para>SQL_ATTR_NOSCAN</para>
      <para>SQL_ATTR_PARAM_BIND_OFFSET_PTR</para>
      <para>SQL_ATTR_PARAM_BIND_TYPE</para>
      <para>SQL_ATTR_PARAM_OPERATION_PTR</para>
      <para>SQL_ATTR_PARAM_STATUS_PTR</para>
      <para>SQL_ATTR_PARAMS_PROCESSED_PTR</para>
      <para>SQL_ATTR_PARAMSET_SIZE</para>
      <para>SQL_ATTR_QUERY_TIMEOUT</para>
      <para>SQL_ATTR_RETRIEVE_DATA</para>
      <para>SQL_ATTR_ROW_ARRAY_SIZE</para>
      <para>SQL_ATTR_ROW_BIND_OFFSET_PTR</para>
      <para>SQL_ATTR_ROW_NUMBER</para>
      <para>SQL_ATTR_ROW_OPERATION_PTR</para>
      <para>SQL_ATTR_ROW_STATUS_PTR</para>
      <para>SQL_ATTR_ROWS_FETCHED_PTR</para>
      <para>SQL_ATTR_SIMULATE_CURSOR</para>
      <para>SQL_ATTR_USE_BOOKMARKS</para>
      <para>
        <embeddedLabel>SQLSetStmtOption</embeddedLabel>
      </para>
      <para>When the <parameterReference>Option</parameterReference> parameter has one of the following values, a 64-bit value is passed in *<parameterReference>Value</parameterReference>:</para>
      <para>SQL_KEYSET_SIZE</para>
      <para>SQL_MAX_LENGTH</para>
      <para>SQL_MAX_ROWS</para>
      <para>SQL_ROWSET_SIZE</para>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="dbe0b5a3-d7fa-440d-80b4-6cc00de159dc">Introduction to ODBC</link>
</relatedTopics>
</developerConceptualDocument>