---
title: "Driver Manager Diagnostic Example"
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: af8f2d35-d1bf-495c-af25-630654542b7d
caps.latest.revision: 4
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Driver Manager Diagnostic Example
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The Driver Manager can also generate diagnostic messages. For example, if an application passed an invalid direction option to <legacyBold>SQLDataSources</legacyBold>, the Driver Manager might format and return the following values from <legacyBold>SQLGetDiagRec</legacyBold>:</para>
    <code>SQLSTATE:         "HY103"
Native Error:      0
Diagnostic Msg:   "[Microsoft][ODBC Driver Manager]Direction option out of range"</code>
    <para>Because the error occurred in the Driver Manager, it added prefixes to the diagnostic message for its vendor ([Microsoft]) and its identifier ([ODBC Driver Manager]).</para>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>