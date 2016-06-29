---
title: SET NULL Command
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 410c5a6e-e957-4ecc-9e2d-e591cbc0bc4f
translation.priority.ht: 
  - en-gb
---
# SET NULL Command
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Determines how null values are supported by the ALTER TABLE - SQL, CREATE TABLE - SQL, and INSERT - SQL commands.</para>
  </introduction>
  <syntaxSection>
    <legacySyntax>
SET NULL ON | OFF</legacySyntax>
  </syntaxSection>
  <section>
    <title>Arguments</title>
    <content>
      <definitionTable>
        <definedTerm>ON </definedTerm>
        <definition>
          <para>(Default for the driver; the default for Visual FoxPro is OFF.) Specifies that all columns in a table created with ALTER TABLE and CREATE TABLE will allow null values. You can override null value support for columns in the table by including the NOT NULL clause in the columns' definitions.</para>
          <para>Also specifies that INSERT - SQL will insert null values into any columns not included in the INSERT - SQL VALUE clause. INSERT - SQL will insert null values only into columns that allow null values.
</para>
        </definition>
        <definedTerm>OFF </definedTerm>
        <definition>
          <para>Specifies that all columns in a table created with ALTER TABLE and CREATE TABLE will not allow null values. You can designate null value support for columns in ALTER TABLE and CREATE TABLE by including the NULL clause in the columns' definitions.</para>
          <para>Also specifies that INSERT - SQL will insert blank values into any columns not included in the INSERT - SQL VALUE clause.
</para>
        </definition>
      </definitionTable>
    </content>
  </section>
  <languageReferenceRemarks>
    <content>
      <para>SET NULL affects only how null values are supported by ALTER TABLE, CREATE TABLE, and INSERT - SQL. Other commands are unaffected by SET NULL.</para>
    </content>
  </languageReferenceRemarks>
  <relatedTopics>
<link xlink:href="3a01a291-f4d9-43bc-a725-5a95546ff364">ALTER TABLE</link>
<link xlink:href="be2143ba-fc16-42c9-84f7-8985cd924860">CREATE TABLE - SQL</link>
<link xlink:href="9b648198-349f-46f6-b869-13d129945971">INSERT - SQL</link>
</relatedTopics>
</developerReferenceWithSyntaxDocument>