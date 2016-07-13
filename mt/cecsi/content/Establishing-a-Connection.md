---
title: Establishing a Connection
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 8e3c717e-35e3-47ef-b5d3-3a96eeb7b869
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Establishing a Connection
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>After allocating environment and connection handles and setting any connection attributes, the application is ready to connect to the data source or driver. There are three different functions the application can use to do this: <legacyBold>SQLConnect</legacyBold> (Core interface conformance level), <legacyBold>SQLDriverConnect</legacyBold> (Core), and <legacyBold>SQLBrowseConnect</legacyBold> (Level 1). Each of the three is designed to be used in a different scenario. Before connecting, the application can determine which of these functions is supported with the <legacyBold>ConnectFunctions</legacyBold> keyword returned by <legacyBold>SQLDrivers</legacyBold>.</para>
    <alert class="note">
      <para>Some drivers limit the number of active connections they support. An application calls <legacyBold>SQLGetInfo</legacyBold> with the SQL_MAX_DRIVER_CONNECTIONS option to determine how many active connections a particular driver supports.</para>
    </alert>
    <para>This section contains the following topics.  </para>
    <list class="bullet">
      <listItem>
        <para>             <legacyLink xlink:href="dd473cc6-f051-4aa0-ab14-3dd1b37fe99e">Default Data Source</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="b16319d2-2c2c-4341-abb5-caa9e17362b4">Connecting with SQLConnect</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="724c7b86-300a-4fa9-ad96-4afa0fdcb3e9">Connection Strings</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="e46e959f-d3c5-4ddb-810a-107bfcb83fd2">Connecting with SQLDriverConnect</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="6c2e9f76-b766-48df-b109-246bb05ae45d">Connecting with SQLBrowseConnect</legacyLink>           </para>
      </listItem>
    </list>
  </introduction>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>