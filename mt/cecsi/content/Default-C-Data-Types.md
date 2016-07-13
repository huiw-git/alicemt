---
title: Default C Data Types
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 229140ae-af8f-4ec8-9ccf-1e92360e0bac
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Default C Data Types
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>If an application specifies SQL_C_DEFAULT in <legacyBold>SQLBindCol</legacyBold>, <legacyBold>SQLGetData</legacyBold>, or <legacyBold>SQLBindParameter</legacyBold>, the driver assumes that the C data type of the output or input buffer corresponds to the SQL data type of the column or parameter to which the buffer is bound.</para>
    <alert class="important">
      <para>Interoperable applications should not use SQL_C_DEFAULT. Instead, they should always specify the C type of the buffer they are using. This is because drivers cannot always correctly determine the default C type, for the following reasons:</para>
    </alert>
    <list class="bullet">
      <listItem>
        <para>If the DBMS promotes an SQL data type of a column or parameter, the driver cannot determine the original SQL data type of a column or parameter. Therefore, it cannot determine the corresponding default C data type.</para>
      </listItem>
      <listItem>
        <para>If the driver cannot determine whether a particular column or parameter is signed, as is often the case when this is handled by the DBMS, the driver cannot determine whether the corresponding default C data type should be signed or unsigned. </para>
        <para>Because SQL_C_DEFAULT is provided only as a programming convenience, the application does not lose any functionality when it specifies the actual C data type. </para>
      </listItem>
    </list>
    <para>A table showing the default C data type for each SQL data type is included in <legacyLink xlink:href="029727f6-d3f0-499a-911c-bcaf9714e43b">Converting Data from SQL to C Data Types</legacyLink>, later in this appendix.</para>
  </introduction>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>