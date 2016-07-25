---
title: "Database Access Architecture"
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3811599f-48cb-4205-9fe5-5ab4b240047d
caps.latest.revision: 4
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Database Access Architecture
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>One of the questions in the development of ODBC was which part of the database access architecture to standardize. The SQL programming interfaces described in the previous section — embedded SQL, SQL modules, and CLIs — are only one part of this architecture. In fact, because ODBC was primarily intended to connect personal computer–based applications to minicomputer and mainframe DBMSs, there were also a number of network components, some of which could be standardized.</para>
    <para>This section contains the following topics.  </para>
    <list class="bullet">
      <listItem>
        <para>             <legacyLink xlink:href="f31dd938-e992-436b-b613-145c23973064">Network Database Access</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="a9d41800-9068-4b76-895a-32b2853692dd">Standard Database Access Architectures</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="34b80790-e010-4b90-8eaa-03189f5d8986">The ODBC Solution</legacyLink>           </para>
      </listItem>
    </list>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>