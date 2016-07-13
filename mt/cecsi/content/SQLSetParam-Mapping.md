---
title: SQLSetParam Mapping
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 022dfbc0-8d18-4c35-8a28-d9eb16063188
manager:jhubbard
translation.priority.ht: 
  - en-gb
---
# SQLSetParam Mapping
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>
      <legacyBold>SQLSetParam</legacyBold> continues to be mapped on top of <legacyBold>SQLBindParameter</legacyBold> as in ODBC 2.<legacyItalic>x</legacyItalic>. Even though it is conceptually similar to <legacyBold>SQLBindParam</legacyBold>, the Driver Manager does not map <legacyBold>SQLSetParam</legacyBold> to <legacyBold>SQLBindParam</legacyBold>. This is because certain existing ODBC 2.<legacyItalic>x</legacyItalic> drivers use the special value of <legacyItalic>BufferLength</legacyItalic> (SQL_SETPARAM_VALUE_MAX) that the Driver Manager generates when it maps <legacyBold>SQLSetParam</legacyBold> on top of <legacyBold>SQLBindParameter</legacyBold> to determine when it is called by a 1.<legacyItalic>x</legacyItalic> ODBC application.</para>
  </introduction>
  <section>
    <content>
      <para>A call to</para>
      <code>SQLSetParam(hstmt, ipar, fCType, fSqlType, cbColDef, ibScale, rgbValue, pcbValue)</code>
      <para>will result in the following:</para>
      <code>SQLBindParameter(StatementHandle, ParameterNumber, SQL_PARAM_INPUT_OUTPUT, ValueType, ParameterType, ColumnSize, DecimalDigits, ParameterValuePtr, SQL_SETPARAM_VALUE_MAX, StrLen_or_IndPtr)</code>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>