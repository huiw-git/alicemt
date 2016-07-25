---
title: "WillConnect Event (ADO)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: da561d58-eb58-446c-a4fd-1838c76073c0
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
# WillConnect Event (ADO)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The <legacyBold>WillConnect</legacyBold> event is called before a connection starts. </para>
    <para>
      <embeddedLabel>Applies To:</embeddedLabel> <link xlink:href="ef6b1824-5b12-43db-89d7-8f3d13896d4d">Connection Object</link></para>
  </introduction>
  <syntaxSection>
    <legacySyntax>
<legacyBold>WillConnect</legacyBold> <parameterReference>ConnectionString, UserID, Password, Options, adStatus, pConnection</parameterReference></legacySyntax>
  </syntaxSection>
  <parameters>
    <content>
      <definitionTable>
        <definedTerm> <legacyItalic>ConnectionString</legacyItalic> </definedTerm>
        <definition>
          <para>A <languageKeyword>String</languageKeyword> that contains connection information for the pending connection.</para>
        </definition>
        <definedTerm> <legacyItalic>UserID</legacyItalic> </definedTerm>
        <definition>
          <para>A <languageKeyword>String</languageKeyword> that contains a user name for the pending connection.</para>
        </definition>
        <definedTerm> <legacyItalic>Password</legacyItalic> </definedTerm>
        <definition>
          <para>A <languageKeyword>String</languageKeyword> that contains a password for the pending connection.</para>
        </definition>
        <definedTerm> <legacyItalic>Options</legacyItalic> </definedTerm>
        <definition>
          <para>A <languageKeyword>Long</languageKeyword> value that indicates how the provider should evaluate the <legacyItalic>ConnectionString</legacyItalic>. Your only option is <legacyBold>adAsyncOpen</legacyBold>.</para>
        </definition>
        <definedTerm> <legacyItalic>adStatus</legacyItalic> </definedTerm>
        <definition>
          <para>An <legacyLink xlink:href="ebfd4cda-4017-4873-9d28-38b1c7db12a8">EventStatusEnum</legacyLink> status value.</para>
          <para>When this event is called, this parameter is set to <legacyBold>adStatusOK</legacyBold> by default. It is set to <legacyBold>adStatusCantDeny</legacyBold> if the event cannot request cancellation of the pending operation.   </para>
          <para>Before this event returns, set this parameter to <legacyBold>adStatusUnwantedEvent</legacyBold> to prevent subsequent notifications. Set this parameter to <legacyBold>adStatusCancel</legacyBold> to request the connection operation that caused cancellation of this notification. </para>
        </definition>
        <definedTerm> <legacyItalic>pConnection</legacyItalic> </definedTerm>
        <definition>
          <para>The <legacyLink xlink:href="ef6b1824-5b12-43db-89d7-8f3d13896d4d">Connection</legacyLink> object for which this event notification applies. Changes to the parameters of the <legacyBold>Connection</legacyBold> by the <legacyBold>WillConnect</legacyBold> event handler will have no effect on the <legacyBold>Connection</legacyBold>.</para>
        </definition>
      </definitionTable>
    </content>
  </parameters>
  <languageReferenceRemarks>
    <content>
      <para>When <legacyBold>WillConnect</legacyBold> is called, the <legacyItalic>ConnectionString</legacyItalic>, <legacyItalic>UserID</legacyItalic>, <legacyItalic>Password</legacyItalic>, and <legacyItalic>Options</legacyItalic> parameters are set to the values established by the operation that caused this event (the pending connection), and can be changed before the event returns. <legacyBold>WillConnect</legacyBold> may return a request that the pending connection be canceled.</para>
      <para>When this event is canceled, <legacyBold>ConnectComplete</legacyBold> will be called with its <legacyItalic>adStatus </legacyItalic>parameter set to <legacyBold>adStatusErrorsOccurred</legacyBold>.</para>
    </content>
  </languageReferenceRemarks>
  <relatedTopics>
<link xlink:href="29530153-b963-4a7c-8665-2335f1d604a8">Visual C++ Example</link>
<link xlink:href="b34f4472-5e04-4a2c-ab64-38d6eca31a69">ADO Event Handler Summary</link>
</relatedTopics>
</developerReferenceWithSyntaxDocument>