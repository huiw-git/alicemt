---
title: "BeginTrans, CommitTrans, and RollbackTrans Methods (ADO)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: d4683472-4120-4236-8640-fa9ae289e23e
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
# BeginTrans, CommitTrans, and RollbackTrans Methods (ADO)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>These transaction methods manage transaction processing within a <legacyLink xlink:href="ef6b1824-5b12-43db-89d7-8f3d13896d4d">Connection</legacyLink> object as follows:  </para>
    <list class="bullet">
      <listItem>
        <para>
          <legacyBold>BeginTrans</legacyBold>     Begins a new transaction.</para>
      </listItem>
      <listItem>
        <para>
          <legacyBold>CommitTrans</legacyBold>     Saves any changes and ends the current transaction. It may also start a new transaction.</para>
      </listItem>
      <listItem>
        <para>
          <legacyBold>RollbackTrans</legacyBold>      Cancels any changes made during the current transaction and ends the transaction. It may also start a new transaction.</para>
      </listItem>
    </list>
  </introduction>
  <syntaxSection>
    <legacySyntax>
level = object.BeginTrans()
object.BeginTrans
object.CommitTrans
object.RollbackTrans</legacySyntax>
  </syntaxSection>
  <returnValue>
    <content>
      <para>
        <legacyBold>BeginTrans</legacyBold> can be called as a function that returns a <languageKeyword>Long</languageKeyword> variable indicating the nesting level of the transaction.</para>
    </content>
  </returnValue>
  <parameters>
    <content>
      <definitionTable>
        <definedTerm> <legacyItalic>object</legacyItalic> </definedTerm>
        <definition>
          <para>A <legacyBold>Connection</legacyBold> object.</para>
        </definition>
      </definitionTable>
    </content>
    <sections>
      <section>
        <title>Connection</title>
        <content>
          <para>Use these methods with a <legacyBold>Connection</legacyBold> object when you want to save or cancel a series of changes made to the source data as a single unit. For example, to transfer money between accounts, you subtract an amount from one and add the same amount to the other. If either update fails, the accounts no longer balance. Making these changes within an open transaction ensures that either all or none of the changes go through.</para>
          <alert class="note">
            <para>Not all providers support transactions. Verify that the provider-defined property "<legacyBold>Transaction DDL</legacyBold>" appears in the <legacyBold>Connection</legacyBold> object's <legacyLink xlink:href="1d539aa8-ce0d-4418-ab03-8d0a3c1e9d82">Properties</legacyLink> collection, indicating that the provider supports transactions. If the provider does not support transactions, calling one of these methods will return an error.</para>
          </alert>
          <para>After you call the <legacyBold>BeginTrans</legacyBold> method, the provider will no longer instantaneously commit changes you make until you call <legacyBold>CommitTrans</legacyBold> or <legacyBold>RollbackTrans</legacyBold> to end the transaction.</para>
          <para>For providers that support nested transactions, calling the <legacyBold>BeginTrans</legacyBold> method within an open transaction starts a new, nested transaction. The return value indicates the level of nesting: a return value of "1" indicates you have opened a top-level transaction (that is, the transaction is not nested within another transaction), "2" indicates that you have opened a second-level transaction (a transaction nested within a top-level transaction), and so forth. Calling <legacyBold>CommitTrans</legacyBold> or <legacyBold>RollbackTrans</legacyBold> affects only the most recently opened transaction; you must close or roll back the current transaction before you can resolve any higher-level transactions.</para>
          <para>Calling the <legacyBold>CommitTrans</legacyBold> method saves changes made within an open transaction on the connection and ends the transaction. Calling the <legacyBold>RollbackTrans</legacyBold> method reverses any changes made within an open transaction and ends the transaction. Calling either method when there is no open transaction generates an error.</para>
          <para>Depending on the <legacyBold>Connection</legacyBold> object's <legacyLink xlink:href="acc15d40-68a6-4ba9-85bd-12d331aecaa6">Attributes</legacyLink> property, calling either the <legacyBold>CommitTrans</legacyBold> or <legacyBold>RollbackTrans</legacyBold> methods may automatically start a new transaction. If the <legacyBold>Attributes</legacyBold> property is set to <legacyBold>adXactCommitRetaining</legacyBold>, the provider automatically starts a new transaction after a <legacyBold>CommitTrans</legacyBold> call. If the <legacyBold>Attributes</legacyBold> property is set to <legacyBold>adXactAbortRetaining</legacyBold>, the provider automatically starts a new transaction after a <legacyBold>RollbackTrans</legacyBold> call.</para>
        </content>
      </section>
      <section>
        <title>Remote Data Service</title>
        <content>
          <para>The <legacyBold>BeginTrans</legacyBold>, <legacyBold>CommitTrans</legacyBold>, and <legacyBold>RollbackTrans</legacyBold> methods are not available on a client-side <legacyBold>Connection</legacyBold> object.</para>
        </content>
      </section>
    </sections>
  </parameters>
  <section>
    <title>Applies To</title>
    <content>
      <para>
        <link xlink:href="ef6b1824-5b12-43db-89d7-8f3d13896d4d">Connection</link>
      </para>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="aa7de324-cd71-4bd0-8043-24229f4a785e">Visual Basic Example</link>
<link xlink:href="4ac19647-73e7-4edf-9913-25c8fd927e36">Visual C++ Example</link>
<link xlink:href="27f502f8-d66a-4b44-9071-a05993d3fabb">Visual J++ Example</link>
<link xlink:href="acc15d40-68a6-4ba9-85bd-12d331aecaa6">Attributes Property</link>
</relatedTopics>
</developerReferenceWithSyntaxDocument>