---
title: Dynamic Tracing
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ebe58a83-a7b0-4747-86c8-2af2940471ef
manager:jhubbard
translation.priority.ht: 
  - en-gb
---
# Dynamic Tracing
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Tracing can be enabled or disabled at any point in an application run. This allows an application to trace any number of function calls.</para>
    <para>The variable <legacyBold>ODBCSharedTraceFlag</legacyBold> is set to enable tracing dynamically. This variable is shared among all running copies of the Driver Manager. If any application sets this variable, tracing is enabled for all ODBC applications currently running. To turn tracing off when dynamic tracing is enabled, an application calls <legacyBold>SQLSetConnectAttr</legacyBold> to set SQL_ATTR_TRACE to SQL_TRACE_OFF. This call will turn tracing off for that application only. Applications that are linked with Odbc32.lib can modify use of this variable. Trace data can be displayed in a real-time window, instead of the trace file, which must be opened after the ODBC session. Controls can be added to an application's screen to turn tracing on or off at will.</para>
    <para>The trace DLL shipped with ODBC 3<legacyItalic>.x</legacyItalic> is not thread-safe. It is not guaranteed that the log file is written correctly if global tracing is enabled (the variable <legacyBold>ODBCSharedTraceFlag</legacyBold> is set) and more than one application writes to the trace file at the same time. This condition does not return an error.</para>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>