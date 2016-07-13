---
title: Table Names
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f7a5cb0a-3be7-4f46-82f9-64ffdbceaa9b
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Table Names
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>When the dBASE, Microsoft Excel, Paradox, or Text driver is used, table names that occur in the FROM clause of SELECT or DELETE, after the INTO clause in INSERT, and after UPDATE, CREATE TABLE, and DROP TABLE can contain a valid path, primary name, and file name extension.</para>
    <para>Use of a table name elsewhere in an SQL statement does not support the use of paths or extensions but will accept only the primary name (for example, EMP FROM C:\ABC\EMP). </para>
    <para>Correlation names (aliases) can be used. For example:</para>
    <code>SELECT *  
FROM C:\ABC\EMP T1  
WHERE T1.COL1 = 'aaa'</code>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>