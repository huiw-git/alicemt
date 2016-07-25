---
title: "BeginTransComplete, CommitTransComplete, and RollbackTransComplete Events (ADO)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: ec4e4b38-e9c6-4757-b2ef-4e468ae5f1d8
caps.latest.revision: 10
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
# BeginTransComplete, CommitTransComplete, and RollbackTransComplete Events (ADO)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>These events will be called after the associated operation on the <legacyLink xlink:href="ef6b1824-5b12-43db-89d7-8f3d13896d4d">Connection</legacyLink> object finishes executing.  </para>
    <list class="bullet">
      <listItem>
        <para>
          <legacyBold>BeginTransComplete</legacyBold> is called after the <legacyLink xlink:href="d4683472-4120-4236-8640-fa9ae289e23e">BeginTrans</legacyLink> operation.</para>
      </listItem>
      <listItem>
        <para>
          <legacyBold>CommitTransComplete</legacyBold> is called after the <legacyLink xlink:href="d4683472-4120-4236-8640-fa9ae289e23e">CommitTrans</legacyLink> operation.</para>
      </listItem>
      <listItem>
        <para>
          <legacyBold>RollbackTransComplete</legacyBold> is called after the <legacyLink xlink:href="d4683472-4120-4236-8640-fa9ae289e23e">RollbackTrans</legacyLink> operation.</para>
      </listItem>
    </list>
  </introduction>
  <syntaxSection>
    <legacySyntax>
<legacyBold>BeginTransComplete</legacyBold> <parameterReference>TransactionLevel, pError</parameterReference>, <parameterReference>adStatus</parameterReference>, <parameterReference>pConnection</parameterReference>
<legacyBold>CommitTransComplete </legacyBold><parameterReference>pError</parameterReference>, <parameterReference>adStatus</parameterReference>, <parameterReference>pConnection</parameterReference>
<legacyBold>RollbackTransComplete </legacyBold><parameterReference>pError</parameterReference>, <parameterReference>adStatus</parameterReference>, <parameterReference>pConnection</parameterReference></legacySyntax>
  </syntaxSection>
  <parameters>
    <content>
      <definitionTable>
        <definedTerm> <legacyItalic>TransactionLevel</legacyItalic> </definedTerm>
        <definition>
          <para>A <languageKeyword>Long</languageKeyword> value that contains the new transaction level of the <legacyBold>BeginTrans</legacyBold> that caused this event.</para>
        </definition>
        <definedTerm> <legacyItalic>pError</legacyItalic> </definedTerm>
        <definition>
          <para>An <legacyLink xlink:href="a175d453-fa55-4f49-9ede-a26d83177919">Error</legacyLink> object. It describes the error that occurred if the value of EventStatusEnum is <legacyBold>adStatusErrorsOccurred</legacyBold>; otherwise it is not set.</para>
        </definition>
        <definedTerm> <legacyItalic>adStatus</legacyItalic> </definedTerm>
        <definition>
          <para>An <legacyLink xlink:href="ebfd4cda-4017-4873-9d28-38b1c7db12a8">EventStatusEnum</legacyLink> status value. When any of these events is called, this parameter is set to <legacyBold>adStatusOK</legacyBold> if the operation that caused the event was successful, or to <legacyBold>adStatusErrorsOccurred</legacyBold> if the operation failed.</para>
          <para>These events can prevent subsequent notifications by setting this parameter to <legacyBold>adStatusUnwantedEvent</legacyBold> before the event returns. </para>
        </definition>
        <definedTerm> <legacyItalic>pConnection</legacyItalic> </definedTerm>
        <definition>
          <para>The <legacyBold>Connection</legacyBold> object for which this event occurred.</para>
        </definition>
      </definitionTable>
    </content>
  </parameters>
  <languageReferenceRemarks>
    <content>
      <para>In Visual C++, multiple <legacyBold>Connections</legacyBold> can share the same event handling method. The method uses the returned <legacyBold>Connection</legacyBold> object to determine which object caused the event.</para>
      <para>If the <legacyLink xlink:href="acc15d40-68a6-4ba9-85bd-12d331aecaa6">Attributes</legacyLink> property is set to <legacyBold>adXactCommitRetaining</legacyBold> or <legacyBold>adXactAbortRetaining</legacyBold>, a new transaction starts after committing or rolling back a transaction. Use the <legacyBold>BeginTransComplete</legacyBold> event to ignore all but the first transaction start event.</para>
    </content>
  </languageReferenceRemarks>
  <relatedTopics>
<link xlink:href="29530153-b963-4a7c-8665-2335f1d604a8">Visual C++ Example</link>
<link xlink:href="27f502f8-d66a-4b44-9071-a05993d3fabb">Visual J++ Example</link>
<link xlink:href="aa7de324-cd71-4bd0-8043-24229f4a785e">Visual Basic Example</link>
<link xlink:href="b34f4472-5e04-4a2c-ab64-38d6eca31a69">ADO Event Handler Summary</link>
<link xlink:href="d4683472-4120-4236-8640-fa9ae289e23e">BeginTrans, CommitTrans, and RollbackTrans Methods</link>
</relatedTopics>
</developerReferenceWithSyntaxDocument>