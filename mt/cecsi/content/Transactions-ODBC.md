---
title: Transactions ODBC
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b4ca861a-c164-4e87-8672-d5de15e3823c
translation.priority.ht: 
  - en-gb
---
# Transactions ODBC
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>A <legacyItalic>transaction</legacyItalic> is a unit of work that is done as a single,atomic operation; that is, the operation succeeds or fails as a whole. For example, consider transferring money from one bank account to another. This involves two steps: withdrawing the money from the first account and depositing it in the second. It is important that both steps succeed; it is not acceptable for one step to succeed and the other to fail. A database that supports transactions is able to guarantee this.</para>
    <para>Transactions can be completed by either being <legacyItalic>committed</legacyItalic> or being <legacyItalic>rolled back</legacyItalic>. When a transaction is committed, the changes made in that transaction are made permanent. When a transaction is rolled back, the affected rows are returned to the state they were in before the transaction was started. To extend the account transfer example, an application executes one SQL statement to debit the first account and a different SQL statement to credit the second account. If both statements succeed, the application then commits the transaction. But if either statement fails for any reason, the application rolls back the transaction. In either case, the application guarantees a consistent state at the end of the transaction.</para>
    <para>A single transaction can encompass multiple database operations that occur at different times. If other transactions had complete access to the intermediate results, the transactions might interfere with one another. For example, suppose one transaction inserts a row, a second transaction reads that row, and the first transaction is rolled back. The second transaction now has data for a row that does not exist.</para>
    <para>To solve this problem, there are various schemes to isolate transactions from one another. <legacyItalic>Transaction isolation</legacyItalic> is generally implemented by locking rows, which precludes more than one transaction from using the same row at the same time. In some databases, locking a row may also lock other rows.</para>
    <para>With increased transaction isolation comes reduced <legacyItalic>concurrency,</legacyItalic> or the ability of two transactions to use the same data at the same time. For more information, see <legacyLink xlink:href="64a037f0-5065-4f45-9669-6710404a540c">Setting the Transaction Isolation Level</legacyLink>.</para>
    <para>This section contains the following topics.  </para>
    <list class="bullet">
      <listItem>
        <para>             <legacyLink xlink:href="2c8cde03-4bb8-4b35-881b-1ba23da15fbc">Transactions in ODBC</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="351bfe5c-3b26-4010-9b9c-22e796135f3b">Transaction Isolation</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="75e4adb3-3d43-49c5-8c5e-8df96310d912">Concurrency Control</legacyLink>           </para>
      </listItem>
    </list>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>