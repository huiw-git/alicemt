---
title: Serializability
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 142e4ac0-2977-4a2b-96ae-c9e5bd2c448a
translation.priority.ht: 
  - en-gb
---
# Serializability
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Ideally, transactions should be <legacyItalic>serializable</legacyItalic>. Transactions are said to be serializable if the results of running transactions simultaneously are the same as the results of running them serially — that is, one after the other. It is not important which transaction executes first, only that the result does not reflect any mixing of the transactions.</para>
    <para>For example, suppose transaction A multiplies data values by 2 and transaction B adds 1 to data values. Now suppose that there are two data values: 0 and 10. If these transactions are run one after the other, the new values will be 1 and 21 if transaction A is run first, or 2 and 22 if transaction B is run first. But what if the order in which the two transactions are run is different for each value? If transaction A is run first on the first value and transaction B is run first on the second value, the new values are 1 and 22. If this order is reversed, the new values are 2 and 21. The transactions are serializable if 1, 21 and 2, 22 are the only possible results. The transactions are not serializable if 1, 22 or 2, 21 is a possible result.</para>
    <para>So why is serializability desirable? In other words, why is it important that it appears that one transaction finishes before the next transaction starts? Consider the following problem. A salesman is entering orders at the same time a clerk is sending out bills. Suppose the salesman enters an order from Company X but does not commit it; the salesman is still talking to the representative from Company X. The clerk requests a list of all open orders and discovers the order for Company X and sends them a bill. Now the representative from Company X decides they want to change their order, so the salesman changes it before committing the transaction. Company X gets an incorrect bill.</para>
    <para>If the salesman's and clerk's transactions were serializable, this problem would never have occurred. Either the salesman's transaction would have finished before the clerk's transaction started, in which case the clerk would have sent out the correct bill, or the clerk's transaction would have finished before the salesman's transaction started, in which case the clerk would not have sent a bill to Company X at all.</para>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>