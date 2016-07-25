---
title: "Sequence of Status Records"
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0e0436cc-230f-44b0-b373-04a57e83ee76
caps.latest.revision: 5
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Sequence of Status Records
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>If two or more status records are returned, the Driver Manager and driver rank them according to the following rules. The record with the highest rank is the first record. The source of a record (Driver Manager, driver, gateway, and so on) is not considered when ranking records.  </para>
    <list class="bullet">
      <listItem>
        <para>
          <legacyBold>Errors</legacyBold> Status records that describe errors have the highest rank. Among error records, records that indicate a transaction failure or possible transaction failure outrank all other records. If two or more records describe the same error condition, SQLSTATEs defined by the Open Group CLI specification (classes 03 through HZ) outrank ODBC-defined and driver-defined SQLSTATEs.</para>
      </listItem>
      <listItem>
        <para>
          <legacyBold>Implementation-defined No Data Values</legacyBold> Status records that describe driver-defined No Data values (class 02) have the second highest rank.</para>
      </listItem>
      <listItem>
        <para>
          <legacyBold>Warnings</legacyBold> Status records that describe warnings (class 01) have the lowest rank. If two or more records describe the same warning condition, warning SQLSTATEs defined by the Open Group CLI specification outrank ODBC-defined and driver-defined SQLSTATEs.</para>
      </listItem>
    </list>
    <para>If there are two or more records with the highest rank, it is undefined which record is the first record. The order of all other records is undefined. In particular, because warnings may appear before errors, applications should check all status records when a function returns a value other than SQL_SUCCESS.</para>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>