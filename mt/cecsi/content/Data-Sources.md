---
title: Data Sources
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4ae44fa2-0b9b-4e19-ab45-c1dc93b68406
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Data Sources
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>A <legacyItalic>data source</legacyItalic> is simply the source of the data. It can be a file, a particular database on a DBMS, or even a live data feed. The data might be located on the same computer as the program, or on another computer somewhere on a network. For example, a data source might be an Oracle DBMS running on an OS/2® operating system, accessed by Novell® Netware; an IBM DB2 DBMS accessed through a gateway; a collection of Xbase files in a server directory; or a local Microsoft® Access database file.</para>
    <para>The purpose of a data source is to gather all of the technical information needed to access the data — the driver name, network address, network software, and so on — into a single place and hide it from the user. The user should be able to look at a list that includes Payroll, Inventory, and Personnel, choose Payroll from the list, and have the application connect to the payroll data, all without knowing where the payroll data resides or how the application got to it.</para>
    <para>The term <legacyItalic>data source</legacyItalic> should not be confused with similar terms. In this manual, <legacyItalic>DBMS</legacyItalic> or <legacyItalic>database</legacyItalic> refers to a database program or engine. A further distinction is made between <legacyItalic>desktop databases,</legacyItalic> designed to run on personal computers and often lacking in full SQL and transaction support, and <legacyItalic>server databases,</legacyItalic> designed to run in a client/server situation and characterized by a stand-alone database engine and rich SQL and transaction support. <legacyItalic>Database</legacyItalic> also refers to a particular collection of data, such as a collection of Xbase files in a directory or a database on SQL Server. It is generally equivalent to the term <legacyItalic>catalog,</legacyItalic> used elsewhere in this manual, or the term <legacyItalic>qualifier</legacyItalic> in earlier versions of ODBC.</para>
    <para>This section contains the following topics.  </para>
    <list class="bullet">
      <listItem>
        <para>             <legacyLink xlink:href="a5e3f966-3357-4827-afbc-6153682d26bc">Types of Data Sources</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="d5550619-22b2-4b16-bd08-fbabb6554c40">Using Data Sources</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="cbf15f32-0550-4c74-8088-8f7ac3855469">Data Source Example</legacyLink>           </para>
      </listItem>
    </list>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>