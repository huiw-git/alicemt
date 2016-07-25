---
title: "Setting the Date Format on Connection"
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ba0d5123-db52-448b-8e19-b7647ce4b361
caps.latest.revision: 7
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Setting the Date Format on Connection
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <alert class="important">
      <para>This feature will be removed in a future version of Windows. Avoid using this feature in new development work, and plan to modify applications that currently use this feature. Instead, use the ODBC driver provided by Oracle.</para>
    </alert>
    <para>The new version of the Microsoft ODBC Driver for Oracle does not automatically set the date format for Oracle date fields. Previously when the driver connected, it used <codeInline>ALTER SESSION SET NLS_DATE_FORMAT ='YYYY-MM-DD HH:MI:SS'</codeInline>.</para>
    <para>To set the date format, call ALTER SESSION SET and then perform the insert. For example:</para>
    <code>conn.Execute "ALTER SESSION SET NLS_DATE_FORMAT = 'YYYY-MM-DD HH:MI:SS' "
sSql = "INSERT INTO DATETEST VALUES (24,'1988-12-01 10:23:03')"
conn.Execute sSql</code>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>