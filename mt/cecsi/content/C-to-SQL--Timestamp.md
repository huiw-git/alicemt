---
title: C to SQL: Timestamp
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0e08bfff-68f9-4648-9558-09b57fea08ad
manager:jhubbard
translation.priority.ht: 
  - en-gb
---
# C to SQL: Timestamp
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The identifier for the timestamp ODBC C data type is:</para>
    <para>SQL_C_TYPE_TIMESTAMP</para>
    <para>The following table shows the ODBC SQL data types to which timestamp C data may be converted. For an explanation of the columns and terms in the table, see <legacyLink xlink:href="ee0afe78-b58f-4d34-ad9b-616bb23653bd">Converting Data from C to SQL Data Types</legacyLink>.</para>
    <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
      <thead>
        <tr>
          <TD>
            <para>SQL type identifier</para>
          </TD>
          <TD>
            <para>Test</para>
          </TD>
          <TD>
            <para>SQLSTATE</para>
          </TD>
        </tr>
      </thead>
      <tbody>
        <tr>
          <TD>
            <para>SQL_CHAR</para>
            <para>SQL_VARCHAR</para>
            <para>SQL_LONGVARCHAR</para>
          </TD>
          <TD>
            <para>Column byte length &gt;= Character byte length</para>
            <para>19 &lt;= Column byte length &lt; Character byte length</para>
            <para>Column byte length &lt; 19</para>
            <para>Data value is not a valid timestamp</para>
          </TD>
          <TD>
            <para>n/a</para>
            <para>22001</para>
            <para>22001</para>
            <para>22008</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_WCHAR</para>
            <para>SQL_WVARCHAR</para>
            <para>SQL_WLONGVARCHAR</para>
          </TD>
          <TD>
            <para>Column character length &gt;= Character length of data</para>
            <para>19 &lt;= Column character length &lt; Character length of data</para>
            <para>Column character length &lt; 19</para>
            <para>Data value is not a valid timestamp</para>
          </TD>
          <TD>
            <para>n/a</para>
            <para>22001</para>
            <para>22001</para>
            <para>22008</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_TYPE_DATE</para>
          </TD>
          <TD>
            <para>Time fields are zero</para>
            <para>Time fields are nonzero</para>
            <para>Data value does not contain a valid date</para>
          </TD>
          <TD>
            <para>n/a</para>
            <para>22008</para>
            <para>22007</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_TYPE_TIME</para>
          </TD>
          <TD>
            <para>Fractional seconds fields are zero[a]</para>
            <para>Fractional seconds fields are nonzero[a]</para>
            <para>Data value does not contain a valid time</para>
          </TD>
          <TD>
            <para>n/a</para>
            <para>22008</para>
            <para>22007</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_TYPE_TIMESTAMP</para>
          </TD>
          <TD>
            <para>Fractional seconds fields are not  truncated</para>
            <para>Fractional seconds fields are truncated</para>
            <para>Data value is not a valid timestamp</para>
          </TD>
          <TD>
            <para>n/a</para>
            <para>22008</para>
            <para>22007</para>
          </TD>
        </tr>
      </tbody>
    </table>
    <para>[a]   The date fields of the timestamp structure are ignored.</para>
    <para>For information about what values are valid in a SQL_C_TIMESTAMP structure, see <legacyLink xlink:href="b681d260-3dbb-47df-a616-4910d727add7">C Data Types</legacyLink>, earlier in this appendix.</para>
    <para>When timestamp C data is converted to character SQL data, the resulting character data is in the "<legacyItalic>yyyy</legacyItalic>-<legacyItalic>mm</legacyItalic>-<legacyItalic>dd</legacyItalic> <legacyItalic>hh</legacyItalic>:<legacyItalic>mm</legacyItalic>:<legacyItalic>ss</legacyItalic>[.<legacyItalic>f...</legacyItalic>]" format.</para>
    <para>The driver ignores the length/indicator value when converting data from the timestamp C data type and assumes that the size of the data buffer is the size of the timestamp C data type. The length/indicator value is passed in the <legacyItalic>StrLen_or_Ind</legacyItalic> argument in <legacyBold>SQLPutData</legacyBold> and in the buffer specified with the <legacyItalic>StrLen_or_IndPtr</legacyItalic> argument in <legacyBold>SQLBindParameter</legacyBold>. The data buffer is specified with the <legacyItalic>DataPtr</legacyItalic> argument in <legacyBold>SQLPutData</legacyBold> and the <legacyItalic>ParameterValuePtr</legacyItalic> argument in <legacyBold>SQLBindParameter</legacyBold>.</para>
  </introduction>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>