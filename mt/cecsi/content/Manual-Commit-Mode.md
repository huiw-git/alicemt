---
title: Manual-Commit Mode
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9c4b3931-e48b-4960-89a2-5697537e9f51
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Manual-Commit Mode
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>       <legacyItalic>In manual-commit mode,</legacyItalic> applications must explicitly complete transactions by calling <legacyBold>SQLEndTran</legacyBold> to commit them or roll them back. This is the normal transaction mode for most relational databases.</para>
    <para>Transactions in ODBC do not have to be explicitly initiated. Instead, a transaction begins implicitly whenever the application starts operating on the database. If the data source requires explicit transaction initiation, the driver must provide it whenever the application executes a statement requiring a transaction and there is no current transaction.</para>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>