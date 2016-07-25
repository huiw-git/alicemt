---
title: "Connecting to Data Sources"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 82770486-37bd-4c90-885f-6817a7c77ad7
caps.latest.revision: 11
manager: sonalm
translation.priority.ht: 
  - de-de
  - es-es
  - fr-fr
  - it-it
  - ja-jp
  - ko-kr
  - pt-br
  - ru-ru
  - zh-cn
  - zh-tw
---
# Connecting to Data Sources
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>An ADO <legacyBold>Connection</legacyBold> object represents a unique session with a data source, including a DBMS, a file store, or a comma-delimited text file. In the case of a client/server database system, the ADO connection can be an actual network connection to the server.</para>
    <para>The <legacyBold>Connection</legacyBold> object supports various <legacyLink xlink:href="f571b74d-b796-4009-9c66-6a36ab995a2a">properties and methods</legacyLink> for specifying connection configurations, opening and closing connections, creating and executing commands against the data source, and providing information about the design of the underlying data source in the form of schema rowsets, etc. Depending on the functionality supported by the provider, some collections, methods, or properties of a <legacyBold>Connection</legacyBold> object might not be available.</para>
    <para>You can connect to a data source either by using a <legacyBold>Connection</legacyBold> object or by using a <legacyBold>Recordset</legacyBold> object.</para>
    <para>This section contains the following topics.  </para>
    <list class="bullet">
      <listItem>
        <para>             <legacyLink xlink:href="4b34f971-5699-43e7-9b15-137d334fa66e">Using a Connection Object</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="01c630d8-eb35-4bd0-a99f-7c0f85316cc1">Using a Recordset Object</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="14eae122-2d1e-40c8-b88e-b7cb8dfbc93b">Creating a Connection String</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="49456201-b085-4851-9686-e814136b07be">Specifying Connection Properties</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="189240e8-3ffa-4024-81a9-c6cb5d17eee0">Controlling Transactions</legacyLink>           </para>
      </listItem>
    </list>
  </introduction>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>