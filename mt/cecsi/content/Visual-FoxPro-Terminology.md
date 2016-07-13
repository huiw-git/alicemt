---
title: Visual FoxPro Terminology
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a379b3cb-0393-46e7-b03b-724a56d8f31c
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Visual FoxPro Terminology
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <definitionTable>
      <definedTerm> <legacyBold>database</legacyBold> </definedTerm>
      <definition>
        <para>In Visual FoxPro, a database file has a .dbc extension and can contain one or more <legacyBold>tables</legacyBold>.</para>
      </definition>
      <definedTerm> <legacyBold>database table</legacyBold> </definedTerm>
      <definition>
        <para>In Visual FoxPro, a table that is associated with a database. Contrast <legacyBold>free table</legacyBold>.</para>
      </definition>
      <definedTerm> <legacyBold>free table</legacyBold> </definedTerm>
      <definition>
        <para>In Visual FoxPro, a table that is not associated with a database.</para>
        <para>A .dbf file created in FoxPro version 2.x is a free table unless it is converted to a Visual FoxPro table and added to a Visual FoxPro database. Contrast <legacyBold>database table</legacyBold>. </para>
      </definition>
      <definedTerm> <legacyBold>preparable SQL statement</legacyBold> </definedTerm>
      <definition>
        <para>A SQL statement that has not already been processed by the <legacyBold>SQLPrepare</legacyBold> function. For more information about this function with the Visual FoxPro ODBC Driver, see <legacyLink xlink:href="0c4cb5a4-9729-4b2e-a0c6-52027b92e8fc">SQLPrepare (Visual FoxPro ODBC Driver)</legacyLink>.</para>
      </definition>
      <definedTerm> <legacyBold>table</legacyBold> </definedTerm>
      <definition>
        <para>In Visual FoxPro, records are stored in a table. Each row of a table represents a record, and the columns of the table represent the fields of the record. Each Visual FoxPro table is stored in its own file with a .dbf extension. Visual FoxPro tables can be associated with a database.</para>
        <para>FoxPro version 2.<legacyItalic>x</legacyItalic> tables are not associated with a database. </para>
      </definition>
    </definitionTable>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>