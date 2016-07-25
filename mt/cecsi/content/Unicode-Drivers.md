---
title: "Unicode Drivers"
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3b4742d5-74fb-4aff-aa21-d83a0064d73d
caps.latest.revision: 5
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Unicode Drivers
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Whether a driver should be a Unicode driver or an ANSI driver depends entirely on the nature of the data source. If the data source supports Unicode data, the driver should be a Unicode driver. If the data source only supports ANSI data, the driver should remain an ANSI driver.</para>
    <para>A Unicode driver must export <legacyBold>SQLConnectW</legacyBold> to be recognized as a Unicode driver by the Driver Manager.</para>
    <para>A Unicode driver must accept Unicode functions (with a suffix of <legacyItalic>W</legacyItalic>) and store Unicode data. It can also accept ANSI functions, but is not required to. (The Driver Manager does not pass an ANSI function call with the <legacyItalic>A</legacyItalic> suffix to the driver, but converts it to an ANSI function call without the suffix and then passes it to the driver.)</para>
    <para>A Unicode driver must be able to return result sets in either Unicode or ANSI, depending on the application's binding. If an application binds to SQL_C_CHAR, the Unicode driver must convert SQL_WCHAR data to SQL_CHAR. The driver manager will map SQL_C_WCHAR to SQL_C_CHAR for ANSI drivers but does no mapping for Unicode drivers.</para>
    <alert class="note">
      <para>When determining the driver type, the Driver Manager will call <legacyBold>SQLSetConnectAttr</legacyBold> and set the SQL_ATTR_ANSI_APP attribute at connection time. If the application is using ANSI APIs, SQL_ATTR_ANSI_APP will be set to SQL_AA_TRUE, and if it is using Unicode, it will be set to a value of SQL_AA_FALSE. This attribute is used so that the driver can exhibit different behavior based on the application type. The attribute cannot be set by the application directly, and it is not supported by <legacyBold>SQLGetConnectAttr</legacyBold>. If a driver exhibits the same behavior for both ANSI and Unicode applications, it should return SQL_ERROR for this attribute. If the driver returns SQL_SUCCESS, the Driver Manager will separate ANSI and Unicode connections when Connection Pooling is used.</para>
    </alert>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>