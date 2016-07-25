---
title: "Transaction Processing"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 74ab6706-e2dc-42cb-af77-dbc58a9cf4ce
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
# Transaction Processing
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>A <legacyItalic>transaction </legacyItalic>delimits the beginning and end of a series of data access operations executed across a connection. Subject to the transactional capabilities of your data source, the <legacyBold>Connection</legacyBold> object also allows you to create and manage transactions. For example, using the Microsoft OLE DB Provider for SQL Server to access a database on Microsoft SQL Server, you can create multiple nested transactions for the commands you execute.</para>
    <para>ADO ensures that changes to a data source resulting from operations in a transaction occur successfully together or not at all.</para>
    <para>If you cancel the transaction, or if one of its operations fails, the result will be as if none of the operations in the transaction occurred. The data source will remain as it was before the transaction began.</para>
    <para>ADO provides the following methods for controlling transactions: <legacyBold>BeginTrans</legacyBold>, <legacyBold>CommitTrans</legacyBold>, and <legacyBold>RollbackTrans</legacyBold>. Use these methods with a <legacyBold>Connection</legacyBold> object when you want to save or cancel a series of changes made to the source data as a single unit. For example, to transfer money between accounts, you subtract an amount from one and add the same amount to the other. If either update fails, the accounts no longer balance. Making these changes within an open transaction ensures that either all or none of the changes go through.</para>
    <alert class="note">
      <para>Not all providers support transactions. Verify that the provider-defined property "<legacyBold>Transaction DDL</legacyBold>" appears in the <legacyBold>Connection</legacyBold> object's <legacyLink xlink:href="1d539aa8-ce0d-4418-ab03-8d0a3c1e9d82">Properties</legacyLink> collection, indicating that the provider supports transactions. If the provider does not support transactions, calling one of these methods will return an error.</para>
    </alert>
    <para>After you call the <legacyBold>BeginTrans</legacyBold> method, the provider will no longer instantaneously commit changes you make until you call <legacyBold>CommitTrans</legacyBold> or <legacyBold>RollbackTrans</legacyBold> to end the transaction.</para>
    <para>Calling the <legacyBold>CommitTrans</legacyBold> method saves changes made within an open transaction on the connection and ends the transaction. Calling the <legacyBold>RollbackTrans</legacyBold> method reverses any changes made within an open transaction and ends the transaction. Calling either method when there is no open transaction generates an error.</para>
    <para>Depending on the <legacyBold>Connection</legacyBold> object's <legacyLink xlink:href="acc15d40-68a6-4ba9-85bd-12d331aecaa6">Attributes</legacyLink> property, calling either the <legacyBold>CommitTrans</legacyBold> or <legacyBold>RollbackTrans</legacyBold> method may automatically start a new transaction. If the <legacyBold>Attributes</legacyBold> property is set to <legacyBold>adXactCommitRetaining</legacyBold>, the provider automatically starts a new transaction after a <legacyBold>CommitTrans</legacyBold> call. If the <legacyBold>Attributes</legacyBold> property is set to <legacyBold>adXactAbortRetaining</legacyBold>, the provider automatically starts a new transaction after a <legacyBold>RollbackTrans</legacyBold> call.</para>
  </introduction>
  <section>
    <title>Transaction Isolation Level</title>
    <content>
      <para>Use the <legacyBold>IsolationLevel</legacyBold> property to set the isolation level of a transaction on a <legacyBold>Connection</legacyBold> object. The setting does not take effect until the next time you call the <legacyLink xlink:href="d4683472-4120-4236-8640-fa9ae289e23e">BeginTrans</legacyLink> method. If the level of isolation you request is unavailable, the provider may return the next greater level of isolation. Refer to the <legacyBold>IsolationLevel</legacyBold> property in the ADO Programmer's Reference for more details on valid values.</para>
    </content>
  </section>
  <section>
    <title>Nested Transactions</title>
    <content>
      <para>For providers that support nested transactions, calling the <legacyBold>BeginTrans</legacyBold> method within an open transaction starts a new, nested transaction. The return value indicates the level of nesting: a return value of "1" indicates you have opened a top-level transaction (that is, the transaction is not nested within another transaction), "2" indicates that you have opened a second-level transaction (a transaction nested within a top-level transaction), and so forth. Calling <legacyBold>CommitTrans</legacyBold> or <legacyBold>RollbackTrans</legacyBold> affects only the most recently opened transaction; you must close or roll back the current transaction before you can resolve any higher-level transactions.</para>
    </content>
  </section>
  <relatedTopics />
</developerConceptualDocument>