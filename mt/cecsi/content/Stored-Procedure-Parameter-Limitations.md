---
title: Stored Procedure Parameter Limitations
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 8b804bcf-4cce-4e6f-aa45-00bab9ef9921
translation.priority.ht: 
  - en-gb
---
# Stored Procedure Parameter Limitations
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <alert class="important">
      <para>This feature will be removed in a future version of Windows. Avoid using this feature in new development work, and plan to modify applications that currently use this feature. Instead, use the ODBC driver provided by Oracle.</para>
    </alert>
    <para>When running Oracle stored procedures that utilize 10 or more output parameters, the stored procedure call will fail, resulting in an Access Violation or ActiveX Data Objects (ADO) error. This can occur when using the Microsoft ODBC Driver for Oracle with versions 8.0.4.0.0 and 8.0.4.0.4 of the Oracle client software.</para>
    <para>To correct the problem, the Oracle client software must be upgraded to version 8.0.4.2.0 or higher. Contact Oracle Corporation for more information about the <legacyLink xlink:href="1275157b-f4e1-4c24-b273-c02555e261c2">patches</legacyLink>.</para>
    <alert class="note">
      <para>This problem does not occur with the early release of Oracle client software version 8.0.3.0.0.</para>
    </alert>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>