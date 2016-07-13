---
title: ODBC Overview
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 233315bd-2b7f-4b20-9978-e920e1ea9a07
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# ODBC Overview
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Open Database Connectivity (ODBC) is a widely accepted application programming interface (API) for database access. It is based on the Call-Level Interface (CLI) specifications from Open Group and ISO/IEC for database APIs and uses Structured Query Language (SQL) as its database access language.</para>
    <para>ODBC is designed for maximum <legacyItalic>interoperability</legacyItalic> - that is, the ability of a single application to access different database management systems (DBMSs) with the same source code. Database applications call functions in the ODBC interface, which are implemented in database-specific modules called <legacyItalic>drivers</legacyItalic>. The use of drivers isolates applications from database-specific calls in the same way that printer drivers isolate word processing programs from printer-specific commands. Because drivers are loaded at run time, a user only has to add a new driver to access a new DBMS; it is not necessary to recompile or relink the application.</para>
    <para>This section contains the following topics.  </para>
    <list class="bullet">
      <listItem>
        <para>             <legacyLink xlink:href="ba6eb993-316b-4650-bab8-d76583c00e53">Why Was ODBC Created?</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="badf3a45-f941-44ae-a31d-393116f68a18">What Is ODBC?</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="79b9c268-16ac-4b80-b451-f9dcd8c02ca4">ODBC and the Standard CLI</legacyLink>           </para>
      </listItem>
    </list>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>