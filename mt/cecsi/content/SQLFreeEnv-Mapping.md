---
title: SQLFreeEnv Mapping
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c0f76455-d072-4bae-bee7-452277dfa479
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# SQLFreeEnv Mapping
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>When an application calls <legacyBold>SQLFreeEnv</legacyBold> through an ODBC 3<legacyItalic>.x</legacyItalic> driver, the call to</para>
  </introduction>
  <section>
    <content>
      <code>SQLFreeEnv(henv) </code>
      <para>is mapped to</para>
      <code>SQLFreeHandle(SQL_HANDLE_ENV,Handle)</code>
      <para>with the <legacyItalic>Handle</legacyItalic> argument set to the value in <legacyItalic>henv</legacyItalic>.</para>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>