---
title: Buffers
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 42c5226c-cb40-4d1e-809f-2ea50ce6bd55
manager:jhubbard
translation.priority.ht: 
  - en-gb
---
# Buffers
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>A buffer is any piece of application memory used to pass data between the application and the driver. For example, application buffers can be associated with, or <legacyItalic>bound to,</legacyItalic> result set columns with <legacyBold>SQLBindCol</legacyBold>. As each row is fetched, the data is returned for each column in these buffers. <legacyItalic>Input buffers</legacyItalic> are used to pass data from the application to the driver; <legacyItalic>output buffers</legacyItalic> are used to return data from the driver to the application.</para>
    <alert class="note">
      <para>If an ODBC function returns SQL_ERROR, the contents of any output arguments to that function are undefined.</para>
    </alert>
    <para>This discussion concerns itself primarily with buffers of indeterminate type. The addresses of these buffers appear as arguments of type SQLPOINTER, such as the <legacyItalic>TargetValuePtr</legacyItalic> argument in <legacyBold>SQLBindCol</legacyBold>. However, some of the items discussed here, such as the arguments used with buffers, also apply to arguments used to pass strings to the driver, such as the <legacyItalic>TableName</legacyItalic> argument in <legacyBold>SQLTables</legacyBold>.</para>
    <para>These buffers usually come in pairs. <legacyItalic>Data buffers</legacyItalic> are used to pass the data itself, while <legacyItalic>length/indicator buffers</legacyItalic> are used to pass the length of the data in the data buffer or a special value such as SQL_NULL_DATA, which indicates that the data is NULL. The length of the data in a data buffer is different from the length of the data buffer itself. The following illustration shows the relationship between the data buffer and the length/indicator buffer.</para>
    <mediaLink>
      <image xlink:href="cac2fb34-b8d6-4041-bc34-1b299f7f3f0b" />
    </mediaLink>
    <para>A length/indicator buffer is required whenever the data buffer contains variable-length data, such as character or binary data. If the data buffer contains fixed-length data, such as an integer or date structure, a length/indicator buffer is needed only to pass indicator values because the length of the data is already known. If an application uses a length/indicator buffer with fixed-length data, the driver ignores any lengths passed in it.</para>
    <para>The length of both the data buffer and the data it contains is measured in bytes, as opposed to characters. This distinction is unimportant for programs that use ANSI strings because lengths in bytes and characters are the same.</para>
    <para>When the data buffer represents a driver-defined descriptor field, diagnostic field, or attribute, the application should indicate to the Driver Manager the nature of the function argument that indicates the value for the field or attribute. The application does this by setting the length argument in any function call that sets the field or attribute to one of the following values. (The same is true for functions that retrieve the values of the field or attribute, with the exception that the argument points to the values that for the setting function are in the argument itself.)  </para>
    <list class="bullet">
      <listItem>
        <para>If the function argument that indicates the value for the field or attribute is a pointer to a character string, the <legacyItalic>length</legacyItalic> argument is the length of the string or SQL_NTS.</para>
      </listItem>
      <listItem>
        <para>If the function argument that indicates the value for the field or attribute is a pointer to a binary buffer, the application places the result of the SQL_LEN_BINARY_ATTR(<legacyItalic>length</legacyItalic>) macro in the <legacyItalic>length</legacyItalic> argument. This places a negative value in the <legacyItalic>length</legacyItalic> argument.</para>
      </listItem>
      <listItem>
        <para>If the function argument that indicates the value for the field or attribute is a pointer to a value other than a character string or a binary string, the <legacyItalic>length </legacyItalic>argument should have the value SQL_IS_POINTER.</para>
      </listItem>
      <listItem>
        <para>If the function argument that indicates the value for the field or attribute contains a fixed-length value, the <legacyItalic>length</legacyItalic> argument is SQL_IS_INTEGER, SQL_IS_UINTEGER, SQL_IS_SMALLINT, or SQL_ISI_USMALLINT, as appropriate.</para>
      </listItem>
    </list>
    <para>This section contains the following topics.  </para>
    <list class="bullet">
      <listItem>
        <para>
          <legacyLink xlink:href="02c9a75c-2103-4f68-a1db-e31f7e0f1f03">Deferred Buffers</legacyLink>
        </para>
      </listItem>
      <listItem>
        <para>
          <legacyLink xlink:href="886bc9ed-39d4-43d2-82ff-aebc35b14d39">Allocating and Freeing Buffers</legacyLink>
        </para>
      </listItem>
      <listItem>
        <para>
          <legacyLink xlink:href="06b9f603-b395-497c-979b-d3ec3d6db375">Using Data Buffers</legacyLink>
        </para>
      </listItem>
    </list>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>