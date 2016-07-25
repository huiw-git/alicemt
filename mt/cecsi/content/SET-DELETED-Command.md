---
title: "SET DELETED Command"
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6b5e0086-156d-471d-8e7f-6c5fa9686cd5
caps.latest.revision: 4
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# SET DELETED Command
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Specifies whether records marked for deletion are processed and whether they are available for use in other commands.</para>
  </introduction>
  <syntaxSection>
    <legacySyntax>
SET DELETED ON | OFF</legacySyntax>
  </syntaxSection>
  <section>
    <title>Arguments</title>
    <content>
      <definitionTable>
        <definedTerm>ON </definedTerm>
        <definition>
          <para>(Default for the driver; the default for Visual FoxPro is OFF.) Specifies that commands that operate on records (including records in related tables) using a scope ignore records marked for deletion.</para>
        </definition>
        <definedTerm>OFF </definedTerm>
        <definition>
          <para>Specifies that records marked for deletion can be accessed by commands that operate on records (including records in related tables) using a scope.</para>
        </definition>
      </definitionTable>
    </content>
  </section>
  <languageReferenceRemarks>
    <content>
      <para>Queries that use DELETED( ) to test the status of records can be optimized using Visual FoxPro Rushmore technology if the table is indexed on DELETED( ).</para>
      <alert class="important">
        <para>SET DELETED is ignored if the default scope for the command is the current record or if you include a scope of a single record. INDEX always ignores SET DELETED and indexes all records in the table.</para>
      </alert>
    </content>
  </languageReferenceRemarks>
  <relatedTopics>
<link xlink:href="0d5bd477-626f-4f22-a05a-f531d9f8c5e7">DELETE - SQL</link>
</relatedTopics>
</developerReferenceWithSyntaxDocument>