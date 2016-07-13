---
title: Checking Feature Support and Variability
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ff45f220-9b8b-4c44-82f8-a8e9913fffea
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Checking Feature Support and Variability
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>To check feature support and variability, applications generally call <legacyBold>SQLGetInfo</legacyBold>, <legacyBold>SQLGetFunctions</legacyBold>, and <legacyBold>SQLGetTypeInfo</legacyBold>. A good starting place is the driver's API and SQL grammar conformance levels. These describe broad levels of feature support. The application can then call <legacyBold>SQLGetInfo</legacyBold> with other options to determine the support or variability of features it needs, <legacyBold>SQLGetFunctions</legacyBold> to determine whether functions it needs beyond the returned conformance level are supported, and <legacyBold>SQLGetTypeInfo</legacyBold> to determine what SQL data types are supported.</para>
    <para>An application can determine whether a statement or connection attribute is supported by calling <legacyBold>SQLSetStmtAttr</legacyBold> or <legacyBold>SQLSetConnectAttr</legacyBold> with that attribute. If the function returns SQL_SUCCESS or SQL_SUCCESS_WITH_INFO, the attribute is supported; if it returns SQL_ERROR and SQLSTATE HYC00 (Optional feature not implemented), the attribute is not supported.</para>
    <para>Applications can also determine a limited amount of information before connecting to the driver by calling <legacyBold>SQLDrivers</legacyBold>.</para>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>