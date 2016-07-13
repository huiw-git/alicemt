---
title: SQLError Mapping
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 802ac711-7e5d-4152-9698-db0cafcf6047
manager:jhubbard
translation.priority.ht: 
  - en-gb
---
# SQLError Mapping
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>When an application calls <legacyBold>SQLError</legacyBold> through an ODBC 3<legacyItalic>.x</legacyItalic> driver, the call to</para>
  </introduction>
  <section>
    <content>
      <code>SQLError(henv, hdbc, hstmt, szSqlState, pfNativeError, szErrorMsg, cbErrorMsgMax, pcbErrorMsg) </code>
      <para>is mapped to</para>
      <code>SQLGetDiagRec(HandleType, Handle, RecNumber, szSqlstate, pfNativeErrorPtr, szErrorMsg, cbErrorMsgMax, pcbErrorMsg)</code>
      <para>with the <legacyItalic>HandleType</legacyItalic> argument set to the value SQL_HANDLE_ENV, SQL_HANDLE_DBC, or SQL_HANDLE_STMT, as appropriate, and the <legacyItalic>Handle</legacyItalic> argument set to the value in <legacyItalic>henv</legacyItalic>, <legacyItalic>hdbc</legacyItalic>, or<legacyItalic> hstmt</legacyItalic>, as appropriate. The <legacyItalic>RecNumber</legacyItalic> argument is determined by the Driver Manager.</para>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>