---
title: "CREATE INDEX Statement Limitations"
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 832dcda1-e452-48e6-8adb-7fb33c4fb4ff
caps.latest.revision: 4
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# CREATE INDEX Statement Limitations
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The CREATE INDEX statement is not supported for the Microsoft Excel or Text drivers.</para>
    <para>An index can be defined on a maximum of 10 columns. If more than 10 columns are included in a CREATE INDEX statement, the index will not be recognized and the table will be treated as though no index were created. </para>
    <para>The dBASE driver cannot create an index on a LOGICAL column.</para>
    <para>When the dBASE driver is used, response time on large files can be improved by building an .mdx (or .ndx) index on the column (field) specified in the WHERE clauses of a SELECT statement. Existing .mdx indexes will automatically be applied for =, &gt;, &lt;, &gt;=, =&lt;, and BETWEEN operators in a WHERE clause, and LIKE predicates, as well as in join predicates.</para>
    <para>When the dBASE driver is used, the index created by a CREATE UNIQUE INDEX statement is actually non-unique, and duplicate values can be inserted into the indexed column. Only one record from a set with identical key values can be added to the index.</para>
    <para>When the Paradox driver is used, a unique index must be defined upon a contiguous subset of the columns in a table, including the first column. A table cannot be updated by the Paradox driver if a unique index is not defined on the table or when the Paradox driver is used without the implementation of the Borland Database Engine.</para>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>