---
title: Catalog Position
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 5bc5f64b-c75a-43d2-8745-102ec7a49000
translation.priority.ht: 
  - en-gb
---
# Catalog Position
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The position of a catalog name in an identifier and how it is separated from the rest of the identifier varies from data source to data source. For example, in an Xbase data source, the catalog name is a directory and, in Microsoft® Windows®, is separated from the table name (which is a file name) by a backslash (\). The following illustration demonstrates this condition.</para>
    <mediaLink>
      <image xlink:href="0c08d80d-35d7-4e81-86bb-2ebe9399eb9a" />
    </mediaLink>
    <para>In a SQL Server data source, the catalog is a database and is separated from the schema and table names by a period (.).</para>
    <mediaLink>
      <image xlink:href="986c9b0e-70de-4b4f-a158-ee29f3119c4c" />
    </mediaLink>
    <para>In an Oracle data source, the catalog is also the database but follows the table name and is separated from the schema and table names by an at sign (@).</para>
    <mediaLink>
      <image xlink:href="ff88d8f5-2523-4919-818b-2ced7b53f644" />
    </mediaLink>
    <para>To determine the catalog separator and the location of the catalog name, an application calls <legacyBold>SQLGetInfo</legacyBold> with the SQL_CATALOG_NAME_SEPARATOR and SQL_CATALOG_LOCATION options. Interoperable applications should construct identifiers according to these values.</para>
    <para>When quoting identifiers that contain more than one part, applications must be careful to quote each part separately and not quote the character that separates the identifiers. For example, the following statement to select all of the rows and columns of an Xbase table quotes the catalog (\XBASE\SALES\CORP) and table (Parts.dbf) names, but not the catalog separator (\):</para>
    <code>SELECT * FROM "\XBASE\SALES\CORP"\"PARTS.DBF"</code>
    <para>The following statement to select all of the rows and columns of an Oracle table quotes the catalog (Sales), schema (Corporate), and table (Parts) names, but not the catalog (@) or schema (.) separators:</para>
    <code>SELECT * FROM "Corporate"."Parts"@"Sales"</code>
    <para>For information about quoting identifiers, see the next section, <legacyLink xlink:href="729ba55f-743b-4a04-8c39-ac0a9914211d">Quoted Identifiers</legacyLink>.</para>
  </introduction>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>