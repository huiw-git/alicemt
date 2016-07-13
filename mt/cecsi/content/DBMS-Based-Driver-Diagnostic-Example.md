---
title: DBMS-Based Driver Diagnostic Example
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a80d54b0-43ff-4dfd-b6cb-f4694a5ed765
manager:jhubbard
translation.priority.ht: 
  - en-gb
---
# DBMS-Based Driver Diagnostic Example
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>A DBMS-based driver sends requests to a DBMS and returns information to the application through the Driver Manager. Because the driver is the component that interfaces with the Driver Manager, it formats and returns arguments for <legacyBold>SQLGetDiagRec</legacyBold>.</para>
    <para>For example, if, using SQL/Services, a Microsoft driver for Oracle Rdb encountered an invalid cursor name, it might return the following values from <legacyBold>SQLGetDiagRec</legacyBold>:</para>
    <code>SQLSTATE:         "34000"
Native Error:      0
Diagnostic Msg:   "[Microsoft][ODBC Rdb Driver]Invalid cursor name: EMPLOYEE_CURSOR."</code>
    <para>Because the error occurred in the driver, it added prefixes to the diagnostic message for the vendor ([Microsoft]) and the driver ([ODBC Rdb Driver]).</para>
    <para>If the DBMS could not find the table EMPLOYEE, the driver might format and return the following values from <legacyBold>SQLGetDiagRec</legacyBold>:</para>
    <code>SQLSTATE:         "42S02"
Native Error:      -1
Diagnostic Msg:   "[Microsoft][ODBC Rdb Driver][Rdb] %SQL-F-RELNOTDEF, Table EMPLOYEE "
                  "is not defined in schema."</code>
    <para>Because the error occurred in the data source, the driver added a prefix for the data source identifier ([Rdb]) to the diagnostic message. Because the driver was the component that interfaced with the data source, it added prefixes for its vendor ([Microsoft]) and identifier ([ODBC Rdb Driver]) to the diagnostic message.</para>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>