---
title: "Environment, Connection, and Statement Attributes"
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9e15b276-3b7a-428a-b72f-a3ddfe1ba1ce
caps.latest.revision: 5
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Environment, Connection, and Statement Attributes
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>ODBC defines a number of attributes that are associated with environments, connections, or statements.</para>
    <para>Environment attributes affect the entire environment, such as whether connection pooling is enabled. Environment attributes are set with <legacyBold>SQLSetEnvAttr</legacyBold> and retrieved with <legacyBold>SQLGetEnvAttr</legacyBold>.</para>
    <para>Connection attributes affect each connection individually, such as how long a driver should wait while attempting to connect to a data source before timing out. Connection attributes are set with <legacyBold>SQLSetConnectAttr</legacyBold> and retrieved with <legacyBold>SQLGetConnectAttr</legacyBold>. For more information about connection attributes, see <legacyLink xlink:href="e6d03089-30a3-4627-a642-591ba0980894">Connection Attributes</legacyLink>.</para>
    <para>Statement attributes affect each statement individually, such as whether a statement should be executed asynchronously. Statement attributes are set with <legacyBold>SQLSetStmtAttr</legacyBold> and retrieved with <legacyBold>SQLGetStmtAttr</legacyBold>. A few statement attributes are read-only attributes and cannot be set. For example, the SQL_ATTR_ROW_NUMBER statement attribute, which is used to retrieve the number of the current row in the cursor, is read-only. For more information about statement attributes, see <legacyLink xlink:href="4c59cd8e-a713-4095-9065-20d5bdeafe43">Statement Attributes</legacyLink>.</para>
    <para>In addition to attributes defined by ODBC, a driver can define its own connection and statement attributes. Driver-defined attributes must be registered with Open Group to ensure that two driver vendors do not assign the same integer value to different, proprietary attributes. For more information, see <legacyLink xlink:href="ad4c76d3-5191-4262-b47c-5dd1d19d1154">Driver-Specific Data Types, Descriptor Types, Information Types, Diagnostic Types, and Attributes</legacyLink>.</para>
    <para>For a complete list of attributes, see <legacyLink xlink:href="0343241c-4b15-4d4b-aa2b-2e8ab5215cd2">SQLSetEnvAttr</legacyLink>, <legacyLink xlink:href="97fc7445-5a66-4eb9-8e77-10990b5fd685">SQLSetConnectAttr</legacyLink>, and <legacyLink xlink:href="7abc5260-733a-48d4-9974-2d1a6a9ea5f6">SQLSetStmtAttr</legacyLink>. Most attributes are also described in the description of the ODBC function that they affect.</para>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>