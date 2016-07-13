---
title: Revoking and Granting Rights When Using Stored Procedures
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 24070039-03ab-4623-a681-6308802eb399
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Revoking and Granting Rights When Using Stored Procedures
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <alert class="important">
      <para>This feature will be removed in a future version of Windows. Avoid using this feature in new development work, and plan to modify applications that currently use this feature. Instead, use the ODBC driver provided by Oracle.</para>
    </alert>
    <para>The Microsoft ODBC Driver for Oracle returns the following error message when user rights are granted and then revoked on a table accessed by a stored procedure:</para>
    <para>SQL_ERROR=-1</para>
    <para>szErrorMsg="[Microsoft][ODBC driver for Oracle]Wrong number of parameters"</para>
    <para>szErrorMsg="[Microsoft][ODBC driver for Oracle]Syntax error or access violation"</para>
    <para>The call to the Oracle OCI function Odessp() fails in this scenario but is necessary in order to implement default parameters. After the underlying table permissions are modified, the stored procedure must be recompiled before running it again.</para>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>