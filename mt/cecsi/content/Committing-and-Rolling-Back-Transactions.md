---
title: Committing and Rolling Back Transactions
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 800f2c1a-6f79-4ed1-830b-aa1a62ff5165
manager:jhubbard
translation.priority.ht: 
  - en-gb
---
# Committing and Rolling Back Transactions
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>To commit or roll back a transaction in manual-commit mode, an application calls <legacyBold>SQLEndTran</legacyBold>. Drivers for DBMSs that support transactions typically implement this function by executing a <legacyBold>COMMIT</legacyBold> or <legacyBold>ROLLBACK</legacyBold> statement. The Driver Manager does not call <legacyBold>SQLEndTran</legacyBold> when the connection is in auto-commit mode; it simply returns SQL_SUCCESS, even if the application attempts to roll back the transaction. Because drivers for DBMSs that do not support transactions are always in auto-commit mode, they can either implement <legacyBold>SQLEndTran</legacyBold> to return SQL_SUCCESS without doing anything or not implement it at all.</para>
    <alert class="note">
      <para>Applications should not commit or roll back transactions by executing <legacyBold>COMMIT</legacyBold> or <legacyBold>ROLLBACK</legacyBold> statements with <legacyBold>SQLExecute</legacyBold> or <legacyBold>SQLExecDirect</legacyBold>. The effects of doing this are undefined. Possible problems include the driver no longer knowing when a transaction is active and these statements failing against data sources that do not support transactions. These applications should call <legacyBold>SQLEndTran</legacyBold> instead.</para>
    </alert>
    <para>If an application passes the environment handle to <legacyBold>SQLEndTran</legacyBold> but does not pass a connection handle, the Driver Manager conceptually calls <legacyBold>SQLEndTran</legacyBold> with the environment handle for each driver that has one or more active connections in the environment. The driver then commits the transactions on each connection in the environment. However, it is important to realize that neither the driver nor the Driver Manager performs a two-phase commit on the connections in the environment; this is merely a programming convenience to simultaneously call <legacyBold>SQLEndTran</legacyBold> for all connections in the environment.</para>
    <para>(A <legacyItalic>two-phase commit</legacyItalic> is generally used to commit transactions that are spread across multiple data sources. In its first phase, the data sources are polled as to whether they can commit their part of the transaction. In the second phase, the transaction is actually committed on all data sources. If any data sources reply in the first phase that they cannot commit the transaction, the second phase does not occur.)</para>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>