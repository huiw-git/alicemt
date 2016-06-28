---
title: SQLParamOptions Mapping
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 57ed65f6-9620-4738-b331-19d2a2b5cae4
translation.priority.ht: 
  - en-gb
---
# SQLParamOptions Mapping
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>When an application calls <legacyBold>SQLParamOptions</legacyBold> through an ODBC 3<legacyItalic>.x</legacyItalic> driver, the call</para>
  </introduction>
  <section>
    <content>
      <code>SQLParamOptions(hstmt, crow, piRow);</code>
      <para>will be mapped to two calls of <legacyBold>SQLSetStmtAttr</legacyBold> as follows:</para>
      <code>SQLSetStmtAttr(hstmt, SQL_ATTR_PARAMSET_SIZE, crow, 0);
SQLSetStmtAttr(hstmt, SQL_ATTR_PARAMS_PROCESSED_PTR, piRow, 0);</code>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>