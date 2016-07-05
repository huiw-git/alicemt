---
title: Data Type Support
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 782b4490-372b-4366-aad7-a486fb8a07c8
translation.priority.ht: 
  - en-gb
---
# Data Type Support
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>ODBC drivers must support at least one of SQL_CHAR and SQL_VARCHAR. Support for other data types is determined by the driver's or data source's SQL-92 conformance level. An application should call <legacyBold>SQLGetTypeInfo</legacyBold> to determine the data types supported by the driver.</para>
  </introduction>
  <section>
    <content>
      <para>For more information on data types, see <legacyLink xlink:href="981d49c3-3531-4543-aa75-5bd9e4f67000">Appendix D: Data Types</legacyLink>.</para>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>