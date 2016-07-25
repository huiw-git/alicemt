---
title: "WillChangeRecord and RecordChangeComplete Events (ADO)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: cbc369fd-63af-4a7d-96ae-efa91b78ca69
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
# WillChangeRecord and RecordChangeComplete Events (ADO)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The <legacyBold>WillChangeRecord</legacyBold> event is called before one or more records (rows) in the <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink> change. The <legacyBold>RecordChangeComplete</legacyBold> event is called after one or more records change.</para>
  </introduction>
  <syntaxSection>
    <legacySyntax>
<legacyBold>WillChangeRecord</legacyBold> <parameterReference>adReason</parameterReference>, <parameterReference>cRecords</parameterReference>, <parameterReference>adStatus</parameterReference>, <parameterReference>pRecordset</parameterReference>
<legacyBold>RecordChangeComplete</legacyBold><parameterReference>adReason</parameterReference>, <parameterReference>cRecords</parameterReference>, <parameterReference>pError</parameterReference>, <parameterReference>adStatus</parameterReference>, <parameterReference>pRecordset</parameterReference></legacySyntax>
  </syntaxSection>
  <parameters>
    <content>
      <definitionTable>
        <definedTerm> <legacyItalic>adReason</legacyItalic> </definedTerm>
        <definition>
          <para>An <legacyLink xlink:href="7d4a5496-ec2d-4936-b36a-7049a82be4b4">EventReasonEnum</legacyLink> value that specifies the reason for this event. Its value can be <legacyBold>adRsnAddNew</legacyBold>, <legacyBold>adRsnDelete</legacyBold>, <legacyBold>adRsnUpdate</legacyBold>, <legacyBold>adRsnUndoUpdate</legacyBold>, <legacyBold>adRsnUndoAddNew</legacyBold>, <legacyBold>adRsnUndoDelete</legacyBold>, or <legacyBold>adRsnFirstChange</legacyBold>.</para>
        </definition>
        <definedTerm> <legacyItalic>cRecords</legacyItalic> </definedTerm>
        <definition>
          <para>A <languageKeyword>Long</languageKeyword> value that indicates the number of records changing (affected).</para>
        </definition>
        <definedTerm> <legacyItalic>pError</legacyItalic> </definedTerm>
        <definition>
          <para>An <legacyLink xlink:href="a175d453-fa55-4f49-9ede-a26d83177919">Error</legacyLink> object. It describes the error that occurred if the value of <legacyItalic>adStatus</legacyItalic> is <legacyBold>adStatusErrorsOccurred</legacyBold>; otherwise it is not set.</para>
        </definition>
        <definedTerm> <legacyItalic>adStatus</legacyItalic> </definedTerm>
        <definition>
          <para>An <legacyLink xlink:href="ebfd4cda-4017-4873-9d28-38b1c7db12a8">EventStatusEnum</legacyLink> status value.</para>
          <para>When <legacyBold>WillChangeRecord</legacyBold> is called, this parameter is set to <legacyBold>adStatusOK </legacyBold>if the operation that caused the event was successful. It is set to <legacyBold>adStatusCantDeny</legacyBold> if this event cannot request cancellation of the pending operation.   </para>
          <para>When <legacyBold>RecordChangeComplete</legacyBold> is called, this parameter is set to <legacyBold>adStatusOK</legacyBold> if the operation that caused the event was successful, or to <legacyBold>adStatusErrorsOccurred</legacyBold> if the operation failed.   </para>
          <para>Before <legacyBold>WillChangeRecord</legacyBold> returns, set this parameter to <legacyBold>adStatusCancel</legacyBold> to request cancellation of the operation that caused this event or set this parameter to <legacyBold>adStatusUnwantedEvent</legacyBold> to prevent subsequent notifications.   </para>
          <para>Before <legacyBold>RecordChangeComplete</legacyBold> returns, set this parameter to <legacyBold>adStatusUnwantedEvent</legacyBold> to prevent subsequent notifications. </para>
        </definition>
        <definedTerm> <legacyItalic>pRecordset</legacyItalic> </definedTerm>
        <definition>
          <para>A <legacyBold>Recordset</legacyBold> object. The <legacyBold>Recordset</legacyBold> for which this event occurred.</para>
        </definition>
      </definitionTable>
    </content>
  </parameters>
  <languageReferenceRemarks>
    <content>
      <para>A <legacyBold>WillChangeRecord</legacyBold> or <legacyBold>RecordChangeComplete</legacyBold> event may occur for the first changed field in a row due to the following <legacyBold>Recordset</legacyBold> operations: <legacyLink xlink:href="6b2a9c31-1a7e-40db-8a53-30720d0f6cc1">Update</legacyLink>, <legacyLink xlink:href="1eb9209c-602c-4507-b0c2-6527a599b67d">Delete</legacyLink>, <legacyLink xlink:href="eaa856cc-c786-462e-890c-c896261b1741">CancelUpdate</legacyLink>, <legacyLink xlink:href="a9f54be9-5763-45d0-a6eb-09981b03bc08">AddNew</legacyLink>, <legacyLink xlink:href="23f9314c-b027-4a51-aeae-50caa2977740">UpdateBatch</legacyLink>, and <legacyLink xlink:href="dbdc2574-e44e-4d95-b03d-4a5d9e9adf3c">CancelBatch</legacyLink>. The value of the <legacyBold>Recordset</legacyBold> <legacyLink xlink:href="b62c66ca-58d5-430e-9257-eb38c65e48c2">CursorType</legacyLink> determines which operations cause the events to occur.</para>
      <para>During the <legacyBold>WillChangeRecord</legacyBold> event, the <legacyBold>Recordset</legacyBold> <legacyLink xlink:href="80263a7a-5d21-45d1-84fc-34b7a9be4c22">Filter</legacyLink> property is set to <legacyBold>adFilterAffectedRecords</legacyBold>. You cannot change this property while processing the event.</para>
      <para>You must set the <legacyBold>adStatus</legacyBold> parameter to <legacyBold>adStatusUnwantedEvent</legacyBold> for each possible <legacyBold>adReason</legacyBold> value to completely stop event notification for any event that includes an <legacyBold>adReason</legacyBold> parameter.</para>
    </content>
  </languageReferenceRemarks>
  <relatedTopics>
<link xlink:href="29530153-b963-4a7c-8665-2335f1d604a8">Visual C++ Example</link>
<link xlink:href="b34f4472-5e04-4a2c-ab64-38d6eca31a69">ADO Event Handler Summary</link>
</relatedTopics>
</developerReferenceWithSyntaxDocument>