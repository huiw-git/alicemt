---
title: "SQLExecDirect (Visual FoxPro ODBC Driver)"
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 5004060f-8510-4018-87a4-d41789e69d3e
caps.latest.revision: 4
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# SQLExecDirect (Visual FoxPro ODBC Driver)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <alert class="note">
      <para>This topic contains Visual FoxPro ODBC Driver-specific information. For general information about this function, see the appropriate topic under <legacyLink xlink:href="b7a49774-f458-44ce-9a04-a0457501405b">ODBC API Reference</legacyLink>.</para>
    </alert>
    <para>Support: Full </para>
    <para>ODBC API Conformance: Core Level</para>
    <para>Executes a new, <legacyLink xlink:href="a379b3cb-0393-46e7-b03b-724a56d8f31c">preparable SQL statement</legacyLink>. The Visual FoxPro ODBC Driver uses the current values of the parameter marker variables if any parameters exist in the statement.</para>
    <para>To create a batch command to submit more than one SQL statement at a time, use a semicolon (;) to separate each SQL statement in the batch.</para>
    <para>If your table, view, or field names contain spaces, enclose the names in back quote marks. For example, if your database contains a table named My Table and the field My Field, enclose each element of the identifier as follows:</para>
    <code>SELECT `My Table`.`Field1`, `My Table`.`Field2` FROM `My Table`</code>
    <para>For more information, see <legacyLink xlink:href="985fcee1-f204-425c-bdd1-deb0e7d7bbd9">SQLExecDirect</legacyLink> in the <legacyItalic>ODBC Programmer's Reference</legacyItalic>.</para>
  </introduction>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>