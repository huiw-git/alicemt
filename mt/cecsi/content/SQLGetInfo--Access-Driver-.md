---
title: SQLGetInfo (Access Driver)
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c226aba7-a2f4-4b32-b640-92654b40e5a7
manager:jhubbard
translation.priority.ht: 
  - en-gb
---
# SQLGetInfo (Access Driver)
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <alert class="note">
      <para>This topic provides Access Driver-specific information. For general information about this function, see the appropriate topic under <legacyLink xlink:href="b7a49774-f458-44ce-9a04-a0457501405b">ODBC API Reference</legacyLink>.</para>
    </alert>
    <para>       <legacyBold>SQLGetInfo</legacyBold> supports the SQL_FILE_USAGE information type. The returned value is a 16-bit integer that indicates how the driver directly treats files in a data source:  </para>
    <list class="bullet">
      <listItem>
        <para>SQL_FILE_NOT_SUPPORTED — The driver is not a single-tier driver.</para>
      </listItem>
      <listItem>
        <para>SQL_FILE_TABLE — A single-tier driver treats files in a data source as tables.</para>
      </listItem>
      <listItem>
        <para>SQL_FILE_QUALIFIER — A single-tier driver treats files in a data source as a qualifier.</para>
      </listItem>
    </list>
    <para>The ODBC driver returns SQL_FILE_QUALIFIER because each file is a complete database.</para>
  </introduction>
  <section>
    <title>SQL_BOOKMARK_PERSISTENCE</title>
    <content>
      <para>SQL_BP_SCROLL |  SQL_BP_UPDATE[1]</para>
      <para>[1]   Bookmarks persist after a commit but do not persist after a rollback.</para>
    </content>
  </section>
  <section>
    <title>SQL_CONVERT_BINARY</title>
    <content>
      <para>SQL_CVT_DOUBLE |  SQL_CVT_FLOAT |  SQL_CVT_INTEGER |  SQL_CVT_NUMERIC |  SQL_CVT_REAL |  SQL_CVT_SMALLINT |  SQL_CVT_VARCHAR | SQL_CVT_WVARCHAR</para>
    </content>
  </section>
  <section>
    <title>SQL_CONVERT_CHAR</title>
    <content>
      <para>SQL_CVT_DOUBLE |  SQL_CVT_FLOAT |  SQL_CVT_INTEGER |  SQL_CVT_NUMERIC |  SQL_CVT_REAL |  SQL_CVT_SMALLINT |  SQL_CVT_VARCHAR | SQL_CVT_WVARCHAR</para>
    </content>
  </section>
  <section>
    <title>SQL_CONVERT_DATE</title>
    <content>
      <para>SQL_CVT_DOUBLE |  SQL_CVT_FLOAT |  SQL_CVT_INTEGER |  SQL_CVT_NUMERIC |  SQL_CVT_REAL |  SQL_CVT_SMALLINT |  SQL_CVT_VARCHAR | SQL_CVT_WVARCHAR</para>
    </content>
  </section>
  <section>
    <title>SQL_CONVERT_DOUBLE</title>
    <content>
      <para>SQL_CVT_DOUBLE |  SQL_CVT_FLOAT |  SQL_CVT_INTEGER |  SQL_CVT_NUMERIC |  SQL_CVT_REAL |  SQL_CVT_SMALLINT |  SQL_CVT_VARCHAR | SQL_CVT_WVARCHAR</para>
    </content>
  </section>
  <section>
    <title>SQL_CONVERT_FLOAT</title>
    <content>
      <para>SQL_CVT_DOUBLE |  SQL_CVT_FLOAT |  SQL_CVT_INTEGER |  SQL_CVT_NUMERIC |  SQL_CVT_REAL |  SQL_CVT_SMALLINT |  SQL_CVT_VARCHAR | SQL_CVT_WVARCHAR</para>
    </content>
  </section>
  <section>
    <title>SQL_CONVERT_INTEGER</title>
    <content>
      <para>SQL_CVT_DOUBLE | SQL_CVT_FLOAT |  SQL_CVT_INTEGER |  SQL_CVT_NUMERIC |  SQL_CVT_REAL |  SQL_CVT_SMALLINT |  SQL_CVT_VARCHAR | SQL_CVT_WVARCHAR</para>
    </content>
  </section>
  <section>
    <title>SQL_CONVERT_LONGVARBINARY</title>
    <content>
      <para>SQL_CVT_DOUBLE | SQL_CVT_FLOAT |  SQL_CVT_INTEGER |  SQL_CVT_NUMERIC |  SQL_CVT_REAL |  SQL_CVT_SMALLINT |  SQL_CVT_VARCHAR | SQL_CVT_WVARCHAR</para>
    </content>
  </section>
  <section>
    <title>SQL_CONVERT_LONGVARCHAR</title>
    <content>
      <para>SQL_CVT_DOUBLE | SQL_CVT_FLOAT |  SQL_CVT_INTEGER |  SQL_CVT_NUMERIC |  SQL_CVT_REAL |  SQL_CVT_SMALLINT |  SQL_CVT_VARCHAR | SQL_CVT_WVARCHAR</para>
    </content>
  </section>
  <section>
    <title>SQL_CONVERT_NUMERIC</title>
    <content>
      <para>SQL_CVT_DOUBLE | SQL_CVT_FLOAT |  SQL_CVT_INTEGER |  SQL_CVT_NUMERIC |  SQL_CVT_REAL |  SQL_CVT_SMALLINT |  SQL_CVT_VARCHAR | SQL_CVT_WVARCHAR</para>
    </content>
  </section>
  <section>
    <title>SQL_CONVERT_REAL</title>
    <content>
      <para>SQL_CVT_DOUBLE | SQL_CVT_FLOAT |  SQL_CVT_INTEGER |  SQL_CVT_NUMERIC |  SQL_CVT_REAL |  SQL_CVT_SMALLINT |  SQL_CVT_VARCHAR | SQL_CVT_WVARCHAR</para>
    </content>
  </section>
  <section>
    <title>SQL_CONVERT_SMALLINT</title>
    <content>
      <para>SQL_CVT_DOUBLE | SQL_CVT_FLOAT |  SQL_CVT_INTEGER |  SQL_CVT_NUMERIC |  SQL_CVT_REAL |  SQL_CVT_SMALLINT |  SQL_CVT_VARCHAR | SQL_CVT_WVARCHAR</para>
    </content>
  </section>
  <section>
    <title>SQL_CONVERT_TIME</title>
    <content>
      <para>SQL_CVT_DOUBLE | SQL_CVT_FLOAT |  SQL_CVT_INTEGER |  SQL_CVT_NUMERIC |  SQL_CVT_REAL |  SQL_CVT_SMALLINT |  SQL_CVT_VARCHAR | SQL_CVT_WVARCHAR</para>
    </content>
  </section>
  <section>
    <title>SQL_CONVERT_TIMESTAMP</title>
    <content>
      <para>SQL_CVT_DOUBLE | SQL_CVT_FLOAT |  SQL_CVT_INTEGER |  SQL_CVT_NUMERIC |  SQL_CVT_REAL |  SQL_CVT_SMALLINT |  SQL_CVT_VARCHAR | SQL_CVT_WVARCHAR</para>
    </content>
  </section>
  <section>
    <title>SQL_CONVERT_TINYINT</title>
    <content>
      <para>SQL_CVT_DOUBLE | SQL_CVT_FLOAT |  SQL_CVT_INTEGER |  SQL_CVT_NUMERIC |  SQL_CVT_REAL |  SQL_CVT_SMALLINT |  SQL_CVT_VARCHAR | SQL_CVT_WVARCHAR</para>
    </content>
  </section>
  <section>
    <title>SQL_CONVERT_VARBINARY</title>
    <content>
      <para>SQL_CVT_DOUBLE | SQL_CVT_FLOAT |  SQL_CVT_INTEGER |  SQL_CVT_NUMERIC |  SQL_CVT_REAL |  SQL_CVT_SMALLINT |  SQL_CVT_VARCHAR | SQL_CVT_WVARCHAR</para>
    </content>
  </section>
  <section>
    <title>SQL_CONVERT_VARCHAR</title>
    <content>
      <para>SQL_CVT_DOUBLE | SQL_CVT_FLOAT |  SQL_CVT_INTEGER |  SQL_CVT_NUMERIC |  SQL_CVT_REAL |  SQL_CVT_SMALLINT |  SQL_CVT_VARCHAR | SQL_CVT_WVARCHAR</para>
    </content>
  </section>
  <section>
    <title>SQL_UNION</title>
    <content>
      <para>SQL_U_UNION_ALL | SQL_U_UNION</para>
    </content>
  </section>
  <section>
    <title>SQL_DBMS_VER</title>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>ISAM</para>
            </TD>
            <TD>
              <para>Version</para>
            </TD>
            <TD>
              <para>Format of version numbers</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>Microsoft Access</para>
            </TD>
            <TD>
              <para>2.0</para>
            </TD>
            <TD>
              <para>02.00.0000</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para> </para>
            </TD>
            <TD>
              <para>3.0</para>
            </TD>
            <TD>
              <para>03.00.0000</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para> </para>
            </TD>
            <TD>
              <para>3.5</para>
            </TD>
            <TD>
              <para>03.50.0000</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para> </para>
            </TD>
            <TD>
              <para>4.0</para>
            </TD>
            <TD>
              <para>04.00.0000</para>
            </TD>
          </tr>
        </tbody>
      </table>
      <alert class="note">
        <para>Versions 1.0 and 1.1 are not supported. Also, there is no difference in the data format in Microsoft Access versions 3.0, 7.0, and 97.</para>
      </alert>
    </content>
  </section>
  <section>
    <title>SQL_DDL_INDEX</title>
    <content>
      <para>SQL_DL_CREATE_INDEX</para>
      <para>SQL_DL_DROP_INDEX</para>
    </content>
  </section>
  <section>
    <title>SQL_GETDATA_EXTENSIONS</title>
    <content>
      <para>SQL_GD_ANY_ORDER | SQL_GD_ANY_COLUMN | SQL_GD_BLOCK | SQL_GD_BOUND </para>
    </content>
  </section>
  <section>
    <title>SQL_KEYWORDS</title>
    <content>
      <para>ALPHANUMERIC</para>
      <para>AUTOINCREMENT</para>
      <para>BINARY</para>
      <para>BOOLEAN</para>
      <para>BYTE</para>
      <para>COUNTER</para>
      <para>CURRENCY</para>
      <para>DATABASE</para>
      <para>DATABASENAME</para>
      <para>DATETIME</para>
      <para>DISALLOW</para>
      <para>DISTINCTROW</para>
      <para>DOUBLEFLOAT</para>
      <para>FLOAT4</para>
      <para>FLOAT8</para>
      <para>GENERAL</para>
      <para>IEEEDOUBLE</para>
      <para>IEEESINGLE</para>
      <para>IGNORE</para>
      <para>IMAGE</para>
      <para>INTEGER1</para>
      <para>INTEGER2</para>
      <para>INTEGER4</para>
      <para>LOGICAL</para>
      <para>LOGICAL1</para>
      <para>LONG</para>
      <para>LONGBINARY</para>
      <para>LONGCHAR</para>
      <para>LONGTEXT</para>
      <para>MEMO</para>
      <para>MONEY</para>
      <para>NOTE</para>
      <para>NUMBER</para>
      <para>OLEOBJECT</para>
      <para>OWNERACCESS</para>
      <para>PARAMETERS</para>
      <para>PERCENT</para>
      <para>PIVOT</para>
      <para>SHORT</para>
      <para>SINGLE</para>
      <para>SINGLEFLOAT</para>
      <para>STDEV</para>
      <para>STDEVP</para>
      <para>STRING</para>
      <para>TABLEID</para>
      <para>TEXT</para>
      <para>TOP</para>
      <para>TRANSFORM</para>
      <para>UNSIGNEDBYTE</para>
      <para>VAR</para>
      <para>VARBINARY</para>
      <para>VARP</para>
      <para>YESNO</para>
    </content>
  </section>
  <section>
    <title>SQL_NUMERIC_FUNCTIONS</title>
    <content>
      <para>SQL_FN_NUM_ABS | SQL_FN_NUM_ATAN | SQL_FN_NUM_CEILING | SQL_FN_NUM_COS | SQL_FN_NUM_EXP | SQL_FN_NUM_FLOOR | SQL_FN_NUM_LOG | SQL_FN_NUM_MOD | SQL_FN_NUM_POWER | SQL_FN_NUM_RAND | SQL_FN_NUM_SIGN | SQL_FN_NUM_SIN | SQL_FN_NUM_SQRT | SQL_FN_NUM_TAN </para>
    </content>
  </section>
  <section>
    <title>SQL_OJ_CAPABILITIES</title>
    <content>
      <para>SQL_OJ_LEFT SQL_OJ_RIGHT SQL_OJ_NOT_ORDERED SQL_OJ_INNER SQL_OJ_ALL_COMPARISON_OPS</para>
    </content>
  </section>
  <section>
    <title>SQL_CATALOG_USAGE</title>
    <content>
      <para>SQL_QU_DML_STATEMENTS | SQL_QU_TABLE_DEFINITION | SQL_QU_INDEX_DEFINITION | SQL_QU_PROCEDURE_INVOCATION </para>
    </content>
  </section>
  <section>
    <title>SQL_SCROLL_OPTIONS</title>
    <content>
      <para>SQL_SO_FORWARD_ONLY | SQL_SO_STATIC | SQL_SO_KEYSET_DRIVEN </para>
    </content>
  </section>
  <section>
    <title>SQL_STRING_FUNCTIONS</title>
    <content>
      <para>SQL_FN_STR_ASCII | SQL_FN_STR_CHAR | SQL_FN_STR_CONCAT |  SQL_FN_STR_LCASE |  SQL_FN_STR_LEFT |  SQL_FN_STR_LENGTH |  SQL_FN_STR_LOCATE | SQL_FN_STR_LOCATE_2  SQL_FN_STR_LTRIM |  SQL_FN_STR_RIGHT |  SQL_FN_STR_RTRIM |  SQL_FN_STR_SPACE | SQL_FN_STR_SUBSTRING |  SQL_FN_STR_UCASE </para>
    </content>
  </section>
  <section>
    <title>SQL_SUBQUERIES</title>
    <content>
      <para>SQL_SQ_COMPARISON | SQL_SQ_EXISTS | SQL_SQ_IN | SQL_SQ_QUANTIFIED | SQL_SQ_CORRELATED_SUBQUERIES </para>
    </content>
  </section>
  <section>
    <title>SQL_TIMEDATE_FUNCTIONS</title>
    <content>
      <para>SQL_FN_TD_CURDATE |  SQL_FN_TD_CURTIME |  SQL_FN_TD_DAYOFMONTH |  SQL_FN_TD_DAYOFWEEK | SQL_FN_TD_DAYOFYEAR |  SQL_FN_TD_HOUR | SQL_FN_TD_MINUTE | SQL_FN_TD_MONTH |  SQL_FN_TD_NOW | SQL_FN_TD_SECOND | SQL_FN_TD_WEEK | SQL_FN_TD_YEAR</para>
    </content>
  </section>
  <relatedTopics />
</developerConceptualDocument>