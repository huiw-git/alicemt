---
title: SQLGetInfo (Visual FoxPro ODBC Driver)
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: fbc39e3d-67d9-4331-bf5f-76dbd74c4c45
manager:jhubbard
translation.priority.ht: 
  - en-gb
---
# SQLGetInfo (Visual FoxPro ODBC Driver)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <alert class="note">
      <para>This topic contains Visual FoxPro ODBC Driver-specific information. For general information about this function, see the appropriate topic under <legacyLink xlink:href="b7a49774-f458-44ce-9a04-a0457501405b">ODBC API Reference</legacyLink>.</para>
    </alert>
    <para>Support: Full </para>
    <para>ODBC API Conformance: Level 1</para>
    <para>Returns general information about the Visual FoxPro ODBC Driver and data source associated with a connection handle, <legacyItalic>hdbc</legacyItalic>. The following list shows the value returned by the Visual FoxPro ODBC Driver for each <legacyItalic>fInfoType</legacyItalic> argument and comments regarding the returned values.</para>
    <para>For more information, see <legacyLink xlink:href="49dceccc-d816-4ada-808c-4c6138dccb64">SQLGetInfo</legacyLink> in the <legacyItalic>ODBC Programmer's Reference</legacyItalic>.</para>
  </introduction>
  <section>
    <title>A</title>
    <content>
      <para>SQL_ACCESSIBLE_PROCEDURES returns 'N'.</para>
      <para>SQL_ACCESSIBLE_TABLES returns 'Y'.</para>
      <para>SQL_ACTIVE_CONNECTIONS returns 0.</para>
      <para>SQL_ACTIVE_STATEMENTS returns 0.</para>
      <para>SQL_ALTER_TABLE returns either SQL_AT_ADD_COLUMN or SQL_AT_DROP_COLUMN.</para>
    </content>
  </section>
  <section>
    <title>B</title>
    <content>
      <para>SQL_BOOKMARK_PERSISTENCE returns SQL_BP_SCROLL.</para>
    </content>
  </section>
  <section>
    <title>C</title>
    <content>
      <para>SQL_COLUMN_ALIAS returns 'Y'.</para>
      <para>SQL_CONCAT_NULL_BEHAVIOR returns SQL_CB_NULL.</para>
      <para>SQL_CONVERT_BIGINT returns 0. The Visual FoxPro ODBC Driver does not support <legacyItalic>BigInt</legacyItalic>.</para>
      <para>SQL_CONVERT_BINARY returns 0.</para>
      <para>SQL_CONVERT_BIT returns 0.</para>
      <para>SQL_CONVERT_CHAR returns 0.</para>
      <para>SQL_CONVERT_DATE returns 0.</para>
      <para>SQL_CONVERT_DECIMAL returns 0.</para>
      <para>SQL_CONVERT_DOUBLE returns 0.</para>
      <para>SQL_CONVERT_FLOAT returns 0.</para>
      <para>SQL_CONVERT_INTEGER returns 0.</para>
      <para>SQL_CONVERT_LONGVARBINARY returns 0.</para>
      <para>SQL_CONVERT_LONGVARCHAR returns 0.</para>
      <para>SQL_CONVERT_NUMERIC returns 0.</para>
      <para>SQL_CONVERT_REAL returns 0.</para>
      <para>SQL_CONVERT_SMALLINT returns 0.</para>
      <para>SQL_CONVERT_TIME returns 0.</para>
      <para>SQL_CONVERT_TIMESTAMP returns 0.</para>
      <para>SQL_CONVERT_TINYINT returns 0.</para>
      <para>SQL_CONVERT_VARBINARY returns 0.</para>
      <para>SQL_CONVERT_VARCHAR returns 0.</para>
      <para>SQL_CONVERT_FUNCTIONS returns 0.</para>
      <para>SQL_CORRELATION_NAME returns SQL_CN_ANY.</para>
      <para>SQL_CURSOR_COMMIT_BEHAVIOR returns SQL_CB_PRESERVE.</para>
      <para>SQL_CURSOR_ROLLBACK_BEHAVIOR returns SQL_CB_PRESERVE.</para>
    </content>
  </section>
  <section>
    <title>D</title>
    <content>
      <para>SQL_DATA_SOURCE_NAME returns the value passed as DSN to <legacyLink xlink:href="49cbfafa-b21e-4e89-b248-9c7098f46b20">SQLConnect</legacyLink>, or <legacyLink xlink:href="10492c8f-3a18-4971-9db8-879e878083b9">SQLDriverConnect</legacyLink>; returns an empty string if no DSN is specified.</para>
      <para>SQL_DATA_SOURCE_READ_ONLY returns 'N'.</para>
      <para>SQL_DATABASE_NAME returns a full UNC path to the current database if the data source is a <legacyLink xlink:href="a379b3cb-0393-46e7-b03b-724a56d8f31c">database</legacyLink>. If the data source connects to a directory of <legacyLink xlink:href="a379b3cb-0393-46e7-b03b-724a56d8f31c">tables</legacyLink>, the function returns the path to the directory.</para>
      <para>SQL_DBMS_NAME returns "Visual FoxPro".</para>
      <para>SQL_DBMS_VER returns "03.00.0000".</para>
      <para>SQL_DEFAULT_TXN_ISOLATION returns SQL_TXN_READ_COMMITTED. Dirty reads are not possible, but nonrepeatable reads and phantoms are possible.</para>
      <para>SQL_DRIVER_HDBC is implemented by the Driver Manager.</para>
      <para>SQL_DRIVER_HENV is implemented by the Driver Manager.</para>
      <para>SQL_DRIVER_HLIB is implemented by the Driver Manager.</para>
      <para>SQL_DRIVER_HSTMT is implemented by the Driver Manager.</para>
      <para>SQL_DRIVER_NAME returns "vfpodbc.dll".</para>
      <para>SQL_DRIVER_ODBC_VER returns "02.50" (SQL_SPEC_MAJOR, SQL_SPEC_MINOR).</para>
      <para>SQL_DRIVER_VER returns "01.00.0000".</para>
    </content>
  </section>
  <section>
    <title>E</title>
    <content>
      <para>SQL_EXPRESSIONS_IN_ORDERBY returns 'N'.</para>
    </content>
  </section>
  <section>
    <title>F</title>
    <content>
      <para>SQL_FETCH_DIRECTION returns:</para>
      <list class="bullet">
        <listItem>
          <para>SQL_FD_FETCH_NEXT</para>
        </listItem>
        <listItem>
          <para>SQL_FD_FETCH_FIRST</para>
        </listItem>
        <listItem>
          <para>SQL_FD_FETCH_LAST</para>
        </listItem>
        <listItem>
          <para>SQL_FD_FETCH_PRIOR</para>
        </listItem>
        <listItem>
          <para>SQL_FD_FETCH_ABSOLUTE</para>
        </listItem>
        <listItem>
          <para>SQL_FD_FETCH_RELATIVE</para>
        </listItem>
        <listItem>
          <para>SQL_FD_FETCH_BOOKMARK.</para>
        </listItem>
      </list>
      <para>SQL_FILE_USAGE returns SQL_FILE_QUALIFIER both for database (.dbc file) and for free table (.dbf file) data sources.</para>
    </content>
  </section>
  <section>
    <title>G-H</title>
    <content>
      <para>SQL_GETDATA_EXENSIONS returns:</para>
      <list class="bullet">
        <listItem>
          <para>SQL_GD_ANY_COLUMN</para>
        </listItem>
        <listItem>
          <para>SQL_GD_ANY_BLOCK</para>
        </listItem>
        <listItem>
          <para>SQL_GD_ANY_BOUND</para>
        </listItem>
        <listItem>
          <para>SQL_GD_ANY_ORDER</para>
        </listItem>
      </list>
      <para>SQL_GROUP_BY returns SQL_GB_NO_RELATION.</para>
    </content>
  </section>
  <section>
    <title>I-J</title>
    <content>
      <para>SQL_IDENTIFIER_CASE returns SQL_IC_MIXED.</para>
      <para>SQL_IDENTIFIER_QUOTE_CHAR returns `.</para>
    </content>
  </section>
  <section>
    <title>K</title>
    <content>
      <para>SQL_KEYWORDS returns "".</para>
    </content>
  </section>
  <section>
    <title>L</title>
    <content>
      <para>SQL_LIKE_ESCAPE_CLAUSE returns 'N'.</para>
      <para>SQL_LOCK_TYPES returns SQL_LCK_NO_CHANGE.</para>
    </content>
  </section>
  <section>
    <title>M</title>
    <content>
      <para>SQL_MAX_BINARY_LITERAL_LEN returns 0.</para>
      <para>SQL_MAX_CHAR_LITERAL_LEN returns 254.</para>
      <para>SQL_MAX_COLUMN_NAME_LEN returns 128.</para>
      <para>SQL_MAX_COLUMNS_IN_GROUP_BY returns 16.</para>
      <para>SQL_MAX_COLUMNS_IN_ORDER_BY returns 16.</para>
      <para>SQL_MAX_COLUMNS_IN_INDEX returns 0.</para>
      <para>SQL_MAX_COLUMNS_IN_SELECT returns 254.</para>
      <para>SQL_MAX_COLUMNS_IN_TABLE returns 254.</para>
      <para>SQL_MAX_CURSOR_NAME_LEN returns 254.</para>
      <para>SQL_MAX_INDEX_SIZE returns 0.</para>
      <para>SQL_MAX_OWNER_NAME_LEN returns 0.</para>
      <para>SQL_MAX_PROCEDURE_NAME_LEN returns 0. The Visual FoxPro ODBC Driver does not allow direct access to Visual FoxPro stored procedures.</para>
      <para>SQL_MAX_QUALIFIER_NAME_LEN returns the maximum operating system path length.</para>
      <para>SQL_MAX_ROW_SIZE returns 254^2.</para>
      <para>SQL_MAX_ROW_SIZE_INCLUDES_LONG returns 'N'.</para>
      <para>SQL_MAX_STATEMENT_LEN returns 8192.</para>
      <para>SQL_MAX_TABLE_NAME_LEN returns 128.</para>
      <para>SQL_MAX_TABLES_IN_SELECT returns 16.</para>
      <para>SQL_MAX_USER_NAME_LEN returns 0.</para>
      <para>SQL_MULT_RESULT_SETS returns 'Y'.</para>
      <para>SQL_MULTIPLE_ACTIVE_TXN returns 'Y'. Multiple connections can have several transactions open at once.</para>
    </content>
  </section>
  <section>
    <title>N</title>
    <content>
      <para>SQL_NEED_LONG_DATA_LEN returns 'N'.</para>
      <para>SQL_NON_NULLABLE_COLUMNS returns SQL_NNC_NON_NULL.</para>
      <para>SQL_NULL_COLLATION returns SQL_NC_LOW.</para>
      <para>SQL_NUMERIC_FUNCTIONS returns all functions except SQL_FN_NUM_POWER, which is not supported by the Visual FoxPro ODBC Driver. The following functions are supported:</para>
      <list class="bullet">
        <listItem>
          <para>SQL_FN_NUM_ABS</para>
        </listItem>
        <listItem>
          <para>SQL_FN_NUM_ACOS</para>
        </listItem>
        <listItem>
          <para>SQL_FN_NUM_ASIN</para>
        </listItem>
        <listItem>
          <para>SQL_FN_NUM_ATAN</para>
        </listItem>
        <listItem>
          <para>SQL_FN_NUM_ATAN2</para>
        </listItem>
        <listItem>
          <para>SQL_FN_NUM_CELING</para>
        </listItem>
        <listItem>
          <para>SQL_FN_NUM_COS</para>
        </listItem>
        <listItem>
          <para>SQL_FN_NUM_COT</para>
        </listItem>
        <listItem>
          <para>SQL_FN_NUM_DEGREES</para>
        </listItem>
        <listItem>
          <para>SQL_FN_NUM_EXP</para>
        </listItem>
        <listItem>
          <para>SQL_FN_NUM_FLOOR</para>
        </listItem>
        <listItem>
          <para>SQL_FN_NUM_LOG</para>
        </listItem>
        <listItem>
          <para>SQL_FN_NUM_LOG10</para>
        </listItem>
        <listItem>
          <para>SQL_FN_NUM_MOD</para>
        </listItem>
        <listItem>
          <para>SQL_FN_NUM_PI</para>
        </listItem>
        <listItem>
          <para>SQL_FN_NUM_RADIANS</para>
        </listItem>
        <listItem>
          <para>SQL_FN_NUM_RAND</para>
        </listItem>
        <listItem>
          <para>SQL_FN_NUM_ROUND</para>
        </listItem>
        <listItem>
          <para>SQL_FN_NUM_SIGN</para>
        </listItem>
        <listItem>
          <para>SQL_FN_NUM_SIN</para>
        </listItem>
        <listItem>
          <para>SQL_FN_NUM_SQRT</para>
        </listItem>
        <listItem>
          <para>SQL_FN_NUM_TAN</para>
        </listItem>
      </list>
    </content>
  </section>
  <section>
    <title>O</title>
    <content>
      <para>SQL_ODBC_API_CONFORMANCE returns SQL_OAC_LEVEL1.</para>
      <para>SQL_ODBC_SAG_CLI_CONFORMANCE returns SQL_OSCC_COMPLIANT.</para>
      <para>SQL_ODBC_SQL_CONFORMANCE returns SQL_OSC_MINIMUM. Minimum SQL syntax is supported.</para>
      <para>SQL_ODBC_SQL_OPT_IEF returns "N".</para>
      <para>SQL_ODBC_VER is implemented by the Driver Manager.</para>
      <para>SQL_ORDER_BY_COLUMNS_IN_SELECT returns "N".</para>
      <para>SQL_OUTER_JOINS returns "N".</para>
      <para>SQL_OWNER_TERM returns "". The Visual FoxPro ODBC Driver does not support owners for its objects.</para>
      <para>SQL_OWNER_USAGE returns 0. The Visual FoxPro ODBC Driver does not support owners for its objects.</para>
    </content>
  </section>
  <section>
    <title>P</title>
    <content>
      <para>SQL_POS_OPERATIONS returns SQL_POS_POSITION.</para>
      <para>SQL_POSITIONED_STATEMENTS returns 0.</para>
      <para>SQL_PROCEDURE_TERM returns "".</para>
      <para>SQL_PROCEDURES returns 'N'.</para>
    </content>
  </section>
  <section>
    <title>Q</title>
    <content>
      <para>SQL_QUALIFIER_LOCATION returns SQL_QL_START.</para>
      <para>SQL_QUALIFIER_NAME_SEPARATOR returns '!' or '\'. The separator between database and table is '!' for data sources connected to <legacyLink xlink:href="a379b3cb-0393-46e7-b03b-724a56d8f31c">databases</legacyLink>, and '\' for data sources that are directories of <legacyLink xlink:href="a379b3cb-0393-46e7-b03b-724a56d8f31c">free tables</legacyLink>.</para>
      <para>SQL_QUALIFIER_TERM returns "database" or "directory". The qualifier is "database" for data sources connected to <legacyLink xlink:href="a379b3cb-0393-46e7-b03b-724a56d8f31c">databases</legacyLink>, and "directory" for data sources that are directories of <legacyLink xlink:href="a379b3cb-0393-46e7-b03b-724a56d8f31c">free tables</legacyLink>.</para>
      <para>SQL_QUALIFIER_USAGE does not support SQL_QU_PRIVILEGE_DEFINITION; it returns either SQL_QU_DML_STATEMENT or SQL_QU_TABLE_DEFINITION.</para>
      <para>SQL_QUOTED_IDENTIFIER_CASE returns SQL_IC_MIXED.</para>
    </content>
  </section>
  <section>
    <title>R</title>
    <content>
      <para>SQL_ROW_UPDATES returns "N". The Visual FoxPro ODBC Driver supports only static and forward cursors.</para>
    </content>
  </section>
  <section>
    <title>S</title>
    <content>
      <para>SQL_SCROLL_CONCURRENCY returns SQL_SCCO_READ_ONLY.</para>
      <para>SQL_SCROLL_OPTIONS returns either SQL_SO_STATIC or SQL_SO_READONLY.</para>
      <para>SQL_SEARCH_PATTERN_ESCAPE returns "\".</para>
      <para>SQL_SERVER_NAME returns "".</para>
      <para>SQL_SPECIAL_CHARACTERS returns "~@#$%^".</para>
      <para>SQL_STATIC_SENSITIVITY returns 0. The Visual FoxPro ODBC Driver does not support positional updates.</para>
      <para>SQL_STRING_FUNCTIONS does not support SQL_FN_STR_INSERT, SQL_FN_STR_LOCATE, SQL_FN_STR_LOCATE_2, or SQL_FN_STR_SOUNDEX. </para>
      <para>It returns:</para>
      <list class="bullet">
        <listItem>
          <para>SQL_FN_STR_ASCII </para>
        </listItem>
        <listItem>
          <para>SQL_FN_STR_CHAR</para>
        </listItem>
        <listItem>
          <para>SQL_FN_STR_CONCAT</para>
        </listItem>
        <listItem>
          <para>SQL_FN_STR_DIFFERENCE</para>
        </listItem>
        <listItem>
          <para>SQL_FN_STR_LCASE</para>
        </listItem>
        <listItem>
          <para>SQL_FN_STR_LEFT</para>
        </listItem>
        <listItem>
          <para>SQL_FN_STR_LENGTH</para>
        </listItem>
        <listItem>
          <para>SQL_FN_STR_LTRIM</para>
        </listItem>
        <listItem>
          <para>SQL_FN_STR_REPEAT</para>
        </listItem>
        <listItem>
          <para>SQL_FN_STR_REPLACE</para>
        </listItem>
        <listItem>
          <para>SQL_FN_STR_RIGHT</para>
        </listItem>
        <listItem>
          <para>SQL_FN_STR_RTRIM</para>
        </listItem>
        <listItem>
          <para>SQL_FN_STR_SUBSTRING</para>
        </listItem>
        <listItem>
          <para>SQL_FN_STR_UCASE</para>
        </listItem>
        <listItem>
          <para>SQL_FN_STR_SPACE.</para>
        </listItem>
      </list>
      <para>SQL_SUBQUERIES returns:</para>
      <list class="bullet">
        <listItem>
          <para>SQL_SQ_CORRELATED_SUBQUERIES</para>
        </listItem>
        <listItem>
          <para>SQL_SQ_COMPARISON</para>
        </listItem>
        <listItem>
          <para>SQL_SQ_EXISTS</para>
        </listItem>
        <listItem>
          <para>SQL_SQ_IN</para>
        </listItem>
        <listItem>
          <para>SQL_SQ_QUANTIFIED.</para>
        </listItem>
      </list>
      <para>SQL_SYSTEM_FUNCTIONS returns:</para>
      <list class="bullet">
        <listItem>
          <para>SQL_FN_SYS_DBNAME</para>
        </listItem>
        <listItem>
          <para>SQL_FN_SYS_IFNULL</para>
        </listItem>
      </list>
      <para>but not:</para>
      <list class="bullet">
        <listItem>
          <para>SQL_FN_SYS_USERNAME</para>
        </listItem>
      </list>
    </content>
  </section>
  <section>
    <title>T</title>
    <content>
      <para>SQL_TABLE_TERM returns "table".</para>
      <para>SQL_TIMEDATE_ADD_INTERVALS returns:</para>
      <list class="bullet">
        <listItem>
          <para>SQL_FN_TSI_ SECOND</para>
        </listItem>
        <listItem>
          <para>SQL_FN_TSI_MINUTE </para>
        </listItem>
        <listItem>
          <para>SQL_FN_TSI_HOUR </para>
        </listItem>
        <listItem>
          <para>SQL_FN_TSI_DAY</para>
        </listItem>
        <listItem>
          <para>SQL_FN_TSI_MONTH</para>
        </listItem>
        <listItem>
          <para>SQL_FN_TSI_YEAR</para>
        </listItem>
      </list>
      <para>but not:</para>
      <list class="bullet">
        <listItem>
          <para>SQL_FN_TSI_FRAC_SECOND</para>
        </listItem>
        <listItem>
          <para>SQL_FN_TSI_WEEK</para>
        </listItem>
        <listItem>
          <para>SQL_FN_TSI_QUARTER</para>
        </listItem>
      </list>
      <para>SQL_TIMEDATE_DIFF_INTERVALS returns:</para>
      <list class="bullet">
        <listItem>
          <para>SQL_FN_TSI_ SECOND</para>
        </listItem>
        <listItem>
          <para>SQL_FN_TSI_MINUTE</para>
        </listItem>
        <listItem>
          <para>SQL_FN_TSI_HOUR</para>
        </listItem>
        <listItem>
          <para>SQL_FN_TSI_DAY</para>
        </listItem>
        <listItem>
          <para>SQL_FN_TSI_MONTH</para>
        </listItem>
        <listItem>
          <para>SQL_FN_TSI_YEAR</para>
        </listItem>
      </list>
      <para>SQL_TIMEDATE_FUNCTIONS does not support SQL_FN_TD_QUARTER, SQL_FN_TD_TIMESTAMPADD, SQL_FN_TD_DAYOFYEAR, or SQL_FN_TD_WEEK.</para>
      <para>It returns:</para>
      <list class="bullet">
        <listItem>
          <para>SQL_FN_TD_CURDATE </para>
        </listItem>
        <listItem>
          <para>SQL_FN_TD_CURTIME </para>
        </listItem>
        <listItem>
          <para>SQL_FN_TD_DAYNAME</para>
        </listItem>
        <listItem>
          <para>SQL_FN_TD_DAYOFMONTH</para>
        </listItem>
        <listItem>
          <para>SQL_FN_TD_DAYOFWEEK</para>
        </listItem>
        <listItem>
          <para>SQL_FN_TD_HOUR</para>
        </listItem>
        <listItem>
          <para>SQL_FN_TD_MINUTE</para>
        </listItem>
        <listItem>
          <para>SQL_FN_TD_MONTH</para>
        </listItem>
        <listItem>
          <para>SQL_FN_TD_MONTHNAME</para>
        </listItem>
        <listItem>
          <para>SQL_FN_TD_NOW</para>
        </listItem>
        <listItem>
          <para>SQL_FN_TD_SECOND</para>
        </listItem>
        <listItem>
          <para>SQL_FN_TD_TIMESTAMPDIFF </para>
        </listItem>
        <listItem>
          <para>SQL_FN_TD_YEAR .</para>
        </listItem>
      </list>
      <para>SQL_TXN_CAPABLE returns SQL_TC_DML.</para>
      <para>SQL_TXN_ISOLATION_OPTION returns SQL_TXN_READ_COMMITTED.</para>
    </content>
  </section>
  <section>
    <title>U-Z</title>
    <content>
      <para>SQL_UNION returns either SQL_U_UNION or SQL_U_UNION_ALL.</para>
      <para>SQL_USER_NAME returns &lt;blank&gt;.</para>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>