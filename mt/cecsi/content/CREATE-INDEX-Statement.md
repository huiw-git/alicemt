---
title: CREATE INDEX Statement
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 69438247-eef3-44c5-bef2-acef4e146f41
translation.priority.ht: 
  - en-gb
---
# CREATE INDEX Statement
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The syntax of the CREATE INDEX statement is: </para>
  </introduction>
  <section>
    <content>
      <para>CREATE [UNIQUE] INDEX <legacyItalic>index-name</legacyItalic> ON <legacyItalic>table-name</legacyItalic> (<legacyItalic>column-identifier</legacyItalic> [ASC][DESC][, <legacyItalic>column-identifier</legacyItalic> [ASC][DESC]...]) WITH &lt;<legacyItalic>index option list</legacyItalic>&gt;</para>
      <para>where &lt;<legacyItalic>index option list</legacyItalic>&gt; can be: PRIMARY | DISALLOW NULL | IGNORE NULL</para>
      <para>Only the Microsoft Access driver uses the DISALLOW NULL and IGNORE NULL index options. The dBASE and Paradox drivers accept the syntax, but ignore the presence of either option.</para>
      <para>When the Paradox driver is used, the CREATE INDEX statement creates Paradox primary key files and secondary files.</para>
      <para>This statement is not supported by the Microsoft Excel or Text drivers.</para>
    </content>
  </section>
  <relatedTopics />
</developerConceptualDocument>