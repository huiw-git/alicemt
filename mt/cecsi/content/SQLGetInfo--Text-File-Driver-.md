---
title: SQLGetInfo (Text File Driver)
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6b7a630e-47f8-4ee1-b2a7-476bc1d0b0d4
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# SQLGetInfo (Text File Driver)
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <alert class="note">
      <para>This topic provides Text File Driver-specific information. For general information about this function, see the appropriate topic under <legacyLink xlink:href="b7a49774-f458-44ce-9a04-a0457501405b">ODBC API Reference</legacyLink>.</para>
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
    <para>The ODBC driver returns SQL_FILE_TABLE for the Textdriver, because each file is a table.</para>
  </introduction>
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
              <para>Text</para>
            </TD>
            <TD>
              <para>1.0</para>
            </TD>
            <TD>
              <para>01.00.0000</para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <section>
    <title>SQL_CATALOG_USAGE</title>
    <content>
      <para>SQL_QU_DML_STATEMENTS | SQL_QU_TABLE_DEFINITION</para>
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