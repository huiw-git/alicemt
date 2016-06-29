---
title: DDL Statements
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 96ac9859-5976-4b06-ae1f-2fec3231e266
translation.priority.ht: 
  - en-gb
---
# DDL Statements
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Data Definition Language (DDL) statements vary tremendously among DBMSs. ODBC SQL defines statements for the most common data definition operations: creating and dropping tables, indexes, and views; altering tables; and granting and revoking privileges. All other DDL statements are data source–specific. Therefore, interoperable applications cannot perform some data definition operations. In general, this is not a problem, because such operations tend to be highly DBMS-specific and are best left to the proprietary database administration software shipped with most DBMSs or the setup program shipped with the driver.</para>
    <para>Another problem in data definition is that data type names vary tremendously among DBMSs. Rather than defining standard data type names and forcing drivers to convert them to DBMS-specific names, <legacyBold>SQLGetTypeInfo</legacyBold> provides a way for applications to discover DBMS-specific data type names. Interoperable applications should use these names in SQL statements to create and alter tables; the names listed in <legacyLink xlink:href="0ee36f09-59e7-4b94-88ca-7ebc0952a3be">Appendix C: SQL Grammar</legacyLink>, and <legacyLink xlink:href="981d49c3-3531-4543-aa75-5bd9e4f67000">Appendix D: Data Types</legacyLink>, are examples only.</para>
  </introduction>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>