---
title: "Event Parameters"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: bd5c5afa-d301-4899-acda-40f98a6afa4d
caps.latest.revision: 9
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
# Event Parameters
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Every event handler has a status parameter that controls the event handler. For Complete events, this parameter is also used to indicate the success or failure of the operation that generated the event. Most Complete events also have an error parameter to provide information about any error that might have occurred, and one or more object parameters that refer to the ADO objects used to perform the operation. For example, the <legacyLink xlink:href="62470d42-e511-494c-bec4-ad4591734b7b">ExecuteComplete</legacyLink> event includes object parameters for the <legacyBold>Command</legacyBold>, <legacyBold>Recordset</legacyBold>, and <legacyBold>Connection</legacyBold> objects associated with the event. In the following Microsoft® Visual Basic® example, you can see the pCommand, pRecordset, and pConnection objects which represent the <legacyBold>Command</legacyBold>, <legacyBold>Recordset</legacyBold>, and <legacyBold>Connection</legacyBold> objects that are used by the <legacyBold>Execute</legacyBold> method.</para>
    <code>Private Sub connEvent_ExecuteComplete(ByVal RecordsAffected As Long, _
     ByVal pError As ADODB.Error, _
     adStatus As ADODB.EventStatusEnum, _
     ByVal pCommand As ADODB.Command, _
     ByVal pRecordset As ADODB.Recordset, _
     ByVal pConnection As ADODB.Connection)</code>
    <para>Except for the <legacyBold>Error </legacyBold>object, the same parameters are passed to the Will events. This lets you examine each of the objects that will be used in the pending operation and determine whether the operation should be allowed to finish.</para>
    <para>Some event handlers have a <legacyItalic>Reason</legacyItalic> parameter, which provides additional information about why the event occurred. For example, the <legacyBold>WillMove</legacyBold> and <legacyBold>MoveComplete</legacyBold> events can occur because of any one of the navigation methods (<legacyBold>MoveNext</legacyBold>, <legacyBold>MovePrevious</legacyBold>, and so on) being called or as the result of a requery.</para>
  </introduction>
  <section>
    <title>Status Parameter</title>
    <content>
      <para>When the event-handler routine is called, the <legacyItalic>Status</legacyItalic> parameter is set to one of the following values.</para>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>Value</para>
            </TD>
            <TD>
              <para>Description</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>               <legacyBold>adStatusOK</legacyBold>             </para>
            </TD>
            <TD>
              <para>Passed to both Will and Complete events. This value means that the operation that caused the event completed successfully.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>               <legacyBold>adStatusErrorsOccurred</legacyBold>             </para>
            </TD>
            <TD>
              <para>Passed to Complete events only. This value means that the operation that caused the event was unsuccessful, or a Will event canceled the operation. Check the <legacyItalic>Error</legacyItalic> parameter for more details.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>               <legacyBold>adStatusCantDeny</legacyBold>             </para>
            </TD>
            <TD>
              <para>Passed to Will events only. This value means that the operation cannot be canceled by the Will event. It must be performed.</para>
            </TD>
          </tr>
        </tbody>
      </table>
      <para>If you determine in your Will event that the operation should continue, leave the <legacyItalic>Status</legacyItalic> parameter unchanged. As long as the incoming status parameter was not set to <legacyBold>adStatusCantDeny</legacyBold>, however, you can cancel the pending operation by changing <legacyItalic>Status</legacyItalic> to <legacyBold>adStatusCancel</legacyBold>. When you do this, the Complete event associated with the operation has its <legacyItalic>Status</legacyItalic> parameter set to <legacyBold>adStatusErrorsOccurred</legacyBold>. The <legacyBold>Error</legacyBold> object passed to the Complete event will contain the value <legacyBold>adErrOperationCancelled</legacyBold>.</para>
      <para>If you no longer want to process an event, you can set <legacyItalic>Status</legacyItalic> to <legacyBold>adStatusUnwantedEvent</legacyBold> and your application will no longer receive notification of that event. However, remember that some events can be raised for more than one reason. In that case, you must specify <legacyBold>adStatusUnwantedEvent</legacyBold> for each possible reason. For example, to stop receiving notification of pending <legacyBold>RecordChange</legacyBold> events, you must set the <legacyItalic>Status</legacyItalic> parameter to <legacyBold>adStatusUnwantedEvent</legacyBold> for <legacyBold>adRsnAddNew</legacyBold>, <legacyBold>adRsnDelete</legacyBold>, <legacyBold>adRsnUpdate</legacyBold>, <legacyBold>adRsnUndoUpdate</legacyBold>, <legacyBold>adRsnUndoAddNew</legacyBold>, <legacyBold>adRsnUndoDelete</legacyBold>, and <legacyBold>adRsnFirstChange</legacyBold> as they occur.</para>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>Value</para>
            </TD>
            <TD>
              <para>Description</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>               <legacyBold>adStatusUnwantedEvent</legacyBold>             </para>
            </TD>
            <TD>
              <para>Request that this event handler receive no further notifications.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>               <legacyBold>adStatusCancel</legacyBold>             </para>
            </TD>
            <TD>
              <para>Request cancellation of the operation that is about to occur.</para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <section>
    <title>Error Parameter</title>
    <content>
      <para>The <legacyItalic>Error</legacyItalic> parameter is a reference to an ADO <legacyLink xlink:href="a175d453-fa55-4f49-9ede-a26d83177919">Error</legacyLink> object. When the <legacyItalic>Status</legacyItalic> parameter is set to <legacyBold>adStatusErrorsOccurred</legacyBold>, the <legacyBold>Error</legacyBold> object contains details about why the operation failed. If the Will event associated with a Complete event has canceled the operation by setting the <legacyItalic>Status</legacyItalic> parameter to <legacyBold>adStatusCancel</legacyBold>, the error object is always set to <legacyBold>adErrOperationCancelled</legacyBold>.</para>
    </content>
  </section>
  <section>
    <title>Object Parameter</title>
    <content>
      <para>Each event receives one or more objects representing the objects that are involved in the operation. For example, the <legacyBold>ExecuteComplete</legacyBold> event receives a <legacyBold>Command</legacyBold> object, a <legacyBold>Recordset</legacyBold> object, and a <legacyBold>Connection</legacyBold> object.</para>
    </content>
  </section>
  <section>
    <title>Reason Parameter</title>
    <content>
      <para>The <legacyItalic>Reason</legacyItalic> parameter, <legacyItalic>adReason</legacyItalic>, provides additional information about why the event occurred. Events with an <legacyItalic>adReason</legacyItalic> parameter may be called several times, even for the same operation, for a different reason every time. For example, the <legacyBold>WillChangeRecord</legacyBold> event handler is called for operations that are about to do or undo the insertion, deletion, or modification of a record. If you want to process an event only when it occurs for a particular reason, you can use the <legacyItalic>adReason</legacyItalic> parameter to filter out the occurrences you are not interested in. For example, if you wanted to process record-change events only when they occur because a record was added, you can use something like the following.</para>
      <code>' BeginEventExampleVB01
