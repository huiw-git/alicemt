---
title: SQL Conformance Levels
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3529df2c-a09b-4c16-9c60-eae7a06d903a
translation.priority.ht: 
  - en-gb
---
# SQL Conformance Levels
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The level of SQL-92 grammar supported by a driver is indicated by the value returned by a call to <legacyBold>SQLGetInfo</legacyBold> with the SQL_SQL_CONFORMANCE information type. This indicates whether the driver conforms to the Entry, FIPS Transitional, Intermediate, or Full levels defined in SQL-92.</para>
    <para>All ODBC drivers must support the minimum SQL grammar described in <legacyLink xlink:href="4f36d785-104f-4fec-93be-f201203bc7c7">SQL Minimum Grammar</legacyLink> in Appendix C: SQL Grammar. This grammar is a subset of the Entry level of SQL-92. Drivers may support additional SQL and be conformant to the SQL-92 Entry, Intermediate, or Full level, or to the FIPS 127-2 Transitional level. Drivers that comply to a given level of SQL-92 or FIPS 127-2 can support additional features in any of the higher levels yet not be fully conformant to that level. To determine whether a feature is supported, an application should call <legacyBold>SQLGetInfo</legacyBold> with the appropriate information type. The conformance level of an SQL feature is described in the corresponding information type. (See the <legacyLink xlink:href="49dceccc-d816-4ada-808c-4c6138dccb64">SQLGetInfo</legacyLink> function description.)</para>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>