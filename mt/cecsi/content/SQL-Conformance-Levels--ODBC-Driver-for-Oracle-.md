---
title: "SQL Conformance Levels (ODBC Driver for Oracle)"
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 077a6c6a-2c57-42c9-a4fd-4cf0e65cf7e2
caps.latest.revision: 7
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# SQL Conformance Levels (ODBC Driver for Oracle)
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <alert class="important">
      <para>This feature will be removed in a future version of Windows. Avoid using this feature in new development work, and plan to modify applications that currently use this feature. Instead, use the ODBC driver provided by Oracle.</para>
    </alert>
    <para>The ODBC Driver for Oracle supports the Minimum SQL grammar and Core SQL grammar and also supports the following ODBC extensions to SQL:  </para>
    <list class="bullet">
      <listItem>
        <para>Date, time, and timestamp data</para>
      </listItem>
      <listItem>
        <para>Left and right outer joins</para>
      </listItem>
      <listItem>
        <para>Numeric functions:</para>
        <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
          <tbody>
            <tr>
              <TD>
                <para>Abs</para>
              </TD>
              <TD>
                <para>Log</para>
              </TD>
              <TD>
                <para>round</para>
              </TD>
              <TD>
                <para>tan</para>
              </TD>
            </tr>
            <tr>
              <TD>
                <para>Ceiling</para>
              </TD>
              <TD>
                <para>Log10</para>
              </TD>
              <TD>
                <para>second</para>
              </TD>
              <TD>
                <para>truncate</para>
              </TD>
            </tr>
            <tr>
              <TD>
                <para>Cos</para>
              </TD>
              <TD>
                <para>Mod</para>
              </TD>
              <TD>
                <para>sign</para>
              </TD>
              <TD>
                <para> </para>
              </TD>
            </tr>
            <tr>
              <TD>
                <para>Exp</para>
              </TD>
              <TD>
                <para>Pi</para>
              </TD>
              <TD>
                <para>sin</para>
              </TD>
              <TD>
                <para> </para>
              </TD>
            </tr>
            <tr>
              <TD>
                <para>Floor</para>
              </TD>
              <TD>
                <para>Power</para>
              </TD>
              <TD>
                <para>sqrt</para>
              </TD>
              <TD>
                <para> </para>
              </TD>
            </tr>
          </tbody>
        </table>
      </listItem>
      <listItem>
        <para>Date functions:</para>
        <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
          <tbody>
            <tr>
              <TD>
                <para>Curdate</para>
              </TD>
              <TD>
                <para>Dayofweek</para>
              </TD>
              <TD>
                <para>monthname</para>
              </TD>
              <TD>
                <para>second</para>
              </TD>
            </tr>
            <tr>
              <TD>
                <para>Curtime</para>
              </TD>
              <TD>
                <para>Dayofyear</para>
              </TD>
              <TD>
                <para>minute</para>
              </TD>
              <TD>
                <para>week</para>
              </TD>
            </tr>
            <tr>
              <TD>
                <para>Dayname</para>
              </TD>
              <TD>
                <para>Hour</para>
              </TD>
              <TD>
                <para>now</para>
              </TD>
              <TD>
                <para>year</para>
              </TD>
            </tr>
            <tr>
              <TD>
                <para>Dayofmonth</para>
              </TD>
              <TD>
                <para>Month</para>
              </TD>
              <TD>
                <para>quarter</para>
              </TD>
              <TD>
                <para> </para>
              </TD>
            </tr>
          </tbody>
        </table>
      </listItem>
      <listItem>
        <para>String functions:</para>
        <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
          <tbody>
            <tr>
              <TD>
                <para>Ascii</para>
              </TD>
              <TD>
                <para>Left</para>
              </TD>
              <TD>
                <para>right</para>
              </TD>
              <TD>
                <para>ucase</para>
              </TD>
            </tr>
            <tr>
              <TD>
                <para>Char</para>
              </TD>
              <TD>
                <para>Length</para>
              </TD>
              <TD>
                <para>rtrim</para>
              </TD>
              <TD>
                <para> </para>
              </TD>
            </tr>
            <tr>
              <TD>
                <para>Concat</para>
              </TD>
              <TD>
                <para>Ltrim</para>
              </TD>
              <TD>
                <para>soundex</para>
              </TD>
              <TD>
                <para> </para>
              </TD>
            </tr>
            <tr>
              <TD>
                <para>Lcase</para>
              </TD>
              <TD>
                <para>Replace</para>
              </TD>
              <TD>
                <para>substring</para>
              </TD>
              <TD>
                <para> </para>
              </TD>
            </tr>
          </tbody>
        </table>
      </listItem>
      <listItem>
        <para>Type-conversion function:</para>
        <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
          <tbody>
            <tr>
              <TD>
                <para>Convert</para>
              </TD>
            </tr>
          </tbody>
        </table>
      </listItem>
      <listItem>
        <para>System functions:</para>
        <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
          <tbody>
            <tr>
              <TD>
                <para>Ifnull</para>
              </TD>
            </tr>
            <tr>
              <TD>
                <para>User</para>
              </TD>
            </tr>
          </tbody>
        </table>
      </listItem>
    </list>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>