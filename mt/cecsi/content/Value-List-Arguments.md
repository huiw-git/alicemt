---
title: Value List Arguments
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 863837be-603b-4c7a-8b96-b71014037ee5
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Value List Arguments
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>A value list argument consists of a list of comma-separated values to be used for matching. There is only one value list argument in the ODBC catalog functions: the <legacyItalic>TableType</legacyItalic> argument in <legacyBold>SQLTables</legacyBold>. Setting <legacyItalic>TableType</legacyItalic> to a null pointer is the same as if it is set to SQL_ALL_TABLE_TYPES, which enumerates all possible members of the value list. This argument is not affected by the SQL_ATTR_METADATA_ID statement attribute. For more information, see the <legacyLink xlink:href="60d5068a-7d7c-447c-acc6-f3f2cf73440c">SQLTables</legacyLink> function description.</para>
  </introduction>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>