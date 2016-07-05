---
title: DROP INDEX Statement
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: cd0ff767-9254-413b-bd1a-bed26c6774f5
translation.priority.ht: 
  - en-gb
---
# DROP INDEX Statement
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>When the Microsoft Access, dBASE, or Paradox driver is used, the syntax of the DROP INDEX statement is "DROP INDEX a on b" where "a" is the name of the index and "b" is the name of the table (not DROP INDEX <legacyItalic>index-name</legacyItalic>).</para>
  </introduction>
  <section>
    <content>
      <para>When the Paradox driver is used, the DROP INDEX statement deletes Paradox secondary index files.</para>
      <para>The DROP INDEX statement is not supported for the Microsoft Excel or Text drivers.</para>
    </content>
  </section>
  <relatedTopics />
</developerConceptualDocument>