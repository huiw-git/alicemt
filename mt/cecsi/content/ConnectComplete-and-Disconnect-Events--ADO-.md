---
title: "ConnectComplete and Disconnect Events (ADO)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: 568f5252-d069-4d99-a01b-2ada87ad1304
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
# ConnectComplete and Disconnect Events (ADO)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The <legacyBold>ConnectComplete</legacyBold> event is called after a connection starts. The <legacyBold>Disconnect</legacyBold> event is called after a connection ends.</para>
  </introduction>
  <syntaxSection>
    <legacySyntax>
<legacyBold>ConnectComplete</legacyBold> <parameterReference>pError, adStatus, pConnection</parameterReference>
<legacyBold>Disconnect </legacyBold><parameterReference>adStatus, pConnection</parameterReference></legacySyntax>
  </syntaxSection>
  <parameters>
    <content>
      <definitionTable>
        <definedTerm> <legacyItalic>pError</legacyItalic> </definedTerm>
        <definition>
          <para>An <legacyLink xlink:href="a175d453-fa55-4f49-9ede-a26d83177919">Error</legacyLink> object. It describes the error that occurred if the value of <legacyItalic>adStatus </legacyItalic>is <legacyBold>adStatusErrorsOccurred</legacyBold>; otherwise it is not set.</para>
        </definition>
        <definedTerm> <legacyItalic>adStatus</legacyItalic> </definedTerm>
        <definition>
          <para>An <legacyLink xlink:href="ebfd4cda-4017-4873-9d28-38b1c7db12a8">EventStatusEnum</legacyLink> value that always returns <legacyBold>adStatusOK</legacyBold>.</para>
          <para>When <legacyBold>ConnectComplete</legacyBold> is called, this parameter is set to <legacyBold>adStatusCancel</legacyBold> if a <legacyBold>WillConnect</legacyBold> event has requested cancellation of the pending connection.   </para>
          <para>Before either event returns, set this parameter to <legacyBold>adStatusUnwantedEvent</legacyBold> to prevent subsequent notifications. However, closing and reopening the <legacyLink xlink:href="ef6b1824-5b12-43db-89d7-8f3d13896d4d">Connection</legacyLink> causes these events to occur again. </para>
        </definition>
        <definedTerm> <legacyItalic>pConnection</legacyItalic> </definedTerm>
        <definition>
          <para>The <legacyBold>Connection</legacyBold> object for which this event applies.</para>
        </definition>
      </definitionTable>
    </content>
  </parameters>
  <relatedTopics>
<link xlink:href="29530153-b963-4a7c-8665-2335f1d604a8">Visual C++ Example</link>
<link xlink:href="b34f4472-5e04-4a2c-ab64-38d6eca31a69">ADO Event Handler Summary</link>
</relatedTopics>
</developerReferenceWithSyntaxDocument>