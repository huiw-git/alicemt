---
title: Determining Cursor Capabilities
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 35be486c-8f2d-4cec-beb8-df14151abfef
manager:jhubbard
translation.priority.ht: 
  - en-gb
---
# Determining Cursor Capabilities
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The following four options in <legacyBold>SQLGetInfo</legacyBold> describe what types of cursors are supported and what their capabilities are:  </para>
    <list class="bullet">
      <listItem>
        <para>SQL_CURSOR_SENSITIVITY. Indicates whether a cursor is sensitive to changes made by another cursor.</para>
      </listItem>
      <listItem>
        <para>SQL_SCROLL_OPTIONS. Lists the supported cursor types (forward-only, static, keyset-driven, dynamic, or mixed). All data sources must support forward-only cursors.</para>
      </listItem>
      <listItem>
        <para>SQL_DYNAMIC_CURSOR_ATTRIBUTES1, SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES1, SQL_KEYSET_CURSOR_ATTRIBUTES1, or SQL_STATIC_CURSOR_ATTRIBUTES1 (depending on the type of the cursor). Lists the fetch types supported by scrollable cursors. The bits in the return value correspond to the fetch types in <legacyBold>SQLFetchScroll</legacyBold>.</para>
      </listItem>
      <listItem>
        <para>SQL_KEYSET_CURSOR_ATTRIBUTES2 or SQL_STATIC_CURSOR_ATTRIBUTES2 (depending on the type of the cursor). Lists whether static and keyset-driven cursors can detect their own updates, deletes, and inserts.</para>
      </listItem>
    </list>
    <para>An application can determine cursor capabilities at run time by calling <legacyBold>SQLGetInfo</legacyBold> with these options. This is commonly done by generic applications. Cursor capabilities also can be determined during application development and their use hard-coded into the application. This is commonly done by vertical and custom applications but can also be done by generic applications that use a client-side cursor implementation such as the ODBC cursor library.</para>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>