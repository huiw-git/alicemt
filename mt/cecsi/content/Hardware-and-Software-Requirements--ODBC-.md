---
title: Hardware and Software Requirements (ODBC)
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6df2e9cd-de10-4629-97bd-32f2782616c7
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Hardware and Software Requirements (ODBC)
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This topic lists requirements for using the ODBC Desktop Database Drivers.</para>
  </introduction>
  <section>
    <title>Hardware Requirements</title>
    <content>
      <para>To use the ODBC Desktop Database Drivers, you must have:  </para>
      <list class="bullet">
        <listItem>
          <para>An IBM-compatible personal computer. </para>
        </listItem>
        <listItem>
          <para>A hard disk with 6 MB of free disk space.</para>
        </listItem>
        <listItem>
          <para>At least 16 MB of random-access memory (RAM).</para>
        </listItem>
      </list>
    </content>
  </section>
  <section>
    <title>Software Requirements</title>
    <content>
      <para>To access data with an ODBC driver, you must have:  </para>
      <list class="bullet">
        <listItem>
          <para>The ODBC driver. </para>
        </listItem>
        <listItem>
          <para>The 32-bit ODBC Driver Manager, version 3.51 or later (Odbc32.dll). </para>
        </listItem>
        <listItem>
          <para>Microsoft Windows 95 or later, or Windows NT 4.0 or Windows 2000.</para>
        </listItem>
        <listItem>
          <para>A stack size of at least 20 KB for an application using a Microsoft ODBC driver.</para>
        </listItem>
      </list>
      <para>When using Microsoft Windows NT 4.0 or Windows 2000, the 32-bit driver is thread-safe, but only through the use of a global semaphore that controls access to the driver. Concurrent use of the driver is very limited under Windows NT. All access to the Jet ISAM layer will be single-threaded for all applications using the Microsoft Jet engine.</para>
      <para>When running multiple 16-bit applications on Windows on Windows (WOW) on Microsoft Windows NT 4.0, the applications must be run in separate memory spaces. (The same memory space cannot be used because ODBC does not support multiple environments in the same process.) To run an application in a separate memory space, select the application's icon in the Program Manager, open the <legacyBold>File</legacyBold> menu and click <legacyBold>Properties</legacyBold>, and then click <legacyBold>Run In Separate Memory Space</legacyBold>.</para>
      <para>The use of these drivers by 16-bit applications on Windows 95 is not supported.</para>
    </content>
  </section>
  <section>
    <title>Driver-Specific Hardware and Software Requirements</title>
    <content>
      <list class="bullet">
        <listItem>
          <para>The MicrosoftAccess and dBASEdrivers may require changes in the Autoexec.bat or Config.sys files.</para>
        </listItem>
      </list>
    </content>
  </section>
  <relatedTopics />
</developerConceptualDocument>