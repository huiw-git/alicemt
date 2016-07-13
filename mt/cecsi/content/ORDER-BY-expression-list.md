---
title: ORDER BY expression-list
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 5ef88186-a99f-4e2c-a3f3-98a42d4f03a5
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# ORDER BY expression-list
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Expressions can be used in the ORDER BY clause. For example, in the following clauses the table is ordered by three key expressions: a+b, c+d, and e.</para>
  </introduction>
  <section>
    <content>
      <code>SELECT * FROM emp
ORDER BY a+b,c+d,e</code>
      <para>No ordering is allowed on set functions or an expression that contains a set function.</para>
    </content>
  </section>
  <relatedTopics />
</developerConceptualDocument>