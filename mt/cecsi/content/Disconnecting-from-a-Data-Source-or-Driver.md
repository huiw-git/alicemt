---
title: Disconnecting from a Data Source or Driver
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 83dbf0bf-b400-41fb-8537-9b016050dc3c
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Disconnecting from a Data Source or Driver
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>When an application has finished using a data source, it calls <legacyBold>SQLDisconnect</legacyBold>. <legacyBold>SQLDisconnect</legacyBold> frees any statements that are allocated on the connection and disconnects the driver from the data source. It returns an error if a transaction is in process.</para>
    <para>After disconnecting, the application can call <legacyBold>SQLFreeHandle</legacyBold> to free the connection. After freeing the connection, it is an application programming error to use the connection's handle in a call to an ODBC function; doing so has undefined but probably fatal consequences. When <legacyBold>SQLFreeHandle</legacyBold> is called, the driver releases the structure used to store information about the connection.</para>
    <para>The application also can reuse the connection, either to connect to a different data source or reconnect to the same data source. The decision to remain connected, as opposed to disconnecting and reconnecting later, requires that the application writer consider the relative costs of each option; both connecting to a data source and remaining connected can be relatively costly depending on the connection medium. In making a correct tradeoff, the application must also make assumptions about the likelihood and timing of further operations on the same data source.</para>
  </introduction>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>