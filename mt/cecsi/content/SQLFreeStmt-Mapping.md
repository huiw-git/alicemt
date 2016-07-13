---
title: SQLFreeStmt Mapping
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 267d95f2-4f0c-47ab-9411-5afe105215a2
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# SQLFreeStmt Mapping
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>When an application calls <legacyBold>SQLFreeStmt</legacyBold> with an <legacyItalic>Option</legacyItalic> argument of SQL_DROP through an ODBC 3<legacyItalic>.x</legacyItalic> driver, the call to</para>
  </introduction>
  <section>
    <content>
      <code>SQLFreeStmt(hstmt, SQL_DROP) </code>
      <para>is mapped to</para>
      <code>SQLFreeHandle(SQL_HANDLE_STMT,Handle)</code>
      <para>with the <legacyItalic>Handle</legacyItalic> argument set to the value in <legacyItalic>hstmt</legacyItalic>.</para>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>