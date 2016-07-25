---
title: "SQL_NO_DATA"
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 07a4144a-a548-4578-b2be-715c3cf73bf8
caps.latest.revision: 4
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# SQL_NO_DATA
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>When an ODBC 3.<legacyItalic>x</legacyItalic> application calls <legacyBold>SQLExecDirect</legacyBold>, <legacyBold>SQLExecute</legacyBold>, or <legacyBold>SQLParamData</legacyBold> in an ODBC 2.<legacyItalic>x</legacyItalic> driver to execute a searched update or delete statement that does not affect any rows at the data source, the driver should return SQL_SUCCESS, not SQL_NO_DATA. When an ODBC 2.<legacyItalic>x</legacyItalic> or ODBC 3.<legacyItalic>x</legacyItalic> application working with an ODBC 3.<legacyItalic>x</legacyItalic> driver calls <legacyBold>SQLExecDirect</legacyBold>, <legacyBold>SQLExecute</legacyBold>, or <legacyBold>SQLParamData</legacyBold> with the same result, the ODBC 3.<legacyItalic>x</legacyItalic> driver should return SQL_NO_DATA.</para>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>