---
title: Connection Handles
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 12222653-f04d-46d6-bdee-61348f5d550f
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Connection Handles
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>A <legacyItalic>connection</legacyItalic> consists of a driver and a data source. A connection handle identifies each connection. The connection handle defines not only which driver to use but which data source to use with that driver. Within a segment of code that implements ODBC (the Driver Manager or a driver), the connection handle identifies a structure that contains connection information, such as the following:  </para>
    <list class="bullet">
      <listItem>
        <para>The state of the connection</para>
      </listItem>
      <listItem>
        <para>The current connection-level diagnostics</para>
      </listItem>
      <listItem>
        <para>The handles of statements and descriptors currently allocated on the connection</para>
      </listItem>
      <listItem>
        <para>The current settings of each connection attribute</para>
      </listItem>
    </list>
    <para>ODBC does not prevent multiple simultaneous connections, if the driver supports them. Therefore, in a particular ODBC environment, multiple connection handles might point to a variety of drivers and data sources, to the same driver and a variety of data sources, or even to multiple connections to the same driver and data source. Some drivers limit the number of active connections they support; the SQL_MAX_DRIVER_CONNECTIONS option in <legacyBold>SQLGetInfo</legacyBold> specifies how many active connections a particular driver supports.</para>
    <para>Connection handles are primarily used when connecting to the data source (<legacyBold>SQLConnect</legacyBold>, <legacyBold>SQLDriverConnect</legacyBold>, or <legacyBold>SQLBrowseConnect</legacyBold>), disconnecting from the data source (<legacyBold>SQLDisconnect</legacyBold>), getting information about the driver and data source (<legacyBold>SQLGetInfo</legacyBold>), retrieving diagnostics (<legacyBold>SQLGetDiagField</legacyBold> and <legacyBold>SQLGetDiagRec</legacyBold>), and performing transactions (<legacyBold>SQLEndTran</legacyBold>). They are also used when setting and getting connection attributes (<legacyBold>SQLSetConnectAttr</legacyBold> and <legacyBold>SQLGetConnectAttr</legacyBold>) and when getting the native format of an SQL statement (<legacyBold>SQLNativeSql</legacyBold>).</para>
    <para>Connection handles are allocated with <legacyBold>SQLAllocHandle</legacyBold> and freed with <legacyBold>SQLFreeHandle</legacyBold>.</para>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>