---
title: File-Based Drivers
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d92e0c5c-d176-4282-bbe1-d449e2223d50
translation.priority.ht: 
  - en-gb
---
# File-Based Drivers
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>File-based drivers are used with data sources such as dBASE that do not provide a stand-alone database engine for the driver to use. These drivers access the physical data directly and must implement a database engine to process SQL statements. As a standard practice, the database engines in file-based drivers implement the subset of ODBC SQL defined by the minimum SQL conformance level; for a list of the SQL statements in this conformance level, see <legacyLink xlink:href="0ee36f09-59e7-4b94-88ca-7ebc0952a3be">Appendix C: SQL Grammar</legacyLink>.</para>
    <para>In comparing file-based and DBMS-based drivers, file-based drivers are harder to write because of the database engine component, less complicated to configure because there are no network pieces, and less powerful because few people have the time to write database engines as powerful as those produced by database companies.</para>
    <para>The following illustration shows two different configurations of file-based drivers, one in which the data resides locally and the other in which it resides on a network file server.</para>
    <mediaLink>
      <image xlink:href="5861ad86-e0e7-4014-b2c7-c77438720e2b" />
    </mediaLink>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>