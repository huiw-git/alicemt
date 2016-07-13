---
title: History of the Desktop Database Drivers
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b4a2aff8-bde7-4bd5-8580-bc50f27311c8
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# History of the Desktop Database Drivers
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The following table shows the Desktop Database Drivers version history.</para>
    <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
      <thead>
        <tr>
          <TD>
            <para>Version</para>
          </TD>
          <TD>
            <para>Release Date</para>
          </TD>
          <TD>
            <para>Description</para>
          </TD>
        </tr>
      </thead>
      <tbody>
        <tr>
          <TD>
            <para>1.0</para>
          </TD>
          <TD>
            <para>August 1993</para>
          </TD>
          <TD>
            <para>Used the SIMBA query processor produced by PageAhead Software. SIMBA received ODBC calls and SQL statements, processed them into Microsoft Jet installable ISAM calls, and then called the Microsoft Jet ISAM dispatch layer to load and call the appropriate installable ISAM driver.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>2.0</para>
          </TD>
          <TD>
            <para>December 1994</para>
          </TD>
          <TD>
            <para>Used with ODBC 2.0, which significantly expanded ODBC functionality. The major change in version 2.0 was that the Microsoft Jet database engine replaced the SIMBA query processor. With the Microsoft Jet database engine, the Desktop Database Drivers integrated much more tightly with the Microsoft Jet installable ISAM drivers and Microsoft Access technology. Significant enhancements were:</para>
            <list class="bullet">
              <listItem>
                <para>Native support for scrollable cursors.</para>
              </listItem>
              <listItem>
                <para>Native support for outer joins, updatable and heterogeneous joins, and transactions.</para>
              </listItem>
              <listItem>
                <para>32-bit versions of the drivers for Microsoft Windows NT.</para>
              </listItem>
            </list>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>3.0</para>
          </TD>
          <TD>
            <para>October 1995</para>
          </TD>
          <TD>
            <para>Provided support for Windows 95 and Windows NT Workstation or NT Server 3.51. Only 32-bit drivers were included in this release; the 16-bit drivers for Windows version 3.1 were removed.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>3.5</para>
          </TD>
          <TD>
            <para>October 1996</para>
          </TD>
          <TD>
            <para>These drivers were double-byte character set (DBCS)-enabled, were better suited for use with Internet applications than previous versions, and accommodated the use of File data source names (DSNs). The Microsoft Access driver was released in an RISC version for use on Alpha platforms for Windows 95/98 and Windows NT 3.51 and later operating systems. </para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>4.0</para>
          </TD>
          <TD>
            <para>Late 1998</para>
          </TD>
          <TD>
            <para>Provides support for Microsoft Jet Engine Unicode format along with compatibility for ANSI format of earlier versions.</para>
          </TD>
        </tr>
      </tbody>
    </table>
    <alert class="note">
      <para>The version3.5 drivers were designed to work with ODBC2.<legacyItalic>x</legacyItalic>. Although they also work with ODBC 3.0, they do not support all ODBC 3.0 features. For more information about how these drivers work with ODBC 3.0, see <legacyLink xlink:href="b5eee7be-28ed-4467-8cf1-2205e2010a53">Backward Compatibility and Standards Compliance</legacyLink>.</para>
    </alert>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>