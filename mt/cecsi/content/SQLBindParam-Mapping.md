---
title: SQLBindParam Mapping
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 375f8f24-36de-4946-916e-c75abc6f070d
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# SQLBindParam Mapping
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>
      <legacyBold>SQLBindParam</legacyBold> cannot truly be called deprecated because it was never there in ODBC; however, it still represents duplicated functionality — the Driver Manager needs to export it because ISO and Open Group–compliant applications will be using it. Because <legacyBold>SQLBindParameter</legacyBold> contains all the functionality of <legacyBold>SQLBindParam</legacyBold>, <legacyBold>SQLBindParam</legacyBold> will be mapped on top of <legacyBold>SQLBindParameter</legacyBold> (when the underlying driver is an ODBC 3<legacyItalic>.x</legacyItalic> driver). An ODBC 3<legacyItalic>.x</legacyItalic> driver does not need to implement <legacyBold>SQLBindParam</legacyBold>.</para>
  </introduction>
  <languageReferenceRemarks>
    <content>
      <para>When the following call to <legacyBold>SQLBindParam</legacyBold> is made:</para>
      <code>SQLBindParam(   StatementHandle,    ParameterNumber,    ValueType,    ParameterType,    ColumnSize,    DecimalDigits,    ParameterValuePtr,    StrLen_or_IndPtr)</code>
      <para>the Driver Manager calls <legacyBold>SQLBindParameter</legacyBold> in the driver as follows:</para>
      <code>SQLBindParameter(   StatementHandle,    ParameterNumber,    SQL_PARAM_INPUT,    ValueType,    ParameterType,    ColumnSize,    DecimalDigits,    ParameterValuePtr,    BufferLength,    StrLen_or_IndPtr)</code>
      <para>See <link xlink:href="ed9851ce-44ee-4c8e-b626-1d0b52da30fe">ODBC 64-Bit Information</link>, if your application will run on a 64-bit operating system.</para>
    </content>
  </languageReferenceRemarks>
  <relatedTopics>
<link xlink:href="ee462617-1d79-4c88-afeb-b129cff34cc6">Mapping Deprecated Functions</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>