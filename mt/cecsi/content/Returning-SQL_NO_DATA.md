---
title: "Returning SQL_NO_DATA"
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: deed0163-9d1a-4e9b-9342-3f82e64477d2
caps.latest.revision: 4
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Returning SQL_NO_DATA
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>When an ODBC 2.<legacyItalic>x</legacyItalic> application workingwith an ODBC 3<legacyItalic>.x</legacyItalic> driver calls <legacyBold>SQLExecDirect</legacyBold>, <legacyBold>SQLExecute</legacyBold>, or <legacyBold>SQLParamData</legacyBold>, and a searched update or delete statement was executed but did not affect any rows at the data source, the ODBC 3<legacyItalic>.x</legacyItalic> driver should return SQL_SUCCESS. When an ODBC 3<legacyItalic>.x</legacyItalic> application working with an ODBC 3<legacyItalic>.x</legacyItalic> driver calls <legacyBold>SQLExecDirect</legacyBold>, <legacyBold>SQLExecute</legacyBold>, or <legacyBold>SQLParamData</legacyBold> with the same result, the ODBC 3<legacyItalic>.x</legacyItalic> driver should return SQL_NO_DATA. </para>
  </introduction>
  <section>
    <content>
      <para>If a searched update or delete statement in a batch of statements does not affect any rows at the data source, <legacyBold>SQLMoreResults</legacyBold> returns SQL_SUCCESS. It cannot return SQL_NO_DATA, because that would mean that there are no more results, not that there is a result from a searched update/delete that affected no rows.</para>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>