---
title: "Schema Views"
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f1dfb3e8-a7bd-46c3-92b6-c19531e8409d
caps.latest.revision: 4
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Schema Views
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>An application can retrieve metadata information from the DBMS either by calling ODBC catalog functions or by using INFORMATION_SCHEMA views. The views are defined by the ANSI SQL-92 standard.</para>
    <para>If supported by the DBMS and the driver, the INFORMATION_SCHEMA views provide a more powerful and comprehensive means of retrieving metadata than the ODBC catalog functions provide. An application can execute its own custom <legacyBold>SELECT</legacyBold> statement against one of these views, can join views, or can perform a union on views. While offering greater utility and a wider range of metadata, INFORMATION_SCHEMA views are not often supported by the DBMS. This might change as more DBMSs and drivers achieve compliance with SQL-92.</para>
    <para>To determine which views are supported, an application calls <legacyBold>SQLGetInfo</legacyBold> with the SQL_INFO_SCHEMA_VIEWS option. To retrieve metadata from a supported view, the application executes a <legacyBold>SELECT</legacyBold> statement that specifies the schema information required.</para>
  </introduction>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>