---
title: "dBASE Indexes"
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: fdfa56f5-e324-4ec2-9267-fdf95ab99373
caps.latest.revision: 5
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# dBASE Indexes
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The ODBC dBASE driver automatically opens and updates dBASE IV index files. You must use the <legacyBold>Select Indexes</legacyBold> dialog box displayed through the ODBC Data Source Administrator to associate dBASE III .ndx files with dBASE files.</para>
    <para>The following limitations apply to the creation of dBASE indexes:  </para>
    <list class="bullet">
      <listItem>
        <para>All column names must be valid.</para>
      </listItem>
      <listItem>
        <para>All columns must be in the same ascending or descending order.</para>
      </listItem>
      <listItem>
        <para>The length of any single text column must be less than 100 bytes.</para>
      </listItem>
      <listItem>
        <para>If more than one column exists, all of the columns must be text columns and the sum of the column sizes must be less than 100 bytes.</para>
      </listItem>
      <listItem>
        <para>Memo fields cannot be indexed.</para>
      </listItem>
      <listItem>
        <para>An index must not be specified for the current set of fields (that is, duplicate indexes are not allowed).</para>
      </listItem>
      <listItem>
        <para>The index name must match the dBASE index naming convention. dBASE III requires that each index be in a separate file, each having an .ndx extension. In dBASE IV, indexes are created as tag names that are stored in a single .mdx file. The .mdx file has the same base name as the database file (for example, Emp.mdx is the index file for the Emp.dbf database).</para>
      </listItem>
      <listItem>
        <para>dBASE defines a unique index as one where only one record from a set with identical key values is added to the index.</para>
      </listItem>
    </list>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>