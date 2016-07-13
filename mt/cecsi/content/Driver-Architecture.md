---
title: Driver Architecture
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c5003413-0cc1-4f41-b877-a64e2f5ab118
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Driver Architecture
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Driver architecture falls into two categories, depending on which software processes SQL statements:  </para>
    <list class="bullet">
      <listItem>
        <para>
          <legacyBold>File-Based Drivers</legacyBold> The driver accesses the physical data directly. In this case, the driver acts as both driver and data source; that is, it processes ODBC calls and SQL statements. For example, dBASE drivers are file-based drivers because dBASE does not provide a stand-alone database engine the driver can use. It is important to note that developers of file-based drivers must write their own database engines.</para>
      </listItem>
      <listItem>
        <para>
          <legacyBold>DBMS-Based Drivers</legacyBold> The driver accesses the physical data through a separate database engine. In this case the driver processes only ODBC calls; it passes SQL statements to the database engine for processing. For example, Oracle drivers are DBMS-based drivers because Oracle has a stand-alone database engine the driver uses. Where the database engine resides is immaterial. It can reside on the same machine as the driver or a different machine on the network; it might even be accessed through a gateway.</para>
      </listItem>
    </list>
    <para>Driver architecture is generally interesting only to driver writers; that is, driver architecture generally makes no difference to the application. However, the architecture can affect whether an application can use DBMS-specific SQL. For example, Microsoft Access provides a stand-alone database engine. If a Microsoft Access driver is DBMS-based — it accesses the data through this engine — the application can pass Microsoft Access–SQL statements to the engine for processing.</para>
    <para>However, if the driver is file-based — that is, it contains a proprietary engine that accesses the Microsoft® Access .mdb file directly — any attempts to pass Microsoft Access–specific SQL statements to the engine are likely to result in syntax errors. The reason is that the proprietary engine is likely to implement only ODBC SQL.</para>
    <para>This section contains the following topics.  </para>
    <list class="bullet">
      <listItem>
        <para>
          <legacyLink xlink:href="d92e0c5c-d176-4282-bbe1-d449e2223d50">File-Based Drivers</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>
          <legacyLink xlink:href="e2208ee0-4cd6-4f0d-bb71-a0b54f7d9330">DBMS-Based Drivers</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>
          <legacyLink xlink:href="e14ae90f-87b3-4bcf-b69a-1773e2c2a1c5">Network Example</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>
          <legacyLink xlink:href="1cad06ee-5940-4361-8d01-7d850db1dd66">Other Driver Architectures</legacyLink>           </para>
      </listItem>
    </list>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>