---
title: "WillChangeRecordset and RecordsetChangeComplete Events (ADO)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: d5d44659-e0d9-46d9-a297-99c43555082f
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
# WillChangeRecordset and RecordsetChangeComplete Events (ADO)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The <legacyBold>WillChangeRecordset</legacyBold> event is called before a pending operation changes the <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink>. The <legacyBold>RecordsetChangeComplete</legacyBold> event is called after the <legacyBold>Recordset</legacyBold> has changed.</para>
  </introduction>
  <syntaxSection>
    <legacySyntax>
<legacyBold>WillChangeRecordset </legacyBold><parameterReference>adReason</parameterReference>, <parameterReference>adStatus</parameterReference>, <parameterReference>pRecordset</parameterReference>
<legacyBold>RecordsetChangeComplete </legacyBold><parameterReference>adReason</parameterReference>, <parameterReference>pError</parameterReference>, <parameterReference>adStatus</parameterReference>, <parameterReference>pRecordset</parameterReference></legacySyntax>
  </syntaxSection>
  <parameters>
    <content>
      <definitionTable>
        <definedTerm> <legacyItalic>adReason</legacyItalic> </definedTerm>
        <definition>
          <para>An <legacyLink xlink:href="7d4a5496-ec2d-4936-b36a-7049a82be4b4">EventReasonEnum</legacyLink> value that specifies the reason for this event. Its value can be <legacyBold>adRsnRequery</legacyBold>, <legacyBold>adRsnResynch</legacyBold>, <legacyBold>adRsnClose</legacyBold>, <legacyBold>adRsnOpen</legacyBold>.</para>
        </definition>
        <definedTerm> <legacyItalic>adStatus</legacyItalic> </definedTerm>
        <definition>
          <para>An <legacyLink xlink:href="ebfd4cda-4017-4873-9d28-38b1c7db12a8">EventStatusEnum</legacyLink> status value.</para>
          <para>When <legacyBold>WillChangeRecordset</legacyBold> is called, this parameter is set to <legacyBold>adStatusOK</legacyBold> if the operation that caused the event was successful. It is set to <legacyBold>adStatusCantDeny</legacyBold> if this event cannot request cancellation of the pending operation.   </para>
          <para>When <legacyBold>RecordsetChangeComplete</legacyBold> is called, this parameter is set to <legacyBold>adStatusOK</legacyBold> if the operation that caused the event was successful, <legacyBold>adStatusErrorsOccurred</legacyBold> if the operation failed, or <legacyBold>adStatusCancel</legacyBold> if the operation associated with the previously accepted <legacyBold>WillChangeRecordset</legacyBold> event has been canceled.   </para>
          <para>Before <legacyBold>WillChangeRecordset</legacyBold> returns, set this parameter to <legacyBold>adStatusCancel</legacyBold> to request cancellation of the pending operation or set this parameter to adStatusUnwantedEvent to prevent subsequent notifications.   </para>
          <para>Before <legacyBold>WillChangeRecordset</legacyBold> or <legacyBold>RecordsetChangeComplete</legacyBold> returns, set this parameter to <legacyBold>adStatusUnwantedEvent</legacyBold> to prevent subsequent notifications. </para>
        </definition>
        <definedTerm> <legacyItalic>pError</legacyItalic> </definedTerm>
        <definition>
          <para>An <legacyLink xlink:href="a175d453-fa55-4f49-9ede-a26d83177919">Error</legacyLink> object. It describes the error that occurred if the value of <legacyItalic>adStatus</legacyItalic> is <legacyBold>adStatusErrorsOccurred</legacyBold>; otherwise it is not set.</para>
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
      <para>A <legacyBold>WillChangeRecordset</legacyBold> or <legacyBold>RecordsetChangeComplete</legacyBold> event may occur because of the <legacyBold>Recordset</legacyBold> <legacyLink xlink:href="d81ab76f-1aa8-4ccf-92ec-b65254dc3ea1">Requery</legacyLink> or <legacyLink xlink:href="3236749c-4b71-4235-89e2-ccdfaaa9319d">Open</legacyLink> methods.</para>
      <para>If the provider does not support bookmarks, a <legacyBold>RecordsetChange</legacyBold> event notification occurs every time that new rows are retrieved from the provider. The frequency of this event depends on the <legacyBold>RecordsetCacheSize</legacyBold> property.</para>
      <para>You must set the <legacyBold>adStatus</legacyBold> parameter to <legacyBold>adStatusUnwantedEvent</legacyBold> for each possible <legacyBold>adReason</legacyBold> value to completely stop event notification for any event that includes an <legacyBold>adReason</legacyBold> parameter.</para>
    </content>
  </languageReferenceRemarks>
  <relatedTopics>
<link xlink:href="29530153-b963-4a7c-8665-2335f1d604a8">Visual C++ Example</link>
<link xlink:href="b34f4472-5e04-4a2c-ab64-38d6eca31a69">ADO Event Handler Summary</link>
</relatedTopics>
</developerReferenceWithSyntaxDocument>