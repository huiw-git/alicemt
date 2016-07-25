---
title: "Using Operating System Authentication"
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 613daef7-3171-42d0-b7e3-3879280f864d
caps.latest.revision: 7
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Using Operating System Authentication
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <alert class="important">
      <para>This feature will be removed in a future version of Windows. Avoid using this feature in new development work, and plan to modify applications that currently use this feature. Instead, use the ODBC driver provided by Oracle.</para>
    </alert>
    <para>Oracle operating system authentication relies on the underlying operating system to control access to database accounts. Users need not enter a password when using this type of login.</para>
    <para>To take advantage of this feature, specify "/" as the user ID and do not specify a password when connecting using any of the following connection APIs: <legacyLink xlink:href="d9f49520-72d7-4234-8635-260d0ce4199c">SQLBrowseConnect</legacyLink>, <legacyLink xlink:href="8596eed7-bda6-4cac-ae1f-efde1aab785f">SQLConnect</legacyLink>, or <legacyLink xlink:href="98cced6f-41b8-43c1-a3cd-f4ea1615c0af">SQLDriverConnect</legacyLink>.</para>
    <para>Oracle databases use SQL*Net Authentication Services to authenticate users that are logged on. This service works well if users are logged into Oracle through SQLPlus; however, when the logged-in user is a service such as Internet Information Services, the authentication fails. This is a known limitation of SQL*Net Authentication and produces the following error: "[Microsoft][ODBC driver for Oracle][Oracle]ORA-12641: TNS:authentication service failed to initialize."</para>
    <para>You can correct this problem by editing the Sqlnet.ora file. This configuration file is usually stored in the Network\Admin subdirectory of the Oracle home directory. Add the following line to Sqlnet.ora:</para>
    <code>SQLNET.AUTHENTICATION_SERVICES = (none)</code>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>