Private Sub rsTest_WillChangeRecord(ByVal adReason As ADODB.EventReasonEnum, ByVal cRecords As Long, adStatus As ADODB.EventStatusEnum, ByVal pRecordset As ADODB.Recordset)
   If adReason = adRsnAddNew Then
       ' Process event
       '...
   Else
       ' Cancel event notification for all
       ' other possible adReason values.
       adStatus = adStatusUnwantedEvent
   End If
End Sub
' EndEventExampleVB01</code>
      <para>In this case, notification can potentially occur for each of the other reasons. However, it will occur only once for each reason. After the notification has occurred once for each reason, you will receive notification only for the addition of a new record.</para>
      <para>In contrast, you need to set <legacyItalic>adStatus</legacyItalic> to <legacyBold>adStatusUnwantedEvent</legacyBold> only one time to request that an event handler without an <legacyBold>adReason</legacyBold> parameter stop receiving event notifications.</para>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="b34f4472-5e04-4a2c-ab64-38d6eca31a69">ADO Event Handler Summary</link>
<link xlink:href="eded7e8c-a25f-46a6-bc2b-32d89a54d1bc">ADO Event Instantiation by Language</link>
<link xlink:href="a86c8a02-dd69-420d-8a47-0188b339858d">How Event Handlers Work Together</link>
<link xlink:href="f3327ea0-635a-43d4-bd78-c1674f62f1a2">Types of Events</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>