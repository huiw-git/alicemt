---
title: "Gateways Diagnostic Example"
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e0695fac-4593-4b3d-8675-cb8f73dab966
caps.latest.revision: 4
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Gateways Diagnostic Example
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>In a gateway architecture, a driver sends requests to a gateway that supports ODBC. The gateway sends the requests to a DBMS. Because it is the component that interfaces with the Driver Manager, the driver formats and returns arguments for <legacyBold>SQLGetDiagRec</legacyBold>.</para>
    <para>For example, if Oracle based a gateway to Rdb on Microsoft Open Data Services and if Rdb could not find the table EMPLOYEE, the gateway might generate this diagnostic message:</para>
    <code>"[42S02][-1][DEC][ODS Gateway][Rdb]%SQL-F-RELNOTDEF, Table EMPLOYEE is not defined "
   "in schema."</code>
    <para>Because the error occurred in the data source, the gateway added a prefix for the data source identifier ([Rdb]) to the diagnostic message. Because the gateway was the component that interfaced with the data source, it added prefixes for its vendor ([DEC]) and identifier ([ODS Gateway]) to the diagnostic message. It also added the SQLSTATE value and the Rdb error code to the beginning of the diagnostic message. This permitted it to preserve the semantics of its own message structure and still supply the ODBC diagnostic information to the driver. The driver parses the error information attached to the error statement by the gateway.</para>
    <para>Because the gateway driver is the component that interfaces with the Driver Manager, it would use the preceding diagnostic message to format and return the following values from <legacyBold>SQLGetDiagRec</legacyBold>:</para>
    <code>SQLSTATE:         "42S02"
Native Error:      -1
Diagnostic Msg:   "[DEC][ODS Gateway][Rdb]%SQL-F-RELNOTDEF, Table EMPLOYEE is not "
                  "defined in schema."</code>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>