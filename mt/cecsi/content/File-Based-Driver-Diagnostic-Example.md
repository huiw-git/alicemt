---
title: File-Based Driver Diagnostic Example
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0575fccd-4641-478d-a3cc-5a764e35bae2
translation.priority.ht: 
  - en-gb
---
# File-Based Driver Diagnostic Example
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>A file-based driver acts both as an ODBC driver and as a data source. It can therefore generate errors and warnings both as a component in an ODBC connection and as a data source. Because it also is the component that interfaces with the Driver Manager, it formats and returns arguments for <legacyBold>SQLGetDiagRec</legacyBold>.</para>
    <para>For example, if a Microsoft® driver for dBASE could not allocate sufficient memory, it might return the following values from <legacyBold>SQLGetDiagRec</legacyBold>:</para>
    <code>SQLSTATE:         "HY001"
Native Error:      42052
Diagnostic Msg:   "[Microsoft][ODBC dBASE Driver]Unable to allocate sufficient memory."</code>
    <para>Because this error was not related to the data source, the driver only added prefixes to the diagnostic message for the vendor ([Microsoft]) and the driver ([ODBC dBASE Driver]).</para>
    <para>If the driver could not find the file Employee.dbf, it might return the following values from <legacyBold>SQLGetDiagRec</legacyBold>:</para>
    <code>SQLSTATE:         "42S02"
Native Error:      -1305
Diagnostic Msg:   "[Microsoft][ODBC dBASE Driver][dBASE]No such table or object"</code>
    <para>Because this error was related to the data source, the driver added the file format of the data source ([dBASE]) as a prefix to the diagnostic message. Because the driver was also the component that interfaced with the data source, it added prefixes for the vendor ([Microsoft]) and the driver ([ODBC dBASE Driver]).</para>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>