---
title: Table Name Limitations
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d9843e4b-1d05-4d5a-9dc3-ee9ec59edb97
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Table Name Limitations
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Table names can contain any valid characters (for example, spaces). If table names contain any characters except letters, numbers, and underscores, the name must be delimited by enclosing it in back quotes (`).</para>
    <para>When the Microsoft Excel driver is used, and a table name is not qualified by a database reference, the default database is implied. If a name in Microsoft Excel includes the "!" character, it will automatically be translated to the "$" character instead. </para>
    <para>The Microsoft Excel table name that references &lt;filename&gt; is supported for Microsoft Excel 3.0 and 4.0 files. The Microsoft Excel table name that references &lt;workbook-name&gt; is supported for Microsoft Excel 5.0, 7.0, or 97 files. </para>
    <para>When the dBASE driver is used, characters with an ASCII value greater than 127 are converted to underscores.</para>
    <para>When the Microsoft Access driver is used, the table name is limited to 64 characters.</para>
    <para>When the dBASE, Microsoft Excel 3.0 or 4.0, Paradox, or Text driver is used, special MS-DOS keywords CON, AUX, LPT1, and LPT2 should not be used as table names.</para>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>