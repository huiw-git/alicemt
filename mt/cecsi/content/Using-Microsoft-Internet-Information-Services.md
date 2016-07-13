---
title: Using Microsoft Internet Information Services
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3328f2f1-b34a-472f-82cf-ad49768ff061
manager:jhubbard
translation.priority.ht: 
  - en-gb
---
# Using Microsoft Internet Information Services
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <alert class="important">
      <para>This feature will be removed in a future version of Windows. Avoid using this feature in new development work, and plan to modify applications that currently use this feature. Instead, use the ODBC driver provided by Oracle.</para>
    </alert>
    <para>If you have difficulty connecting from within an IIS script (particularly if you receive an ORA-12641 error), add the following line to the Sqlnet.ora file:</para>
    <code>SQLNET.AUTHENTICATION_SERVICES = (none)</code>
    <para>This will disable the Secure Network Services so you can connect using anonymous authentication.</para>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>