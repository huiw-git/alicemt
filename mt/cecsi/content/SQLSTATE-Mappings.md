---
title: SQLSTATE Mappings
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6e6cabcf-a204-40eb-b77d-8a0c4a5e8524
manager:jhubbard
translation.priority.ht: 
  - en-gb
---
# SQLSTATE Mappings
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This topic discusses SQLSTATE values for ODBC 2.<legacyItalic>x</legacyItalic> and ODBC 3.<legacyItalic>x</legacyItalic>. For more information on ODBC 3.<legacyItalic>x</legacyItalic> SQLSTATE values, see <link xlink:href="c06902e4-721d-42e2-b818-05f0e18e4ce0">Appendix A: ODBC Error Codes</link>.</para>
    <para>In ODBC 3.<legacyItalic>x</legacyItalic>, HYxxx SQLSTATEs are returned instead of S1xxx, and 42Sxx SQLSTATEs are returned instead of S00XX. This was done to align with Open Group and ISO standards. In many cases, the mapping is not one-to-one because the standards have redefined the interpretation of several SQLSTATEs.</para>
    <para>When an ODBC 2.<legacyItalic>x</legacyItalic> application is upgraded to an ODBC 3.<legacyItalic>x</legacyItalic> application, the application has to be changed to expect ODBC 3.<legacyItalic>x</legacyItalic> SQLSTATEs instead of ODBC 2.<legacyItalic>x</legacyItalic> SQLSTATEs. The following table lists the ODBC 3.<legacyItalic>x</legacyItalic> SQLSTATEs that each ODBC 2.<legacyItalic>x</legacyItalic> SQLSTATE is mapped to.</para>
    <para>When the SQL_ATTR_ODBC_VERSION environment attribute is set to SQL_OV_ODBC2, the driver posts ODBC 2.<legacyItalic>x</legacyItalic> SQLSTATEs instead of ODBC 3.<legacyItalic>x</legacyItalic> SQLSTATEs when <legacyBold>SQLGetDiagField</legacyBold> or <legacyBold>SQLGetDiagRec</legacyBold> is called. A specific mapping can be determined by noting the ODBC 2<legacyItalic>.x</legacyItalic> SQLSTATE in column 1 of the following table that corresponds to the ODBC 3.<legacyItalic>x</legacyItalic> SQLSTATE in column 2.</para>
    <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
      <thead>
        <tr>
          <TD>
            <para>ODBC 2.<legacyItalic>x</legacyItalic> SQLSTATE</para>
          </TD>
          <TD>
            <para>ODBC 3.<legacyItalic>x</legacyItalic> SQLSTATE</para>
          </TD>
          <TD>
            <para>Comments</para>
          </TD>
        </tr>
      </thead>
      <tbody>
        <tr>
          <TD>
            <para>01S03</para>
          </TD>
          <TD>
            <para>01001</para>
          </TD>
          <TD>
            <para> </para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>01S04</para>
          </TD>
          <TD>
            <para>01001</para>
          </TD>
          <TD>
            <para> </para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>22003</para>
          </TD>
          <TD>
            <para>HY019</para>
          </TD>
          <TD>
            <para> </para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>22008</para>
          </TD>
          <TD>
            <para>22007</para>
          </TD>
          <TD>
            <para> </para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>22005</para>
          </TD>
          <TD>
            <para>22018</para>
          </TD>
          <TD>
            <para> </para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>24000</para>
          </TD>
          <TD>
            <para>07005</para>
          </TD>
          <TD>
            <para> </para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>37000</para>
          </TD>
          <TD>
            <para>42000</para>
          </TD>
          <TD>
            <para> </para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>70100</para>
          </TD>
          <TD>
            <para>HY018</para>
          </TD>
          <TD>
            <para> </para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>S0001</para>
          </TD>
          <TD>
            <para>42S01</para>
          </TD>
          <TD>
            <para> </para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>S0002</para>
          </TD>
          <TD>
            <para>42S02</para>
          </TD>
          <TD>
            <para> </para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>S0011</para>
          </TD>
          <TD>
            <para>42S11</para>
          </TD>
          <TD>
            <para> </para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>S0012</para>
          </TD>
          <TD>
            <para>42S12</para>
          </TD>
          <TD>
            <para> </para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>S0021</para>
          </TD>
          <TD>
            <para>42S21</para>
          </TD>
          <TD>
            <para> </para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>S0022</para>
          </TD>
          <TD>
            <para>42S22</para>
          </TD>
          <TD>
            <para> </para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>S0023</para>
          </TD>
          <TD>
            <para>42S23</para>
          </TD>
          <TD>
            <para> </para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>S1000</para>
          </TD>
          <TD>
            <para>HY000</para>
          </TD>
          <TD>
            <para> </para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>S1001</para>
          </TD>
          <TD>
            <para>HY001</para>
          </TD>
          <TD>
            <para> </para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>S1002</para>
          </TD>
          <TD>
            <para>07009</para>
          </TD>
          <TD>
            <para>ODBC 2.<legacyItalic>x</legacyItalic> SQLSTATE S1002 is mapped to ODBC 3.<legacyItalic>x</legacyItalic> SQLSTATE 07009 if the underlying function is <legacyBold>SQLBindCol</legacyBold>, <legacyBold>SQLColAttribute</legacyBold>, <legacyBold>SQLExtendedFetch</legacyBold>, <legacyBold>SQLFetch</legacyBold>, <legacyBold>SQLFetchScroll</legacyBold>, or <legacyBold>SQLGetData</legacyBold>.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>S1003</para>
          </TD>
          <TD>
            <para>HY003</para>
          </TD>
          <TD>
            <para> </para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>S1004</para>
          </TD>
          <TD>
            <para>HY004</para>
          </TD>
          <TD>
            <para> </para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>S1008</para>
          </TD>
          <TD>
            <para>HY008</para>
          </TD>
          <TD>
            <para> </para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>S1009</para>
          </TD>
          <TD>
            <para>HY009</para>
          </TD>
          <TD>
            <para>Returned for an invalid use of a null pointer.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>S1009</para>
          </TD>
          <TD>
            <para>HY024</para>
          </TD>
          <TD>
            <para>Returned for an invalid attribute value.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>S1009</para>
          </TD>
          <TD>
            <para>HY092</para>
          </TD>
          <TD>
            <para>Returned for updating or deleting data by a call to <legacyBold>SQLSetPos</legacyBold>, or adding, updating, or deleting data by a call to <legacyBold>SQLBulkOperations</legacyBold>, when the concurrency is read-only.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>S1010</para>
          </TD>
          <TD>
            <para>HY007 HY010</para>
          </TD>
          <TD>
            <para>SQLSTATE S1010 is mapped to SQLSTATE HY007 when <legacyBold>SQLDescribeCol</legacyBold> is called prior to calling <legacyBold>SQLPrepare</legacyBold>, <legacyBold>SQLExecDirect</legacyBold>, or a catalog function for the <legacyItalic>StatementHandle</legacyItalic>. Otherwise, SQLSTATE S1010 is mapped to SQLSTATE HY010.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>S1011</para>
          </TD>
          <TD>
            <para>HY011</para>
          </TD>
          <TD>
            <para> </para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>S1012</para>
          </TD>
          <TD>
            <para>HY012</para>
          </TD>
          <TD>
            <para> </para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>S1090</para>
          </TD>
          <TD>
            <para>HY090</para>
          </TD>
          <TD>
            <para> </para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>S1091</para>
          </TD>
          <TD>
            <para>HY091</para>
          </TD>
          <TD>
            <para> </para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>S1092</para>
          </TD>
          <TD>
            <para>HY092</para>
          </TD>
          <TD>
            <para> </para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>S1093</para>
          </TD>
          <TD>
            <para>07009</para>
          </TD>
          <TD>
            <para>ODBC 3.<legacyItalic>x</legacyItalic> SQLSTATE 07009 is mapped to ODBC 2.<legacyItalic>x</legacyItalic> SQLSTATE S1093 if the underlying function is <legacyBold>SQLBindParameter</legacyBold> or <legacyBold>SQLDescribeParam</legacyBold>.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>S1096</para>
          </TD>
          <TD>
            <para>HY096</para>
          </TD>
          <TD>
            <para> </para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>S1097</para>
          </TD>
          <TD>
            <para>HY097</para>
          </TD>
          <TD>
            <para> </para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>S1098</para>
          </TD>
          <TD>
            <para>HY098</para>
          </TD>
          <TD>
            <para> </para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>S1099</para>
          </TD>
          <TD>
            <para>HY099</para>
          </TD>
          <TD>
            <para> </para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>S1100</para>
          </TD>
          <TD>
            <para>HY100</para>
          </TD>
          <TD>
            <para> </para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>S1101</para>
          </TD>
          <TD>
            <para>HY101</para>
          </TD>
          <TD>
            <para> </para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>S1103</para>
          </TD>
          <TD>
            <para>HY103</para>
          </TD>
          <TD>
            <para> </para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>S1104</para>
          </TD>
          <TD>
            <para>HY104</para>
          </TD>
          <TD>
            <para> </para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>S1105</para>
          </TD>
          <TD>
            <para>HY105</para>
          </TD>
          <TD>
            <para> </para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>S1106</para>
          </TD>
          <TD>
            <para>HY106</para>
          </TD>
          <TD>
            <para> </para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>S1107</para>
          </TD>
          <TD>
            <para>HY107</para>
          </TD>
          <TD>
            <para> </para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>S1108</para>
          </TD>
          <TD>
            <para>HY108</para>
          </TD>
          <TD>
            <para> </para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>S1109</para>
          </TD>
          <TD>
            <para>HY109</para>
          </TD>
          <TD>
            <para> </para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>S1110</para>
          </TD>
          <TD>
            <para>HY110</para>
          </TD>
          <TD>
            <para> </para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>S1111</para>
          </TD>
          <TD>
            <para>HY111</para>
          </TD>
          <TD>
            <para> </para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>S1C00</para>
          </TD>
          <TD>
            <para>HYC00</para>
          </TD>
          <TD>
            <para> </para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>S1T00</para>
          </TD>
          <TD>
            <para>HYT00</para>
          </TD>
          <TD>
            <para> </para>
          </TD>
        </tr>
      </tbody>
    </table>
    <alert class="note">
      <para>ODBC 3.<legacyItalic>x</legacyItalic> SQLSTATE 07008 is mapped to ODBC 2.<legacyItalic>x</legacyItalic> SQLSTATE S1000.</para>
    </alert>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>