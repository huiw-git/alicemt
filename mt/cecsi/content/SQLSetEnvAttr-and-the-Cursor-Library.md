---
title: SQLSetEnvAttr and the Cursor Library
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 59cc8eae-09ae-4796-869a-c5806488ae83
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# SQLSetEnvAttr and the Cursor Library
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <alert class="important">
      <para>This feature will be removed in a future version of Windows. Avoid using this feature in new development work and plan to modify applications that currently use this feature. Microsoft recommends using the driver's cursor functionality.</para>
    </alert>
    <para>This topic discusses the use of the <legacyBold>SQLSetEnvAttr</legacyBold> function with the cursor library. For general information about <legacyBold>SQLSetEnvAttr</legacyBold>, see <legacyLink xlink:href="0343241c-4b15-4d4b-aa2b-2e8ab5215cd2">SQLSetEnvAttr Function</legacyLink>.</para>
  </introduction>
  <section>
    <content>
      <para>The cursor library is unaffected by the setting of the SQL_ATTR_ODBC_VERSION environment attribute, regardless of the application version or driver version.</para>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>