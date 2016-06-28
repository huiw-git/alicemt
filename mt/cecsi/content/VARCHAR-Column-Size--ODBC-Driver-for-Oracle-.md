---
title: VARCHAR Column Size (ODBC Driver for Oracle)
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: eb4cb410-3d00-4251-8c5e-a06f36c4dac7
translation.priority.ht: 
  - en-gb
---
# VARCHAR Column Size (ODBC Driver for Oracle)
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <alert class="important">
      <para>This feature will be removed in a future version of Windows. Avoid using this feature in new development work, and plan to modify applications that currently use this feature. Instead, use the ODBC driver provided by Oracle.</para>
    </alert>
    <para>In Oracle8, the maximum size of a VARCHAR column has increased from 2000 to 4000 bytes. The Oracle 7.3.x client software has no way to bind a parameter value larger than 2000 bytes. Therefore, if you create a table with a VARCHAR column of larger than 2000 bytes, you will be unable to perform parameterized inserts, updates, deletes, and queries against it with data that exceeds the 2000-byte limit of the client software. Because both the ODBC Driver for Oracle and the OLE DB Provider for Oracle use parameterized inserts, updates, deletes, and queries, they will report ORA-01026 errors in this case. Data that is within the limits enforced by the Oracle client software will work. To avoid this 2000-byte limit, you must upgrade your client software to Oracle8 (8.0.4.1.1c or higher).</para>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>