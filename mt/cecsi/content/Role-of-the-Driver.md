---
title: Role of the Driver
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: cac64c24-a27d-4884-96c0-ea7988351711
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Role of the Driver
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The driver checks for all errors and warnings not checked by the Driver Manager and orders status records that it generates. (An ODBC 2.<legacyItalic>x</legacyItalic> driver does not order status records.) This includes errors and warnings in data truncation, data conversion, syntax, and some state transitions. The driver might also check errors and warnings partially checked by the Driver Manager. For example, although the Driver Manager checks whether the value of <legacyItalic>Operation</legacyItalic> in <legacyBold>SQLSetPos</legacyBold> is legal, the driver must check whether it is supported.</para>
    <para>The driver also maps <legacyItalic>native errors</legacyItalic> — that is, errors returned by the data source — to SQLSTATEs. For example, the driver might map a number of different native errors for illegal SQL syntax to SQLSTATE 42000 (Syntax error or access violation). The driver returns the native error number in the SQL_DIAG_NATIVE field of the status record. Driver documentation should show how errors and warnings are mapped from the data source to arguments in <legacyBold>SQLGetDiagRec</legacyBold> and <legacyBold>SQLGetDiagField</legacyBold>.</para>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>