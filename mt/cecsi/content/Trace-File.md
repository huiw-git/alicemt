---
title: Trace File
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ec97f949-126f-40a2-b67e-e74520a524cb
manager:jhubbard
translation.priority.ht: 
  - en-gb
---
# Trace File
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>An application specifies the trace file either by setting the <legacyBold>TraceFile</legacyBold> keyword in the Odbc.ini registry entry or by calling <legacyBold>SQLSetConnectAttr</legacyBold> with the SQL_ATTR_TRACEFILE connection attribute. If the file does not exist when tracing is enabled, the Driver Manager will create the file. Each application should have its own dedicated trace file to avoid contention. An application can use more than one trace file; an application's setup program can provide the user with a choice of trace files. If tracing is enabled dynamically, an application can also display trace results, rather than logging to the trace file.</para>
    <para>The trace file provides a log of each ODBC function call with the data types and values of all arguments. It logs all input functions and logs all returned functions with return codes and error states.</para>
    <para>In ODBC 3<legacyItalic>.x</legacyItalic>, parameters to connection functions are not provided to the trace DLL.</para>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>