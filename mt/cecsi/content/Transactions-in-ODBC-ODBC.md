---
title: "Transactions in ODBC ODBC"
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2c8cde03-4bb8-4b35-881b-1ba23da15fbc
caps.latest.revision: 4
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Transactions in ODBC ODBC
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Transactions in ODBC are completed at the connection level; that is, when an application completes a transaction, it commits or rolls back all work done through all statement handles on that connection.</para>
    <para>This section contains the following topics.  </para>
    <list class="bullet">
      <listItem>
        <para>             <legacyLink xlink:href="d56e1458-8da2-4d73-a777-09e045c30a33">Transaction Support</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="963fe470-f7cb-4dbe-a779-05f98d7ff17d">Commit Mode</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="800f2c1a-6f79-4ed1-830b-aa1a62ff5165">Committing and Rolling Back Transactions</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="523e22a2-7b53-4c25-97c1-ef0284aec76e">Effect of Transactions on Cursors and Prepared Statements</legacyLink>           </para>
      </listItem>
    </list>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>