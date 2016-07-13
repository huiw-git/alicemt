---
title: Compatibility Matrix
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0690b463-15a1-48fa-9d0b-9cc9e5bf7fc6
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Compatibility Matrix
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The following table describes the compatibility of the types of applications and drivers defined previously in this section.</para>
    <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
      <thead>
        <tr>
          <TD>
            <para>Application type</para>
            <para>and version</para>
          </TD>
          <TD>
            <para>32-bit ODBC</para>
            <para>2.<legacyItalic>x </legacyItalic>driver</para>
          </TD>
          <TD>
            <para>ODBC 3.<legacyItalic>x</legacyItalic></para>
            <para>driver</para>
          </TD>
          <TD>
            <para>ODBC 3.8 driver</para>
          </TD>
          <TD>
            <para>ISO and Open Group–compliant driver</para>
          </TD>
        </tr>
      </thead>
      <tbody>
        <tr>
          <TD>
            <para>16-bit application, any version</para>
          </TD>
          <TD>
            <para>Compatible</para>
          </TD>
          <TD>
            <para>Compatible</para>
          </TD>
          <TD>
            <para>Compatible</para>
          </TD>
          <TD>
            <para>Compatible</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>Pure 2.<legacyItalic>x </legacyItalic>application </para>
          </TD>
          <TD>
            <para>Compatible</para>
          </TD>
          <TD>
            <para>Compatible</para>
          </TD>
          <TD>
            <para>Compatible</para>
          </TD>
          <TD>
            <para>Not compatible[3]</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>Pure 2.<legacyItalic>x </legacyItalic>recompiled application </para>
          </TD>
          <TD>
            <para>Compatible</para>
          </TD>
          <TD>
            <para>Compatible[1]</para>
          </TD>
          <TD>
            <para>Compatible[1]</para>
          </TD>
          <TD>
            <para>Not compatible[3]</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>Pure 2.<legacyItalic>x </legacyItalic>Unicode application </para>
          </TD>
          <TD>
            <para>Compatible</para>
          </TD>
          <TD>
            <para>Compatible[1]</para>
          </TD>
          <TD>
            <para>Compatible[1]</para>
          </TD>
          <TD>
            <para>Not Compatible[3]</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>Pure Open Group and ISO–compliant application </para>
          </TD>
          <TD>
            <para>Not compatible</para>
          </TD>
          <TD>
            <para>Compatible[2]</para>
          </TD>
          <TD>
            <para>Compatible[2]</para>
          </TD>
          <TD>
            <para>Compatible[2]</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>Pure 3.0 application </para>
          </TD>
          <TD>
            <para>Not compatible</para>
          </TD>
          <TD>
            <para>Compatible</para>
          </TD>
          <TD>
            <para>Compatible</para>
          </TD>
          <TD>
            <para>Not compatible[4]</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>Pure 3.5 application </para>
          </TD>
          <TD>
            <para>Not compatible</para>
          </TD>
          <TD>
            <para>Compatible</para>
          </TD>
          <TD>
            <para>Compatible</para>
          </TD>
          <TD>
            <para>Not compatible[4]</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>Pure 3.8 (or higher) application</para>
          </TD>
          <TD>
            <para>Not compatible [5]</para>
          </TD>
          <TD>
            <para>Not compatible [5]</para>
          </TD>
          <TD>
            <para>Compatible</para>
          </TD>
          <TD>
            <para>Not compatible [4]</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>Replaced application </para>
          </TD>
          <TD>
            <para>Compatible</para>
          </TD>
          <TD>
            <para>Compatible</para>
          </TD>
          <TD>
            <para>Compatible</para>
          </TD>
          <TD>
            <para>Not compatible[3]</para>
          </TD>
        </tr>
      </tbody>
    </table>
    <para>[1]   The application must recompile using ODBC 3.5 (or higher) headers with the UNICODE option (if it is a Unicode application) and must set ODBCVER to 0x0250.</para>
    <para>[2]   The application must compile using ODBC 3.5 (or higher)headers and link with the ODBC Driver Manager. It must also set the header flag ODBC_STD.</para>
    <para>[3]   This configuration can potentially fail to work because there are features in ODBC 2.<legacyItalic>x</legacyItalic> that are not in the standards, such as bookmarks.</para>
    <para>[4]   This configuration can potentially fail to work because there are features in ODBC 3<legacyItalic>.x</legacyItalic> that are not in the standards, such as bookmarks.</para>
    <para>[5]   This configuration can potentially fail because there are features in ODBC 3.8 that are not in ODBC 2.x or 3.x drivers, such as driver-specific <link xlink:href="c91bef31-3794-4736-966a-d50997b2233c">C Data Types in ODBC</link>.</para>
  </introduction>
  <section>
    <title>Driver Manager Compatibility</title>
    <content>
      <para>An ODBC 3.0 application that must operate with all Driver Manager versions should do the following on startup:</para>
      <list class="bullet">
        <listItem>
          <para>Allocate an environment handle.</para>
        </listItem>
        <listItem>
          <para>Set the SQL_ATTR_ODBC_VERSION environment attribute to SQL_OV_ODBC3_80. If the Driver Manager returns SQL_ERROR, the Driver Manager is older than 3.8. Reset SQL_ATTR_ODBC_VERSION to SQL_OV_ODBC3 or SQL_OV_ODBC2, as appropriate, to correspond to the Driver Manager.</para>
        </listItem>
        <listItem>
          <para>Allocate a connection handle.</para>
        </listItem>
        <listItem>
          <para>Make a connection.</para>
        </listItem>
        <listItem>
          <para>Call SQLGetInfo for SQL_DRIVER_ODBC_VER to determine the driver version. If the driver is an ODBC 3.8 driver, you can use driver-specific C types. Otherwise, do not use driver-specific C data types.</para>
        </listItem>
      </list>
      <para>Note that a recompiled ODBC 3.x application can use ODBC 3.8 features other than driver-specific C types without specifying SQL_OV_ODBC3_80 for SQL_ATTR_ODBC_VERSION. This is similar to a recompiled ODBC 2.x application using ODBC 3.x features.</para>
    </content>
  </section>
  <section>
    <title>Using SQLCancelHandle in an Application Compatible with all Driver Managers</title>
    <content>
      <para>Because <legacyLink xlink:href="16049b5b-22a7-4640-9897-c25dd0f19d21">SQLCancelHandle Function</legacyLink> is not supported in Driver Managers that were released before Windows 7, an application cannot be loaded in older versions of Windows if it calls <unmanagedCodeEntityReference>SQLCancelHandle</unmanagedCodeEntityReference> directly. To work with all versions of Driver Managers and use <unmanagedCodeEntityReference>SQLCancelHandle</unmanagedCodeEntityReference> on new versions of Windows, an application should call <unmanagedCodeEntityReference>SQLCancelHandle</unmanagedCodeEntityReference> indirectly by using <unmanagedCodeEntityReference>LoadLibrary</unmanagedCodeEntityReference> and <unmanagedCodeEntityReference>GetProcAddress.</unmanagedCodeEntityReference></para>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="854f0bb4-17e9-489b-9595-eefffb8ba99f">What's New in ODBC 3.8</link>
</relatedTopics>
</developerConceptualDocument>