---
title: SQL_C_TCHAR
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9e27c8bd-ee15-4ce9-b70a-34cf1bf16f4c
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# SQL_C_TCHAR
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The SQL_C_TCHAR type identifier does not actually identify a data type; it is a macro that exists within the header file for Unicode conversion. It is replaced by SQL_C_CHAR or SQL_C_WCHAR depending on the setting of the UNICODE <legacyBold>#define</legacyBold>. It is useful for an application transferring character data that is compiled as both an ANSI and a Unicode application.</para>
  </introduction>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>