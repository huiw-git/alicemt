---
title: ODBC Driver for Oracle
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 937e0662-8b1d-44f7-b077-4015c6605b2c
translation.priority.ht: 
  - en-gb
---
# ODBC Driver for Oracle
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <alert class="important">
      <para>This feature will be removed in a future version of Windows. Avoid using this feature in new development work, and plan to modify applications that currently use this feature. Instead, use the ODBC driver provided by Oracle.</para>
    </alert>
    <para>The Microsoft® ODBC Driver for Oracle allows you to connect your ODBC-compliant application to an Oracle database. The ODBC Driver for Oracle conforms to the Open Database Connectivity (ODBC) specification described in the <legacyItalic>ODBC Programmer's Reference</legacyItalic>. It allows access to PL/SQL packages, XA/DTC integration, and Oracle access from within Internet Information Services (IIS).</para>
    <para>Oracle RDBMS is a multiuser relational database management system that runs with various workstation and minicomputer operating systems. IBM-compatible computers running Microsoft Windows can communicate with Oracle database servers over a network. Supported networks include Microsoft LAN Manager, NetWare, VINES, DECnet, and any network that supports TCP/IP.</para>
    <para>The ODBC Driver for Oracle enables an application to access data in an Oracle database through the ODBC interface. The driver can access local Oracle databases or it can communicate with the network through SQL*Net. The following diagram details this application and driver architecture.</para>
    <mediaLink>
      <image xlink:href="5be27e21-ad1f-4971-b669-fa105f67cdd2" />
    </mediaLink>
    <para>The ODBC Driver for Oracle complies with API Conformance Level 1 and SQL Conformance Level Core. It also supports some functions in API Conformance Level 2 and most of the grammar in the Core and Extended SQL conformance levels. The driver is ODBC 2.5 compliant and supports 32-bit systems. Oracle 7.3x is supported fully; Oracle8 has limited support. The ODBC Driver for Oracle does not support any of the new Oracle8 data types — Unicode data types, BLOBs, CLOBs, and so on — nor does it support Oracle's new Relational Object Model. For more information about supported data types, see <legacyLink xlink:href="21d5f8d9-a3aa-4aa4-bc37-ff8bc90c0870">Supported Data Types</legacyLink> in this guide.</para>
    <para>To access Oracle data, the following components are required:  </para>
    <list class="bullet">
      <listItem>
        <para>The ODBC Driver for Oracle</para>
      </listItem>
      <listItem>
        <para>An Oracle RDBMS database</para>
      </listItem>
      <listItem>
        <para>Oracle Client Software</para>
      </listItem>
    </list>
    <para>Additionally, for remote connections:  </para>
    <list class="bullet">
      <listItem>
        <para>A network that connects the computers that run the driver and the database. The network must support SQL*Net connections.</para>
      </listItem>
    </list>
  </introduction>
  <section>
    <title>Component Documentation</title>
    <content>
      <para>This guide contains detailed information about setting up and configuring the Microsoft ODBC Driver for Oracle and adding programmatic functionality. It also contains technical reference material.</para>
      <para>For information regarding specific Oracle product behavior, consult the documentation that accompanies the Oracle product.</para>
      <para>For information about setting up or configuring the Microsoft ODBC Driver for Oracle using the ODBC Data Source Administrator, see the <legacyLink xlink:href="a2f66b4c-a4ac-401b-8e95-d8f96332e0b5">ODBC Data Source Administrator</legacyLink> documentation.</para>
      <para>This section contains the following topics.</para>
      <list class="bullet">
        <listItem>
          <para>
            <legacyLink xlink:href="c506aaa1-0b4f-440b-b069-98e0a463a5f6">ODBC Driver for Oracle User's Guide</legacyLink>
          </para>
        </listItem>
        <listItem>
          <para>
            <legacyLink xlink:href="d70e79a1-6403-49ad-8713-eda6e8aa287e">ODBC Driver for Oracle Programmer's Reference</legacyLink>
          </para>
        </listItem>
      </list>
    </content>
  </section>
  <relatedTopics />
</developerConceptualDocument>