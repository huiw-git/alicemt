---
title: SQLGetTypeInfo (Text File Driver)
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 05a58975-093c-4bd9-bd72-b5f0026a6e36
translation.priority.ht: 
  - en-gb
---
# SQLGetTypeInfo (Text File Driver)
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <alert class="note">
      <para>This topic provides Text File Driver-specific information. For general information about this function, see the appropriate topic under <legacyLink xlink:href="b7a49774-f458-44ce-9a04-a0457501405b">ODBC API Reference</legacyLink>.</para>
    </alert>
    <para>The name of the type (TYPE_NAME) returned in the table produced by <legacyBold>SQLGetTypeInfo</legacyBold> will be the name most commonly used by the data source.</para>
    <para>SQL_ALL_EXCEPT_LIKE will be returned in the SEARCHABLE column for the Byte, Counter, Double, Single, Long, and Short data types. (The LIKE capability can be achieved by converting the value to a character using the ODBC canonical conversion functions, then performing the comparison.)</para>
    <para>When the Text driver is used, <legacyBold>SQLGetTypeInfo</legacyBold> returns a CASE_SENSITIVE value of FALSE for the text data types (CHAR and LONGCHAR), when the data types actually are case-sensitive.</para>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>