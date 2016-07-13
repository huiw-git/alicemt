---
title: Time and Date Functions (Visual FoxPro ODBC Driver)
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c1fb63b7-af50-45d6-8dec-ae6ea7119527
manager: jhubbard
---
# Time and Date Functions (Visual FoxPro ODBC Driver)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The following table lists ODBC time and date functions supported by the Visual FoxPro ODBC Driver; when the Visual FoxPro grammar for the same function differs from the ODBC syntax, the Visual FoxPro equivalent is listed.</para>
    <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
      <thead>
        <tr>
          <TD>
            <para>ODBC grammar</para>
          </TD>
          <TD>
            <para>Visual FoxPro grammar</para>
          </TD>
        </tr>
      </thead>
      <tbody>
        <tr>
          <TD>
            <code>CURDATE<legacyItalic>( )</legacyItalic></code>
          </TD>
          <TD>
            <code>DATE<legacyItalic>( )</legacyItalic></code>
          </TD>
        </tr>
        <tr>
          <TD>
            <code>CURTIME<legacyItalic>( )</legacyItalic></code>
          </TD>
          <TD>
            <code>TIME<legacyItalic>( )</legacyItalic></code>
          </TD>
        </tr>
        <tr>
          <TD>
            <code>DAYNAME<legacyItalic>(date_exp)</legacyItalic></code>
          </TD>
          <TD>
            <code>CDOW<legacyItalic>(date_exp)</legacyItalic></code>
          </TD>
        </tr>
        <tr>
          <TD>
            <code>DAYOFMONTH(<legacyItalic>date_exp)</legacyItalic></code>
          </TD>
          <TD>
            <code>DAY<legacyItalic>( )</legacyItalic></code>
          </TD>
        </tr>
        <tr>
          <TD>
            <code>HOUR<legacyItalic>(time_exp)</legacyItalic></code>
          </TD>
          <TD>
            <code> </code>
          </TD>
        </tr>
        <tr>
          <TD>
            <code>MINUTE<legacyItalic>(time_exp)</legacyItalic></code>
          </TD>
          <TD>
            <code> </code>
          </TD>
        </tr>
        <tr>
          <TD>
            <code>MONTH<legacyItalic>(time_exp)</legacyItalic></code>
          </TD>
          <TD>
            <code> </code>
          </TD>
        </tr>
        <tr>
          <TD>
            <code>MONTHNAME<legacyItalic>(date_exp)</legacyItalic></code>
          </TD>
          <TD>
            <code>CMONTH<legacyItalic>(date_exp)</legacyItalic></code>
          </TD>
        </tr>
        <tr>
          <TD>
            <code>NOW<legacyItalic>( )</legacyItalic></code>
          </TD>
          <TD>
            <code>DATETIME<legacyItalic>( )</legacyItalic></code>
          </TD>
        </tr>
        <tr>
          <TD>
            <code>SECOND<legacyItalic>(time_exp)</legacyItalic></code>
          </TD>
          <TD>
            <code>SEC<legacyItalic>(time_exp)</legacyItalic></code>
          </TD>
        </tr>
        <tr>
          <TD>
            <code>WEEK<legacyItalic>(date_exp)</legacyItalic></code>
          </TD>
          <TD>
            <code> </code>
          </TD>
        </tr>
        <tr>
          <TD>
            <code>YEAR<legacyItalic>(date_exp)</legacyItalic></code>
          </TD>
          <TD>
            <code> </code>
          </TD>
        </tr>
      </tbody>
    </table>
    <para>The following time and date functions are not supported:</para>
    <para> DAYOFYEAR <legacyItalic>(date_exp)</legacyItalic></para>
    <para> QUARTER <legacyItalic>(date_exp)</legacyItalic></para>
    <para> TIMESTAMPADD <legacyItalic>(interval, integer_exp, timestamp_exp)</legacyItalic></para>
    <para> TIMESTAMPDIFF <legacyItalic>(interval, timestamp_exp1, timestamp_exp2)</legacyItalic></para>
  </introduction>
  <section>
    <title>ODBC Escape Sequences</title>
    <content>
      <para>The driver also supports the ODBC escape sequence for date and timestamp data. The escape clause syntax is as follows:</para>
      <code>--(*vendor(Microsoft),product(ODBC) d '<legacyItalic>value</legacyItalic>' *)—
--(*vendor(Microsoft),product(ODBC) ts ''<legacyItalic>value</legacyItalic>' *)—</code>
      <para>In this syntax, <legacyBold>d</legacyBold> indicates that <legacyItalic>value</legacyItalic> is a date in the <legacyItalic>yyyy-mm-dd</legacyItalic> format and <legacyBold>ts</legacyBold> indicates that <legacyItalic>value</legacyItalic> is a timestamp in the <legacyItalic>yyyy-mm-dd hh:mm:ss</legacyItalic>[.<legacyItalic>f...</legacyItalic>] format. The shorthand syntax for date and timestamp data is as follows:</para>
      <code>{d '<legacyItalic>value</legacyItalic>'}
{ts '<legacyItalic>value</legacyItalic>'}</code>
      <para>For example, each of the following statements updates the ALLTYPES table by using the date and timestamp shorthand syntax in a supported SQL UPDATE command:</para>
      <code>UPDATE alltypes
   SET DAT_COL={d'1968-04-28'}
   WHERE KEY=111

UPDATE alltypes
   SET DTI_COL={ts'1968-04-28 12:00:00'}
   WHERE KEY=111</code>
    </content>
  </section>
  <languageReferenceRemarks>
    <content>
      <para>For more information about escape sequences, see <legacyLink xlink:href="cf229f21-6c38-4b5b-aca8-f1be0dfeb3d0">Escape Sequences in ODBC</legacyLink> in the <legacyItalic>ODBC Programmer's Reference</legacyItalic>.</para>
    </content>
  </languageReferenceRemarks>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>