---
title: "SQL_ARD_TYPE"
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 8d87ca10-f955-4284-8689-e9f4cc31e7ae
caps.latest.revision: 5
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# SQL_ARD_TYPE
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The SQL_ARD_TYPE type identifier is used to indicate that the data in a buffer will be of the type specified in the SQL_DESC_CONCISE_TYPE field of the ARD. SQL_ARD_TYPE is entered in the <legacyItalic>TargetType</legacyItalic> argument of a call to <legacyBold>SQLGetData</legacyBold> instead of a specific data type and enables an application to change the data type of the buffer by changing the descriptor field. This value ties the data type of the <legacyItalic>*TargetValuePtr</legacyItalic> buffer to the descriptor field. (SQL_ARD_TYPE is not entered in a call to <legacyBold>SQLBindCol</legacyBold> or <legacyBold>SQLBindParameter</legacyBold> because the type of the bound buffer is already tied to the SQL_DESC_TYPE and SQL_DESC_CONCISE_TYPE fields and can be changed at any time by changing either of those fields.)</para>
    <para>The SQL_ARD_TYPE type identifier can be used to specify nondefault values for leading precision and seconds precision of interval data types, and precision and scale values for the SQL_C_NUMERIC data type. For more information, see <legacyLink xlink:href="3d65493f-dce7-4d29-9f59-c63a4e47918c">Overriding Default Leading and Seconds Precision for Interval Data Types</legacyLink> and <legacyLink xlink:href="84292334-0e33-4a1b-84de-8c018dd787f3">Overriding Default Precision and Scale for Numeric Data Types</legacyLink>, later in this appendix.</para>
  </introduction>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>