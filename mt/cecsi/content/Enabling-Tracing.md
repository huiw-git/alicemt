---
title: "Enabling Tracing"
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 48e318bd-2487-4708-a698-ea01f36a45e9
caps.latest.revision: 4
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Enabling Tracing
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Tracing can be enabled in the following three ways:  </para>
    <list class="bullet">
      <listItem>
        <para>Set the <legacyBold>Trace</legacyBold> and <legacyBold>TraceFile</legacyBold> keywords in the Odbc.ini registry entry. This enables or disables tracing when <legacyBold>SQLAllocHandle</legacyBold> with a <legacyItalic>HandleType</legacyItalic> of SQL_HANDLE_ENV is called. These options are set in the Tracing tab of the ODBC Data Source Administrator dialog box displayed during data source setup. For more information, see <legacyLink xlink:href="78aaa3d3-d081-4550-80e3-720c910d5996">Registry Entries for Data Sources</legacyLink>.</para>
      </listItem>
      <listItem>
        <para>Call <legacyBold>SQLSetConnectAttr</legacyBold> to set the SQL_ATTR_TRACE connection attribute to SQL_OPT_TRACE_ON. This enables or disables tracing for the duration of the connection. For more information, see the <legacyLink xlink:href="97fc7445-5a66-4eb9-8e77-10990b5fd685">SQLSetConnectAttr</legacyLink> function description.</para>
      </listItem>
      <listItem>
        <para>Use <legacyBold>ODBCSharedTraceFlag</legacyBold> to turn tracing on or off dynamically. (For more information, see the next topic, <legacyLink xlink:href="ebe58a83-a7b0-4747-86c8-2af2940471ef">Dynamic Tracing</legacyLink>.)</para>
      </listItem>
    </list>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>