---
title: Connecting with SQLDriverConnect
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e46e959f-d3c5-4ddb-810a-107bfcb83fd2
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Connecting with SQLDriverConnect
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>       <legacyBold>SQLDriverConnect</legacyBold> is used to connect to a data source using a connection string. <legacyBold>SQLDriverConnect</legacyBold> is used instead of <legacyBold>SQLConnect</legacyBold> for the following reasons:  </para>
    <list class="bullet">
      <listItem>
        <para>To let the application use driver-specific connection information.</para>
      </listItem>
      <listItem>
        <para>To request that the driver prompt the user for connection information.</para>
      </listItem>
      <listItem>
        <para>To connect without specifying a data source.</para>
      </listItem>
    </list>
    <para>This section contains the following topics.  </para>
    <list class="bullet">
      <listItem>
        <para>             <legacyLink xlink:href="3748758a-f16a-4f3b-9c40-06f2e300704e">Driver-Specific Connection Information</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="da98e9b9-a4ac-4a9d-bae6-e9252b1fe1e5">Prompting the User for Connection Information</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="3003f8c2-8be6-41cc-8d9c-612e9bd0f3ae">Connecting Using File Data Sources</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="f86e198f-a088-4401-9106-aa62a0eb8f6e">Connecting Directly to Drivers</legacyLink>           </para>
      </listItem>
    </list>
  </introduction>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>