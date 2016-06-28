---
title: Column Size, Decimal Digits, Transfer Octet Length, and Display Size
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 723107a1-be08-4ea3-a8c0-b2c45d38d1aa
translation.priority.ht: 
  - en-gb
---
# Column Size, Decimal Digits, Transfer Octet Length, and Display Size
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Data types are characterized by their column (or parameter) size, decimal digits, length, and display size. The following ODBC functions return these attributes for a parameter in an SQL statement or for an SQL data type on a data source. Each ODBC function returns a different set of these attributes, as follows:  </para>
    <list class="bullet">
      <listItem>
        <para>             <legacyBold>SQLDescribeCol</legacyBold> returns the column size and decimal digits of the columns it describes.</para>
      </listItem>
      <listItem>
        <para>             <legacyBold>SQLDescribeParam</legacyBold> returns the parameter size and decimal digits of the parameters it describes. <legacyBold>SQLBindParameter</legacyBold> sets the parameter size and decimal digits for a parameter in an SQL statement.</para>
      </listItem>
      <listItem>
        <para>The catalog functions <legacyBold>SQLColumns</legacyBold>, <legacyBold>SQLProcedureColumns</legacyBold>, and <legacyBold>SQLGetTypeInfo</legacyBold> return attributes for a column in a table, result set, or a procedure parameter and the catalog attributes of the data types in the data source. <legacyBold>SQLColumns</legacyBold> returns the column size, decimal digits, and length of a column in specified tables (such as the base table, view, or a system table). <legacyBold>SQLProcedureColumns</legacyBold> returns the column size, decimal digits, and length of a column in a procedure. <legacyBold>SQLGetTypeInfo</legacyBold> returns the maximum column size and the minimum and maximum decimal digits of an SQL data type on a data source.</para>
      </listItem>
    </list>
    <para>The values returned by these functions for the column or parameter size correspond to "precision" as defined in ODBC 2.<legacyItalic>x</legacyItalic>. However, the values do not necessarily correspond to the values returned in SQL_DESC_PRECISION or any other one descriptor field. The same is true for decimal digits, which correspond to "scale" as defined in ODBC 2.<legacyItalic>x</legacyItalic>. It does not necessarily correspond to the values returned in SQL_DESC_SCALE or any other one descriptor field, but comes from different descriptor fields depending on the data type. For further information, see <legacyLink xlink:href="541b83ab-b16d-4714-bcb2-3c3daa9a963b">Column Size</legacyLink> and <legacyLink xlink:href="07f3d1fc-b4ee-4693-b342-330b2231b6d0">Decimal Digits</legacyLink>.</para>
    <para>Similarly, the values for transfer octet length do not come from SQL_DESC_LENGTH. They come from the SQL_DESC_OCTET_LENGTH of a field of a descriptor for all character and binary types. There is no descriptor field that holds this information for other types.</para>
    <para>The display size value for all data types corresponds to the value in a single descriptor field, SQL_DESC_DISPLAY_SIZE.</para>
    <para>Descriptor fields describe the characteristics of a result set. Descriptor fields do not contain valid values about data before statement execution. The values for column size, decimal digits, and display size returned by <legacyBold>SQLColumns</legacyBold>, <legacyBold>SQLProcedureColumns</legacyBold>, and <legacyBold>SQLGetTypeInfo</legacyBold>,on the other hand, return characteristics of database objects, such as table columns and data types, that exist in the data source's catalog. Likewise, in its result set, <legacyBold>SQLColAttribute</legacyBold> returns the column size, decimal digits, and transfer octet length of columns at the data source; these values are not necessarily the same as the values in the SQL_DESC_PRECISION, SQL_DESC_SCALE, and SQL_DESC_OCTET_LENGTH descriptor fields.</para>
    <para>For more information about these descriptor fields, see <legacyLink xlink:href="8c544388-fe9d-4f94-a0ac-fa0b9c9c88a5">SQLSetDescField</legacyLink>.</para>
    <para>This section contains the following topics.  </para>
    <list class="bullet">
      <listItem>
        <para>             <legacyLink xlink:href="541b83ab-b16d-4714-bcb2-3c3daa9a963b">Column Size</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="07f3d1fc-b4ee-4693-b342-330b2231b6d0">Decimal Digits</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="9fdc9762-e203-4cff-9212-54f450bf18d9">Transfer Octet Length</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="9f7f766f-2492-463c-aab7-f2476e222042">Display Size</legacyLink>           </para>
      </listItem>
    </list>
  </introduction>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>