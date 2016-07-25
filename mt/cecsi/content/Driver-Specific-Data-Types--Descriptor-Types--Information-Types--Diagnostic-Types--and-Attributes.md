---
title: "Driver-Specific Data Types, Descriptor Types, Information Types, Diagnostic Types, and Attributes"
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ad4c76d3-5191-4262-b47c-5dd1d19d1154
caps.latest.revision: 18
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Driver-Specific Data Types, Descriptor Types, Information Types, Diagnostic Types, and Attributes
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Drivers can allocate driver-specific values for the following:</para>
    <list class="bullet">
      <listItem>
        <para>
          <legacyBold>SQL Data Type Indicators</legacyBold> These are used in <legacyItalic>ParameterType</legacyItalic> in <legacyBold>SQLBindParameter</legacyBold> and in <legacyItalic>DataType</legacyItalic> in <legacyBold>SQLGetTypeInfo</legacyBold> and returned by <legacyBold>SQLColAttribute</legacyBold>, <legacyBold>SQLColumns</legacyBold>, <legacyBold>SQLDescribeCol</legacyBold>, <legacyBold>SQLGetTypeInfo</legacyBold>, <legacyBold>SQLDescribeParam</legacyBold>, <legacyBold>SQLProcedureColumns</legacyBold>, and <legacyBold>SQLSpecialColumns</legacyBold>.</para>
      </listItem>
      <listItem>
        <para>
          <legacyBold>Descriptor Fields</legacyBold> These are used in <legacyItalic>FieldIdentifier</legacyItalic> in <legacyBold>SQLColAttribute</legacyBold>, <legacyBold>SQLGetDescField</legacyBold>, and <legacyBold>SQLSetDescField</legacyBold>.</para>
      </listItem>
      <listItem>
        <para>
          <legacyBold>Diagnostic Fields</legacyBold> These are used in <legacyItalic>DiagIdentifier</legacyItalic> in <legacyBold>SQLGetDiagField</legacyBold> and <legacyBold>SQLGetDiagRec</legacyBold>.</para>
      </listItem>
      <listItem>
        <para>
          <legacyBold>Information Types</legacyBold> These are used in <legacyItalic>InfoType</legacyItalic> in <legacyBold>SQLGetInfo</legacyBold>.</para>
      </listItem>
      <listItem>
        <para>
          <legacyBold>Connection and Statement Attributes</legacyBold> These are used in <legacyItalic>Attribute</legacyItalic> in <legacyBold>SQLGetConnectAttr</legacyBold>, <legacyBold>SQLGetStmtAttr</legacyBold>, <legacyBold>SQLSetConnectAttr</legacyBold>, and <legacyBold>SQLSetStmtAttr</legacyBold>.</para>
      </listItem>
    </list>
    <para>For each of these items, there are two sets of values: values reserved for use by ODBC, and values reserved for use by drivers. Before implementing driver-specific values, a driver writer must request a value for each driver-specific type, field, or attribute from Open Group. For new driver development, use the range described in the table below. The ODBC 3.8 Driver Manager will not generate an error if an unknown value is used that is not in the range described below. However, later versions of the Driver Manager might generate an error if unknown values are received that are not in the range.</para>
    <para>When any of these values is passed to an ODBC function, the driver must check whether the value is valid. Drivers return SQLSTATE HYC00 (Optional feature not implemented) for driver-specific values that apply to other drivers.</para>
    <para>Starting with ODBC 3.8, driver writers can allocate driver-specific attributes within a reserved range.</para>
    <alert class="note">
      <para>The ODBC 3.8 Driver Manager neither validates nor enforces these ranges for backward compatibility. A future version of the Driver Manager might enforce them, however.</para>
    </alert>
    <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
      <thead>
        <tr>
          <TD>
            <para>Attribute type</para>
          </TD>
          <TD>
            <para>ODBC data type</para>
          </TD>
          <TD>
            <para>Driver-specific range base</para>
          </TD>
          <TD>
            <para>Driver-specific range limit</para>
          </TD>
          <TD>
            <para>ODBC constant for driver-specific value range base</para>
          </TD>
        </tr>
      </thead>
      <tbody>
        <tr>
          <TD>
            <para>SQL data type indicators</para>
          </TD>
          <TD>
            <para>SQLSMALLINT</para>
          </TD>
          <TD>
            <para>0x4000</para>
          </TD>
          <TD>
            <para>0x7FFF</para>
          </TD>
          <TD>
            <para>SQL_DRIVER_SQL_TYPE_BASE</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>Descriptor fields</para>
          </TD>
          <TD>
            <para>SQLSMALLINT</para>
          </TD>
          <TD>
            <para>0x4000</para>
          </TD>
          <TD>
            <para>0x7FFF</para>
          </TD>
          <TD>
            <para>SQL_DRIVER_DESCRIPTOR_BASE</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>Diagnostic fields</para>
          </TD>
          <TD>
            <para>SQLSMALLINT</para>
          </TD>
          <TD>
            <para>0x4000</para>
          </TD>
          <TD>
            <para>0x7FFF</para>
          </TD>
          <TD>
            <para>SQL_DRIVER_DIAGNOSTIC_BASE</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>Information types</para>
          </TD>
          <TD>
            <para>SQLUSMALLINT</para>
          </TD>
          <TD>
            <para>0x4000</para>
          </TD>
          <TD>
            <para>0x7FFF</para>
          </TD>
          <TD>
            <para>SQL_DRIVER_INFO_TYPE_BASE</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>Connection attributes</para>
          </TD>
          <TD>
            <para>SQLINTEGER</para>
          </TD>
          <TD>
            <para>0x00004000</para>
          </TD>
          <TD>
            <para>0x00007FFF</para>
          </TD>
          <TD>
            <para>SQL_DRIVER_CONNECT_ATTR_BASE</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>Statement attributes</para>
          </TD>
          <TD>
            <para>SQLINTEGER</para>
          </TD>
          <TD>
            <para>0x00004000</para>
          </TD>
          <TD>
            <para>0x00007FFF</para>
          </TD>
          <TD>
            <para>SQL_DRIVER_STATEMENT_ATTR_BASE</para>
          </TD>
        </tr>
      </tbody>
    </table>
    <alert class="note">
      <para>Driver-specific data types, descriptor fields, diagnostic fields, information types, statement attributes, and connection attributes must be described in the driver documentation. When any of these values is passed to an ODBC function, the driver must check whether the value is valid. Drivers return SQLSTATE HYC00 (Optional feature not implemented) for driver-specific values that apply to other drivers.</para>
    </alert>
    <para>The base values are defined to facilitate driver development. For example, driver specific diagnostic attributes can be defined in the following format:</para>
    <code>SQL_DRIVER_DIAGNOSTIC_BASE+0, SQL_DRIVER_DIAGNOSTIC_BASE +1</code>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>