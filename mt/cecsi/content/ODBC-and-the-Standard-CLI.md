---
title: ODBC and the Standard CLI
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 79b9c268-16ac-4b80-b451-f9dcd8c02ca4
manager:jhubbard
translation.priority.ht: 
  - en-gb
---
# ODBC and the Standard CLI
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>ODBC aligns with the following specifications and standards that deal with the Call-Level Interface (CLI). (The ODBC features are a superset of each of these standards.)  </para>
    <list class="bullet">
      <listItem>
        <para>The Open Group CAE Specification "Data Management: SQL Call-Level Interface (CLI)"</para>
      </listItem>
      <listItem>
        <para>ISO/IEC 9075-3:1995 (E) Call-Level Interface (SQL/CLI)</para>
      </listItem>
    </list>
    <para>As a result of this alignment, the following are true:  </para>
    <list class="bullet">
      <listItem>
        <para>An application written to the Open Group and ISO CLI specifications will work with an ODBC 3.<legacyItalic>x</legacyItalic> driver or a standards-compliant driver when it is compiled with the ODBC 3.<legacyItalic>x</legacyItalic> header files and linked with ODBC 3.<legacyItalic>x</legacyItalic> libraries, and when it gains access to the driver through the ODBC 3.<legacyItalic>x</legacyItalic> Driver Manager.</para>
      </listItem>
      <listItem>
        <para>A driver written to the Open Group and ISO CLI specifications will work with an ODBC 3<legacyItalic>.x</legacyItalic> application or a standards-compliant application when it is compiled with the ODBC 3<legacyItalic>.x</legacyItalic> header files and linked with ODBC 3<legacyItalic>.x</legacyItalic> libraries, and when the application gains access to the driver through the ODBC 3<legacyItalic>.x</legacyItalic> Driver Manager. (For more information, see <legacyLink xlink:href="a1145c4c-3094-4f3f-8cc2-e6bb1a930ab1">Standards-Compliant Applications and Drivers</legacyLink>.</para>
      </listItem>
    </list>
    <para>The Core interface conformance level encompasses all the features in the ISO CLI and all the nonoptional features in the Open Group CLI. Optional features of the Open Group CLI appear in higher interface conformance levels. Because all ODBC 3.<legacyItalic>x</legacyItalic> drivers are required to support the features in the Core interface conformance level, the following are true:  </para>
    <list class="bullet">
      <listItem>
        <para>An ODBC 3.<legacyItalic>x</legacyItalic> driver will support all the features used by a standards-compliant application.</para>
      </listItem>
      <listItem>
        <para>An ODBC 3.<legacyItalic>x</legacyItalic> application using only the features in ISO CLI and the nonoptional features of the Open Group CLI will work with any standards-compliant driver.</para>
      </listItem>
    </list>
    <para>In addition to the call-level interface specifications contained in the ISO/IEC and Open Group CLI standards, ODBC implements the following features. (Some of these features existed in versions of ODBC prior to ODBC 3.<legacyItalic>x</legacyItalic>.)  </para>
    <list class="bullet">
      <listItem>
        <para>Multirow fetches by a single function call</para>
      </listItem>
      <listItem>
        <para>Binding to an array of parameters</para>
      </listItem>
      <listItem>
        <para>Bookmark support including fetching by bookmark, variable-length bookmarks, and bulk update and delete by bookmark operations on discontiguous rows</para>
      </listItem>
      <listItem>
        <para>Row-wise binding</para>
      </listItem>
      <listItem>
        <para>Binding offsets</para>
      </listItem>
      <listItem>
        <para>Support for batches of SQL statements, either in a stored procedure or as a sequence of SQL statements executed through <legacyBold>SQLExecute</legacyBold> or <legacyBold>SQLExecDirect</legacyBold></para>
      </listItem>
      <listItem>
        <para>Exact or approximate cursor row counts</para>
      </listItem>
      <listItem>
        <para>Positioned update and delete operations and batched updates and deletes by function call (<legacyBold>SQLSetPos</legacyBold>)</para>
      </listItem>
      <listItem>
        <para>Catalog functions that extract information from the information schema without the need for supporting information schema views</para>
      </listItem>
      <listItem>
        <para>Escape sequences for outer joins, scalar functions, datetime literals, interval literals, and stored procedures</para>
      </listItem>
      <listItem>
        <para>Code-page translation libraries</para>
      </listItem>
      <listItem>
        <para>Reporting of a driver's ANSI-conformance level and SQL support</para>
      </listItem>
      <listItem>
        <para>On-demand automatic population of implementation parameter descriptor</para>
      </listItem>
      <listItem>
        <para>Enhanced diagnostics and row and parameter status arrays</para>
      </listItem>
      <listItem>
        <para>Datetime, interval, numeric/decimal, and 64-bit integer application buffer types</para>
      </listItem>
      <listItem>
        <para>Asynchronous execution</para>
      </listItem>
      <listItem>
        <para>Stored procedure support, including escape sequences, output parameter binding mechanisms, and catalog functions</para>
      </listItem>
      <listItem>
        <para>Connection enhancements including support for connection attributes and attribute browsing</para>
      </listItem>
    </list>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>