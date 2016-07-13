---
title: Connection Strings
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 724c7b86-300a-4fa9-ad96-4afa0fdcb3e9
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Connection Strings
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>A connection string contains information used for establishing a connection. A complete connection string contains all the information needed to establish a connection. The connection string is a series of keyword/value pairs separated by semicolons. (For the complete syntax of a connection string, see the <legacyLink xlink:href="e299be1d-5c74-4ede-b6a3-430eb189134f">SQLDriverConnect</legacyLink> function description.) The connection string is used by:  </para>
    <list class="bullet">
      <listItem>
        <para>             <legacyBold>SQLDriverConnect</legacyBold>, which completes the connection string by interaction with the user.</para>
      </listItem>
      <listItem>
        <para>             <legacyBold>SQLBrowseConnect</legacyBold>, which completes the connection string iteratively with the data source.</para>
      </listItem>
    </list>
    <para>         <legacyBold>SQLConnect</legacyBold> does not use a connection string; using <legacyBold>SQLConnect</legacyBold> is analogous to connecting using a connection string with exactly three keyword/value pairs (for data source name and, optionally, user ID and password).</para>
  </introduction>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>