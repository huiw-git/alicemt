---
title: "SQLTransact Mapping"
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 8a01041f-3572-46f9-8213-b817f3cf929c
caps.latest.revision: 4
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# SQLTransact Mapping
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>
      <legacyBold>SQLTransact</legacyBold> is now replaced by <legacyBold>SQLEndTran</legacyBold>. The major difference between the two functions is that <legacyBold>SQLEndTran</legacyBold> contains an argument <legacyItalic>HandleType</legacyItalic>, which specifies the scope of the work to be done. The <legacyItalic>HandleType</legacyItalic> argument can specify the environment or the connection handle. The following call to <legacyBold>SQLTransact</legacyBold>:</para>
  </introduction>
  <section>
    <content>
      <code>SQLTransact(henv, hdbc, fType)</code>
      <para>is mapped to</para>
      <code>SQLEndTran(SQL_HANDLE_DBC, ConnectionHandle, CompletionType);</code>
      <para>if <legacyItalic>ConnectionHandle</legacyItalic> is not equal to SQL_NULL_HDBC. The <legacyItalic>ConnectionHandle</legacyItalic> argument is set to the value of <legacyItalic>hdbc</legacyItalic>. </para>
      <para>
        <legacyBold>SQL_Transact</legacyBold> is mapped to</para>
      <code>SQLEndTran (SQL_HANDLE_ENV, EnvironmentHandle, CompletionType);</code>
      <para>if <legacyItalic>ConnectionHandle</legacyItalic> is equal to SQL_NULL_HDBC. The <legacyItalic>EnvironmentHandle</legacyItalic> argument is set to the value of <legacyItalic>henv</legacyItalic>.</para>
      <para>In both of the preceding cases, the <legacyItalic>CompletionType</legacyItalic> argument is set to the same value as <legacyItalic>fType</legacyItalic>.</para>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>