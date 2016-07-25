---
title: "WillMove and MoveComplete Events (ADO)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: 1a3d1042-4f30-4526-a0c7-853c242496db
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
# WillMove and MoveComplete Events (ADO)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The <unmanagedCodeEntityReference>WillMove</unmanagedCodeEntityReference> event is called before a pending operation changes the current position in the <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink>. The <unmanagedCodeEntityReference>MoveComplete</unmanagedCodeEntityReference> event is called after the current position in the <unmanagedCodeEntityReference>Recordset</unmanagedCodeEntityReference> changes.</para>
  </introduction>
  <syntaxSection>
    <legacySyntax>
<legacyBold>WillMove</legacyBold> <parameterReference>adReason, adStatus, pRecordset</parameterReference>
<legacyBold>MoveComplete</legacyBold> <parameterReference>adReason, pError, adStatus, pRecordset</parameterReference></legacySyntax>
  </syntaxSection>
  <parameters>
    <content>
      <definitionTable>
        <definedTerm> <legacyItalic>adReason</legacyItalic> </definedTerm>
        <definition>
          <para>An <legacyLink xlink:href="7d4a5496-ec2d-4936-b36a-7049a82be4b4">EventReasonEnum</legacyLink> value that specifies the reason for this event. Its value can be <legacyBold>adRsnMoveFirst</legacyBold>, <legacyBold>adRsnMoveLast</legacyBold>, <legacyBold>adRsnMoveNext</legacyBold>, <legacyBold>adRsnMovePrevious</legacyBold>, <legacyBold>adRsnMove</legacyBold>, or <legacyBold>adRsnRequery</legacyBold>.</para>
        </definition>
        <definedTerm> <legacyItalic>pError</legacyItalic> </definedTerm>
        <definition>
          <para>An <legacyLink xlink:href="a175d453-fa55-4f49-9ede-a26d83177919">Error</legacyLink> object. It describes the error that occurred if the value of <legacyItalic>adStatus</legacyItalic> is <legacyBold>adStatusErrorsOccurred</legacyBold>; otherwise the parameter is not set.</para>
        </definition>
        <definedTerm> <legacyItalic>adStatus</legacyItalic> </definedTerm>
        <definition>
          <para>An <legacyLink xlink:href="ebfd4cda-4017-4873-9d28-38b1c7db12a8">EventStatusEnum</legacyLink> status value. </para>
          <para>When <unmanagedCodeEntityReference>WillMove</unmanagedCodeEntityReference> is called, this parameter is set to <legacyBold>adStatusOK </legacyBold>if the operation that caused the event was successful. It is set to <legacyBold>adStatusCantDeny</legacyBold> if this event cannot request cancellation of the pending operation. </para>
          <para>When <unmanagedCodeEntityReference>MoveComplete</unmanagedCodeEntityReference> is called, this parameter is set to <legacyBold>adStatusOK</legacyBold> if the operation that caused the event was successful, or to <legacyBold>adStatusErrorsOccurred</legacyBold> if the operation failed.   </para>
          <para>Before <unmanagedCodeEntityReference>WillMove</unmanagedCodeEntityReference> returns, set this parameter to <legacyBold>adStatusCancel</legacyBold> to request cancellation of the pending operation, or set this parameter to <legacyBold>adStatusUnwantedEvent</legacyBold> to prevent subsequent notifications. </para>
          <para>Before <unmanagedCodeEntityReference>MoveComplete</unmanagedCodeEntityReference> returns, set this parameter to <legacyBold>adStatusUnwantedEvent</legacyBold> to prevent subsequent notifications. </para>
        </definition>
        <definedTerm> <legacyItalic>pRecordset</legacyItalic> </definedTerm>
        <definition>
          <para>A <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink> object. The <unmanagedCodeEntityReference>Recordset</unmanagedCodeEntityReference> for which this event occurred.</para>
        </definition>
      </definitionTable>
    </content>
  </parameters>
  <languageReferenceRemarks>
    <content>
      <para>A <unmanagedCodeEntityReference>WillMove</unmanagedCodeEntityReference> or <unmanagedCodeEntityReference>MoveComplete</unmanagedCodeEntityReference> event may occur due to the following <unmanagedCodeEntityReference>Recordset</unmanagedCodeEntityReference> operations: <legacyLink xlink:href="3236749c-4b71-4235-89e2-ccdfaaa9319d">Open</legacyLink>, <legacyLink xlink:href="13fe9381-d00b-4f4a-9162-83c3f21b3837">Move</legacyLink>, <legacyLink xlink:href="a61a01a7-5b33-4150-9126-21dfa63654cb">MoveFirst</legacyLink>, <legacyLink xlink:href="a61a01a7-5b33-4150-9126-21dfa63654cb">MoveLast</legacyLink>, <legacyLink xlink:href="a61a01a7-5b33-4150-9126-21dfa63654cb">MoveNext</legacyLink>, <legacyLink xlink:href="a61a01a7-5b33-4150-9126-21dfa63654cb">MovePrevious</legacyLink>, <legacyLink xlink:href="a9f54be9-5763-45d0-a6eb-09981b03bc08">AddNew</legacyLink>, and <legacyLink xlink:href="d81ab76f-1aa8-4ccf-92ec-b65254dc3ea1">Requery</legacyLink>. These events may occur because of the following properties: <legacyLink xlink:href="80263a7a-5d21-45d1-84fc-34b7a9be4c22">Filter</legacyLink>, <legacyLink xlink:href="1c79e271-21ec-41a8-8163-c5e89f0001a7">Index</legacyLink>, <legacyLink xlink:href="481dcc93-487b-490e-ac58-a1e9b2ebfd43">Bookmark</legacyLink>, <legacyLink xlink:href="ddb58a35-ec3a-423c-a504-3c65e62c23d4">AbsolutePage</legacyLink>, and <legacyLink xlink:href="79f8ee5e-fc70-46d8-8c29-ebf943c66592">AbsolutePosition</legacyLink>. These events also occur if a child <unmanagedCodeEntityReference>Recordset</unmanagedCodeEntityReference> has <unmanagedCodeEntityReference>Recordset</unmanagedCodeEntityReference> events connected and the parent <unmanagedCodeEntityReference>Recordset</unmanagedCodeEntityReference> is moved.</para>
      <para>You must set the <parameterReference>adStatus</parameterReference> parameter to <legacyBold>adStatusUnwantedEvent</legacyBold> for each possible <parameterReference>adReason</parameterReference> value in order to completely stop event notification for any event that includes an <parameterReference>adReason</parameterReference> parameter.</para>
    </content>
  </languageReferenceRemarks>
  <relatedTopics>
<link xlink:href="29530153-b963-4a7c-8665-2335f1d604a8">Visual C++ Example</link>
<link xlink:href="b34f4472-5e04-4a2c-ab64-38d6eca31a69">ADO Event Handler Summary</link>
<link xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset Object</link>
</relatedTopics>
</developerReferenceWithSyntaxDocument>