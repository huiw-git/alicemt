---
title: SQLPrepare (Visual FoxPro ODBC Driver)
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0c4cb5a4-9729-4b2e-a0c6-52027b92e8fc
translation.priority.ht: 
  - en-gb
---
# SQLPrepare (Visual FoxPro ODBC Driver)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <alert class="note">
      <para>This topic contains Visual FoxPro ODBC Driver-specific information. For general information about this function, see the appropriate topic under <legacyLink xlink:href="b7a49774-f458-44ce-9a04-a0457501405b">ODBC API Reference</legacyLink>.</para>
    </alert>
    <para>Support: Full </para>
    <para>ODBC API Conformance: Core Level</para>
    <para>Prepares an SQL statement by planning how to optimize and execute the statement. The SQL statement is compiled for execution by <legacyLink xlink:href="5004060f-8510-4018-87a4-d41789e69d3e">SQLExecDirect</legacyLink>.</para>
    <para>If your table, view, or field names contain spaces, enclose the names in back quote (`) marks. For example, if your database contains a table named My Table and the field My Field, enclose each element of the identifier as follows:</para>
    <code>SELECT * FROM `My Table`.`My Field`</code>
    <para>For more information, see <legacyLink xlink:href="332e1b4b-b0ed-4e7a-aa4d-4f35f4f4476b">SQLPrepare</legacyLink> in the <legacyItalic>ODBC Programmer's Reference</legacyItalic>.</para>
  </introduction>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>