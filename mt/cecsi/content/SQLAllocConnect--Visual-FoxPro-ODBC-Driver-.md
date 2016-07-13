---
title: SQLAllocConnect (Visual FoxPro ODBC Driver)
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 70d48b12-def5-475c-b8e1-654a55fdfe0f
manager:jhubbard
translation.priority.ht: 
  - en-gb
---
# SQLAllocConnect (Visual FoxPro ODBC Driver)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <alert class="note">
      <para>This topic contains Visual FoxPro ODBC Driver-specific information. For general information about this function, see the appropriate topic under <legacyLink xlink:href="b7a49774-f458-44ce-9a04-a0457501405b">ODBC API Reference</legacyLink>.</para>
    </alert>
    <para>Support: Full </para>
    <para>ODBC API Conformance: Core Level</para>
    <para>Allocates memory for a connection handle, <legacyItalic>hdbc</legacyItalic>, within the environment identified by <legacyItalic>henv</legacyItalic>. The Driver Manager processes this call and calls the driver's <legacyBold>SQLAllocConnect</legacyBold> whenever <legacyLink xlink:href="49cbfafa-b21e-4e89-b248-9c7098f46b20">SQLConnect</legacyLink>, <legacyBold>SQLBrowseConnect</legacyBold>, or <legacyLink xlink:href="10492c8f-3a18-4971-9db8-879e878083b9">SQLDriverConnect</legacyLink> is called.</para>
    <para>For more information, see <legacyLink xlink:href="ca119958-ff72-42d4-b0ac-b1ca3212c705">SQLAllocConnect</legacyLink> in the <legacyItalic>ODBC Programmer's Reference</legacyItalic>.</para>
  </introduction>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>