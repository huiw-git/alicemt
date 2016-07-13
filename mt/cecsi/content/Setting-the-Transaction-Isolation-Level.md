---
title: Setting the Transaction Isolation Level
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 64a037f0-5065-4f45-9669-6710404a540c
manager:jhubbard
translation.priority.ht: 
  - en-gb
---
# Setting the Transaction Isolation Level
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>To set the transaction isolation level, an application uses the SQL_ATTR_TXN_ISOLATION connection attribute. If the data source does not support the requested isolation level, the driver or data source can set a higher level. To determine what transaction isolation levels a data source supports and what the default isolation level is, an application calls <legacyBold>SQLGetInfo</legacyBold> with the SQL_TXN_ISOLATION_OPTION and SQL_DEFAULT_TXN_ISOLATION options, respectively.</para>
    <para>Higher levels of transaction isolation offer the most protection for the integrity of database data. Serializable transactions are guaranteed to be unaffected by other transactions and therefore guaranteed to maintain database integrity.</para>
    <para>However, a higher level of transaction isolation can cause slower performance because it increases the chances that the application will have to wait for locks on data to be released. An application can specify a lower level of isolation to increase performance in the following cases:  </para>
    <list class="bullet">
      <listItem>
        <para>When it can be guaranteed that no other transactions exist that might interfere with an application's transactions. This situation occurs only in limited circumstances, such as when one person in a small company maintains dBASE files that contain personnel data on one computer and does not share these files.</para>
      </listItem>
      <listItem>
        <para>When speed is more critical than accuracy and any errors are likely to be small. For example, suppose that a company makes many small sales and that large sales are rare. A transaction that estimates the total value of all open sales might safely use the Read Uncommitted isolation level. Although the transaction would include orders that are being opened or closed and are subsequently rolled back, these would generally cancel each other out and the transaction would be much faster because it is not blocked every time that it encounters such an order.</para>
      </listItem>
    </list>
    <para>For more information, see <legacyLink xlink:href="9d71e09e-bc68-4c1f-9229-ed2a7be7d324">Optimistic Concurrency</legacyLink>.</para>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>