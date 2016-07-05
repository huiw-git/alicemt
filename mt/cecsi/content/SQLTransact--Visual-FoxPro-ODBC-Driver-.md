---
title: SQLTransact (Visual FoxPro ODBC Driver)
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 92cf86c0-f7a8-44d7-b59f-a1342677440b
translation.priority.ht: 
  - en-gb
---
# SQLTransact (Visual FoxPro ODBC Driver)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <alert class="note">
      <para>This topic contains Visual FoxPro ODBC Driver-specific information. For general information about this function, see the appropriate topic under <legacyLink xlink:href="b7a49774-f458-44ce-9a04-a0457501405b">ODBC API Reference</legacyLink>.</para>
    </alert>
    <para>Support: Full </para>
    <para>ODBC API Conformance: Core Level</para>
    <para>Requests a commit or rollback operation for all active operations on all statement handles (<legacyItalic>hstmt</legacyItalic>s) associated with a connection or for all connections associated with the environment handle, <legacyItalic>henv</legacyItalic>. <legacyBold>SQLTransact</legacyBold> works only for data sources that are <legacyLink xlink:href="a379b3cb-0393-46e7-b03b-724a56d8f31c">databases</legacyLink>.</para>
    <para>If a commit fails when in manual mode, the transaction remains active; you can choose to roll back the transaction or retry the commit operation. If a commit operation fails when in automatic transaction mode, the transaction is rolled back automatically; the transaction cannot be inactive.</para>
    <para>For more information, see <legacyLink xlink:href="496249e0-8eff-4c60-8358-5543bc3ead9c">SQLTransact</legacyLink> in the <legacyItalic>ODBC Programmer's Reference</legacyItalic>.</para>
  </introduction>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>