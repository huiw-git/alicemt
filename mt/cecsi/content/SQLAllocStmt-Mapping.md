---
title: "SQLAllocStmt Mapping"
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a2449dbb-1b6c-4b49-81b9-ebdddd4442fd
caps.latest.revision: 4
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# SQLAllocStmt Mapping
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>When an application calls <legacyBold>SQLAllocStmt</legacyBold> through an ODBC 3<legacyItalic>.x</legacyItalic> driver, the call to:</para>
  </introduction>
  <section>
    <content>
      <code>SQLAllocStmt(hdbc, phstmt)</code>
      <para>is mapped to <legacyBold>SQLAllocHandle</legacyBold> by the Driver Manager in the driver as follows:</para>
      <code>SQLAllocHandle(SQL_HANDLE_STMT, InputHandle, OutputHandlePtr)</code>
      <para>with <legacyItalic>InputHandle</legacyItalic> set to <legacyItalic>hdbc</legacyItalic> and <legacyItalic>OutputHandlePtr</legacyItalic> set to <legacyItalic>phstmt</legacyItalic>.</para>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>