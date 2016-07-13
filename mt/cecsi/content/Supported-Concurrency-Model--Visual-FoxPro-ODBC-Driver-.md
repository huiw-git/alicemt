---
title: Supported Concurrency Model (Visual FoxPro ODBC Driver)
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c39ed963-3af1-4888-8631-6083692ddcd7
manager:jhubbard
translation.priority.ht: 
  - en-gb
---
# Supported Concurrency Model (Visual FoxPro ODBC Driver)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The Visual FoxPro ODBC Driver supports <legacyItalic>read-only concurrency</legacyItalic>. Your application can call <legacyLink xlink:href="76b813e3-c7dc-4bb2-a710-d2aa9dcfdc36">SQLSetStmtOption</legacyLink> with a SQL_CONCURRENCY option of SQL_CONCUR_READ_ONLY.</para>
    <para>For more information, see the <legacyLink xlink:href="b33c3c43-ae66-44a3-be17-9cd82624dd96">ODBC Programmer's Reference</legacyLink>.</para>
  </introduction>
  <section>
    <title>read-only concurrency</title>
    <content>
      <para>The cursor cannot be updated.</para>
    </content>
  </section>
  <section>
    <title>row versioning</title>
    <content>
      <para>Essentially timestamp support, in which row versions are compared at update time.</para>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>