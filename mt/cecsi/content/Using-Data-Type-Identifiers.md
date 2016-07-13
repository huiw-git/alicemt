---
title: Using Data Type Identifiers
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 467e0c0c-a818-4737-8a24-3d8e15c7e162
manager:jhubbard
translation.priority.ht: 
  - en-gb
---
# Using Data Type Identifiers
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Applications use data type identifiers in two ways: to describe their buffers to the driver, and to retrieve metadata about the result set from the driver so that they can determine what type of C buffers to use to store the data. Applications call the following functions to perform these tasks:

</para>
  </introduction>
  <section>
    <content>
      <list class="bullet">
        <listItem>
          <para>
            <legacyBold>SQLBindParameter</legacyBold>, <legacyBold>SQLBindCol</legacyBold>, and <legacyBold>SQLGetData</legacyBold>
					— to describe the C data type of application buffers.</para>
        </listItem>
        <listItem>
          <para>
            <legacyBold>SQLBindParameter</legacyBold>
					— to describe the SQL data type of dynamic parameters.</para>
        </listItem>
        <listItem>
          <para>
            <legacyBold>SQLColAttribute</legacyBold> and <legacyBold>SQLDescribeCol</legacyBold>
					— to retrieve the SQL data types of result set columns.</para>
        </listItem>
        <listItem>
          <para>
            <legacyBold>SQLDescribeParameter</legacyBold>
					— to retrieve the SQL data types of parameters.</para>
        </listItem>
        <listItem>
          <para>
            <legacyBold>SQLColumns</legacyBold>, <legacyBold>SQLProcedureColumns</legacyBold>, and <legacyBold>SQLSpecialColumns</legacyBold>
					— to retrieve the SQL data types of various schema information</para>
        </listItem>
        <listItem>
          <para>
            <legacyBold>SQLGetTypeInfo</legacyBold>
					— to retrieve a list of supported data types</para>
        </listItem>
      </list>
      <para>Data type identifiers are stored in the SQL_DESC_CONCISE_TYPE field of a descriptor. The descriptor functions <legacyBold>SQLSetDescField</legacyBold> and <legacyBold>SQLSetDescRec</legacyBold> can be used with the appropriate types to perform the tasks listed in the previous list. For more information, see <legacyLink xlink:href="8c544388-fe9d-4f94-a0ac-fa0b9c9c88a5">SQLSetDescField</legacyLink>.</para>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>