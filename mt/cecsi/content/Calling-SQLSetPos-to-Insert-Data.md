---
title: Calling SQLSetPos to Insert Data
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 03e5c4d0-2bb3-4649-9781-89cab73f78eb
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Calling SQLSetPos to Insert Data
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>When an ODBC 2.<legacyItalic>x</legacyItalic> application working with an ODBC 3<legacyItalic>.x</legacyItalic> driver calls <legacyBold>SQLSetPos</legacyBold> with an <legacyItalic>Operation</legacyItalic> argument of SQL_ADD, the Driver Manager does not map this call to <legacyBold>SQLBulkOperations</legacyBold>. If an ODBC 3<legacyItalic>.x</legacyItalic> driver should work with an application that calls <legacyBold>SQLSetPos</legacyBold> with SQL_ADD, the driver should support that operation.</para>
  </introduction>
  <section>
    <content>
      <para>One major difference in behavior when <legacyBold>SQLSetPos</legacyBold> is called with SQL_ADD occurs when it is called in state S6. In ODBC 2.<legacyItalic>x</legacyItalic>, the driver returned S1010 when <legacyBold>SQLSetPos</legacyBold> was called with SQL_ADD in state S6 (after the cursor has been positioned with <legacyBold>SQLFetch</legacyBold>). In ODBC 3<legacyItalic>.x</legacyItalic>, <legacyBold>SQLBulkOperations</legacyBold> with an <legacyItalic>Operation</legacyItalic> of SQL_ADD can be called in state S6. A second major difference in behavior is that <legacyBold>SQLBulkOperations</legacyBold> with an <legacyItalic>Operation</legacyItalic> of SQL_ADD can be called in state S5, while <legacyBold>SQLSetPos</legacyBold> with an <legacyBold>Operation</legacyBold> of SQL_ADD cannot. For the statement transitions that can occur for the same call in ODBC 3<legacyItalic>.x</legacyItalic>, see <legacyLink xlink:href="15088dbe-896f-4296-b397-02bb3d0ac0fb">Appendix B: ODBC State Transition Tables</legacyLink>.</para>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>