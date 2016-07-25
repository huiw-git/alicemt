---
title: "SQLGetInfo Returned Values for Text Files"
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 739a9d72-26aa-42dd-b9fd-76c679976d09
caps.latest.revision: 5
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# SQLGetInfo Returned Values for Text Files
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The following table lists the C-language #defines for the <legacyItalic>fInfoType</legacyItalic> argument and the corresponding values returned by <legacyBold>SQLGetInfo</legacyBold>. This information can be retrieved by passing the listed C-language #defines to <legacyBold>SQLGetInfo</legacyBold> in the <legacyItalic>fInfoType</legacyItalic> argument. For more information about the values returned by <legacyBold>SQLGetInfo</legacyBold>, see the <link xlink:href="b33c3c43-ae66-44a3-be17-9cd82624dd96">ODBC Programmer's Reference</link>.</para>
  </introduction>
  <section>
    <content>
      <alert class="note">
        <para>Where <legacyBold>SQLGetInfo</legacyBold> returns a 32-bit bitmask, a vertical bar (|) represents a bitwise OR.</para>
      </alert>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>InfoType</para>
            </TD>
            <TD>
              <para>Returned value</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>SQL_ACCESSIBLE_PROCEDURES</para>
            </TD>
            <TD>
              <para>"N" </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_ACCESSIBLE_TABLES</para>
            </TD>
            <TD>
              <para>"Y"</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_ACTIVE_ENVIRONMENTS</para>
            </TD>
            <TD>
              <para>0</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_AGGREGATE_FUNCTIONS</para>
            </TD>
            <TD>
              <para>All set</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_ALTER_DOMAIN</para>
            </TD>
            <TD>
              <para>0</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_ALTER_TABLE</para>
            </TD>
            <TD>
              <para>0 </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_ASYNC_MODE</para>
            </TD>
            <TD>
              <para>0</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_BATCH_ROW_COUNT</para>
            </TD>
            <TD>
              <para>0</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_BATCH_SUPPORT</para>
            </TD>
            <TD>
              <para>0</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_BOOKMARK_PERSISTENCE</para>
            </TD>
            <TD>
              <para>               Multiple values           </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_CATALOG_LOCATION</para>
            </TD>
            <TD>
              <para>SQL_QL_START </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_CATALOG_NAME</para>
            </TD>
            <TD>
              <para>"Y" </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_CATALOG_NAME_SEPARATOR</para>
            </TD>
            <TD>
              <para>"\" </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_CATALOG_TERM</para>
            </TD>
            <TD>
              <para>"Directory" </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_CATALOG_USAGE</para>
            </TD>
            <TD>
              <para>               Multiple values             </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_COLLATION_SEQ</para>
            </TD>
            <TD>
              <para>"" </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_COLUMN_ALIAS</para>
            </TD>
            <TD>
              <para>"Y"</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_CONCAT_NULL_BEHAVIOR</para>
            </TD>
            <TD>
              <para>SQL_CB_NON_NULL </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_CONVERT_BIGINT</para>
            </TD>
            <TD>
              <para>0 </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_CONVERT_BINARY</para>
            </TD>
            <TD>
              <para>               Multiple values             </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_CONVERT_BIT</para>
            </TD>
            <TD>
              <para>0 </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_CONVERT_CHAR</para>
            </TD>
            <TD>
              <para>               Multiple values             </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_CONVERT_DATE</para>
            </TD>
            <TD>
              <para>               Multiple values             </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_CONVERT_DECIMAL</para>
            </TD>
            <TD>
              <para>0 </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_CONVERT_DOUBLE</para>
            </TD>
            <TD>
              <para>               Multiple values             </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_CONVERT_FLOAT</para>
            </TD>
            <TD>
              <para>               Multiple values             </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_CONVERT_FUNCTIONS</para>
            </TD>
            <TD>
              <para>SQL_FN_CVT_CONVERT </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_CONVERT_INTEGER</para>
            </TD>
            <TD>
              <para>               Multiple values             </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_CONVERT_LONGVARBINARY</para>
            </TD>
            <TD>
              <para>               Multiple values             </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_CONVERT_LONGVARCHAR</para>
            </TD>
            <TD>
              <para>               Multiple values             </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_CONVERT_NUMERIC</para>
            </TD>
            <TD>
              <para>               Multiple values             </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_CONVERT_REAL</para>
            </TD>
            <TD>
              <para>               Multiple values             </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_CONVERT_SMALLINT</para>
            </TD>
            <TD>
              <para>               Multiple values             </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_CONVERT_TIME</para>
            </TD>
            <TD>
              <para>               Multiple values             </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_CONVERT_TIMESTAMP</para>
            </TD>
            <TD>
              <para>               Multiple values             </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_CONVERT_TINYINT</para>
            </TD>
            <TD>
              <para>               Multiple values             </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_CONVERT_VARBINARY</para>
            </TD>
            <TD>
              <para>               Multiple values             </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_CONVERT_VARCHAR</para>
            </TD>
            <TD>
              <para>               Multiple values             </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_CORRELATION_NAME</para>
            </TD>
            <TD>
              <para>SQL_CN_ANY </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_CREATE_ASSERTION</para>
            </TD>
            <TD>
              <para>0</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_CREATE_CHARACTER_SET</para>
            </TD>
            <TD>
              <para>0</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_CREATE_COLLATION</para>
            </TD>
            <TD>
              <para>0</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_CREATE_DOMAIN</para>
            </TD>
            <TD>
              <para>0</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_CREATE_SCHEMA</para>
            </TD>
            <TD>
              <para>0</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_CREATE_TABLE</para>
            </TD>
            <TD>
              <para>SQL_CT_CREATE_TABLE</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_CREATE_TRANSLATION</para>
            </TD>
            <TD>
              <para>0</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_CREATE_VIEW</para>
            </TD>
            <TD>
              <para>0</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_CURSOR_COMMIT_BEHAVIOR</para>
            </TD>
            <TD>
              <para>SQL_CB_CLOSE </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_CURSOR_ROLLBACK_BEHAVIOR</para>
            </TD>
            <TD>
              <para>SQL_CB_CLOSE </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_CURSOR_SENSITIVITY</para>
            </TD>
            <TD>
              <para>SQL_UNSPECIFIED </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_DATA_SOURCE_NAME</para>
            </TD>
            <TD>
              <para>The DSN from Odbc.ini, or "" if DRIVER keyword is used in Odbc.ini </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_DATA_SOURCE_READ_ONLY</para>
            </TD>
            <TD>
              <para>"Y" </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_DATABASE_NAME</para>
            </TD>
            <TD>
              <para>Current database directory</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_DATETIME_LITERALS</para>
            </TD>
            <TD>
              <para>0</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_DBMS_NAME</para>
            </TD>
            <TD>
              <para>"TEXT" </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_DBMS_VER</para>
            </TD>
            <TD>
              <para>ISAM: Text</para>
              <para>Version: 1.0</para>
              <para>Format of version number: 01.00.0000</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_DDL_INDEX</para>
            </TD>
            <TD>
              <para>0</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_DEFAULT_TXN_ISOLATION</para>
            </TD>
            <TD>
              <para>0 </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_DESCRIBE_PARAMETER</para>
            </TD>
            <TD>
              <para>0</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_DRIVER_HDBC</para>
            </TD>
            <TD>
              <para>Handled by the Driver Manager. </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_DRIVER_HENV</para>
            </TD>
            <TD>
              <para>Handled by the Driver Manager. </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_DRIVER_HLIB</para>
            </TD>
            <TD>
              <para>Handled by the Driver Manager. </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_DRIVER_HSTMT</para>
            </TD>
            <TD>
              <para>Handled by the Driver Manager. </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_DRIVER_NAME</para>
            </TD>
            <TD>
              <para>"OdbcJt32.dll" </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_DRIVER_ODBC_VER</para>
            </TD>
            <TD>
              <para>"3.51.0000" </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_DRIVER_VER</para>
            </TD>
            <TD>
              <para>"4.00.<legacyItalic>nnnn</legacyItalic>" (<legacyItalic>nnnn</legacyItalic> specifies the build date) </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_DROP_ASSERTION</para>
            </TD>
            <TD>
              <para>0</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_DROP_CHARACTER_SET</para>
            </TD>
            <TD>
              <para>0</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_DROP_COLLATION</para>
            </TD>
            <TD>
              <para>0</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_DROP_DOMAIN</para>
            </TD>
            <TD>
              <para>0</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_DROP_SCHEMA</para>
            </TD>
            <TD>
              <para>0</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_DROP_TABLE</para>
            </TD>
            <TD>
              <para>SQL_DT_DROP_TABLE</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_DROP_TRANSLATION</para>
            </TD>
            <TD>
              <para>0</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_DROP_VIEW</para>
            </TD>
            <TD>
              <para>SQL_DV_DROP_VIEW</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_EXPRESSIONS_IN_ORDERBY</para>
            </TD>
            <TD>
              <para>"Y" </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_FILE_USAGE</para>
            </TD>
            <TD>
              <para>SQL_FILE_TABLE </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES1</para>
            </TD>
            <TD>
              <para>SQL_CA1_NEXT</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_GETDATA_EXTENSIONS</para>
            </TD>
            <TD>
              <para>               Multiple values             </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_GROUP_BY</para>
            </TD>
            <TD>
              <para>SQL_GB_GROUP_BY_CONTAINS_SELECT </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_IDENTIFIER_CASE</para>
            </TD>
            <TD>
              <para>SQL_IC_MIXED </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_IDENTIFIER_QUOTE_CHAR</para>
            </TD>
            <TD>
              <para>"`" (back quote) </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_KEYWORDS</para>
            </TD>
            <TD>
              <para>               Multiple values             </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_LIKE_ESCAPE_CLAUSE</para>
            </TD>
            <TD>
              <para>"N" </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_MAX_BINARY_LITERAL_LEN</para>
            </TD>
            <TD>
              <para>255 </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_MAX_CATALOG_NAME_LEN</para>
            </TD>
            <TD>
              <para>66</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_MAX_CHAR_LITERAL_LEN</para>
            </TD>
            <TD>
              <para>255 </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_MAX_COLUMN_NAME_LEN</para>
            </TD>
            <TD>
              <para>64 </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_MAX_COLUMNS_IN_GROUP_BY</para>
            </TD>
            <TD>
              <para>10 </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_MAX_COLUMNS_IN_INDEX</para>
            </TD>
            <TD>
              <para>0 </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_MAX_COLUMNS_IN_ORDER_BY</para>
            </TD>
            <TD>
              <para>10 </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_MAX_COLUMNS_IN_SELECT</para>
            </TD>
            <TD>
              <para>255 </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_MAX_COLUMNS_IN_TABLE</para>
            </TD>
            <TD>
              <para>255</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_MAX_CONCURRENT_ACTIVITIES</para>
            </TD>
            <TD>
              <para>0</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_MAX_CURSOR_NAME_LEN</para>
            </TD>
            <TD>
              <para>64 </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_MAX_DRIVER_CONNECTIONS</para>
            </TD>
            <TD>
              <para>64</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_MAX_INDEX_SIZE</para>
            </TD>
            <TD>
              <para>0 </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_MAX_PROCEDURE_NAME_LEN</para>
            </TD>
            <TD>
              <para>0 </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_MAX_ROW_SIZE</para>
            </TD>
            <TD>
              <para>65535 </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_MAX_ROW_SIZE_INCLUDES_LONG</para>
            </TD>
            <TD>
              <para>"Y" </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_MAX_SCHEMA_NAME_LEN</para>
            </TD>
            <TD>
              <para>0</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_MAX_STATEMENT_LEN</para>
            </TD>
            <TD>
              <para>65000 </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_MAX_TABLE_NAME_LEN</para>
            </TD>
            <TD>
              <para>12 </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_MAX_TABLES_IN_SELECT</para>
            </TD>
            <TD>
              <para>16 </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_MAX_USER_NAME_LEN</para>
            </TD>
            <TD>
              <para>0 </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_MULT_RESULT_SETS</para>
            </TD>
            <TD>
              <para>"N" </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_MULTIPLE_ACTIVE_TXN</para>
            </TD>
            <TD>
              <para>"Y" </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_NEED_LONG_DATA_LEN</para>
            </TD>
            <TD>
              <para>"N" </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_NON_NULLABLE_COLUMNS</para>
            </TD>
            <TD>
              <para>SQL_NNC_NON_NULL </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_NULL_COLLATION</para>
            </TD>
            <TD>
              <para>SQL_NC_LOW </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_NUMERIC_FUNCTIONS</para>
            </TD>
            <TD>
              <para>               Multiple values             </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_ODBC_SAG_CLI_ CONFORMANCE</para>
            </TD>
            <TD>
              <para>SQL_OSCC_COMPLIANT </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_ODBC_SQL_INTEGRITY</para>
            </TD>
            <TD>
              <para>"N"</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_ODBC_VER</para>
            </TD>
            <TD>
              <para>From Driver Manager </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_OJ_CAPABILITIES</para>
            </TD>
            <TD>
              <para>               Multiple values             </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_ORDER_BY_COLUMNS_IN_SELECT</para>
            </TD>
            <TD>
              <para>"N" </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_OUTER_JOINS</para>
            </TD>
            <TD>
              <para>"Y" </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_PROCEDURE_TERM</para>
            </TD>
            <TD>
              <para>"" </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_PROCEDURES</para>
            </TD>
            <TD>
              <para>"N" </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_QUOTED_IDENTIFIER_CASE</para>
            </TD>
            <TD>
              <para>SQL_IC_MIXED </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_ROW_UPDATES</para>
            </TD>
            <TD>
              <para>"N" </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_SCHEMA_TERM</para>
            </TD>
            <TD>
              <para>""</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_SCHEMA_USAGE</para>
            </TD>
            <TD>
              <para>0</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_SCROLL_OPTIONS</para>
            </TD>
            <TD>
              <para>               Multiple values             </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_SEARCH_PATTERN_ESCAPE</para>
            </TD>
            <TD>
              <para>"\" </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_SERVER_NAME</para>
            </TD>
            <TD>
              <para>"TEXT" </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_SPECIAL_CHARACTERS</para>
            </TD>
            <TD>
              <para>"~`@#$%^&amp;*_-+=\}{"';:?/&gt;&lt;,.!'[]|" </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_STRING_FUNCTIONS</para>
            </TD>
            <TD>
              <para>               Multiple values             </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_SUBQUERIES</para>
            </TD>
            <TD>
              <para>               Multiple values             </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_SYSTEM_FUNCTIONS</para>
            </TD>
            <TD>
              <para>0 </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_TABLE_TERM</para>
            </TD>
            <TD>
              <para>"TABLE" </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_TIMEDATE_ADD_INTERVALS</para>
            </TD>
            <TD>
              <para>0 </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_TIMEDATE_DIFF_INTERVALS</para>
            </TD>
            <TD>
              <para>0 </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_TIMEDATE_FUNCTIONS</para>
            </TD>
            <TD>
              <para>               Multiple values             </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_TXN_CAPABLE</para>
            </TD>
            <TD>
              <para>SQL_TC_NONE </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_TXN_ISOLATION_OPTION</para>
            </TD>
            <TD>
              <para>0 </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_UNION</para>
            </TD>
            <TD>
              <para>               Multiple values             </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_USER_NAME</para>
            </TD>
            <TD>
              <para>""</para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <relatedTopics />
</developerConceptualDocument>