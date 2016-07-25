---
title: "How Event Handlers Work Together"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a86c8a02-dd69-420d-8a47-0188b339858d
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
# How Event Handlers Work Together
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Unless you are programming in Visual Basic, all event handlers for <legacyBold>Connection</legacyBold> and <legacyBold>Recordset</legacyBold> events must be implemented, regardless of whether you actually process all of the events. The amount of implementation work you have to do depends on your programming language. For more information, see <legacyLink xlink:href="eded7e8c-a25f-46a6-bc2b-32d89a54d1bc">ADO Event Instantiation by Language</legacyLink>.</para>
  </introduction>
  <section>
    <title>Paired Event Handlers</title>
    <content>
      <para>Each Will event handler has an associated <unmanagedCodeEntityReference>Complete</unmanagedCodeEntityReference> event handler. For example, when your application changes the value of a field, the <legacyBold>WillChangeField</legacyBold> event handler is called. If the change is acceptable, your application leaves the <legacyBold>adStatus</legacyBold> parameter unchanged and the operation is performed. When the operation completes, a <legacyBold>FieldChangeComplete</legacyBold> event notifies your application that the operation has finished. If it completed successfully, <legacyBold>adStatus</legacyBold> contains <legacyBold>adStatusOK</legacyBold>; otherwise, <legacyBold>adStatus</legacyBold> contains <legacyBold>adStatusErrorsOccurred</legacyBold> and you must check the <legacyBold>Error</legacyBold> object to determine the cause of the error.</para>
      <para>When <legacyBold>WillChangeField</legacyBold> is called, you might determine that the change should not be made. In that case, set <legacyBold>adStatus</legacyBold> to <legacyBold>adStatusCancel.</legacyBold> The operation is canceled and the <legacyBold>FieldChangeComplete</legacyBold> event receives an <legacyBold>adStatus</legacyBold> value of <legacyBold>adStatusErrorsOccurred</legacyBold>. The <legacyBold>Error</legacyBold> object contains <legacyBold>adErrOperationCancelled</legacyBold> so that your <legacyBold>FieldChangeComplete</legacyBold> handler knows that the operation was canceled. However, you need to check the value of the <legacyBold>adStatus</legacyBold> parameter before changing it, because setting <legacyBold>adStatus</legacyBold> to <legacyBold>adStatusCancel</legacyBold> has no effect if the parameter was set to <legacyBold>adStatusCantDeny</legacyBold> on entry to the procedure.</para>
      <para>Sometimes an operation can raise more than one event. For example, the <legacyBold>Recordset</legacyBold> object has paired events for <legacyBold>Field</legacyBold> changes and <legacyBold>Record</legacyBold> changes. When your application changes the value of a <legacyBold>Field</legacyBold>, the <legacyBold>WillChangeField</legacyBold> event handler is called. If it determines that the operation can continue, the <legacyBold>WillChangeRecord</legacyBold> event handler is also raised. If this handler also allows the event to continue, the change is made and the <legacyBold>FieldChangeComplete</legacyBold> and <legacyBold>RecordChangeComplete</legacyBold> event handlers are called. The order in which the Will event handlers for a particular operation are called is not defined, so you should avoid writing code that depends on calling handlers in a particular sequence.</para>
      <para>In instances when multiple Will events are raised, one of the events might cancel the pending operation. For example, when your application changes the value of a <legacyBold>Field</legacyBold>, both <legacyBold>WillChangeField</legacyBold> and <legacyBold>WillChangeRecord</legacyBold> event handlers would normally be called. However, if the operation is canceled in the first event handler, its associated <unmanagedCodeEntityReference>Complete</unmanagedCodeEntityReference> handler is immediately called with <legacyBold>adStatusOperationCancelled</legacyBold>. The second handler is never called. If, however, the first event handler allows the event to proceed, the other event handler will be called. If it then cancels the operation, both <unmanagedCodeEntityReference>Complete</unmanagedCodeEntityReference> events will be called as in the earlier examples.</para>
    </content>
  </section>
  <section>
    <title>Unpaired Event Handlers</title>
    <content>
      <para>As long as the status passed to the event is not <legacyBold>adStatusCantDeny</legacyBold>, you can turn off event notifications for any event by returning <legacyBold>adStatusUnwantedEvent</legacyBold> in the <legacyItalic>Status</legacyItalic> parameter. For example, when your <unmanagedCodeEntityReference>Complete</unmanagedCodeEntityReference> event handler is called the first time, you can return <legacyBold>adStatusUnwantedEvent</legacyBold>. You will subsequently receive only <unmanagedCodeEntityReference>Will</unmanagedCodeEntityReference> events. However, some events can be triggered for more than one reason. In that case, the event will have a <legacyItalic>Reason</legacyItalic> parameter. When you return <legacyBold>adStatusUnwantedEvent</legacyBold>, you will stop receiving notifications for that event only when they occur for that particular reason. In other words, you will potentially receive notification for each possible reason that the event could be triggered.</para>
      <para>Single <unmanagedCodeEntityReference>Will</unmanagedCodeEntityReference> event handlers can be useful when you want to examine the parameters that will be used in an operation. You can modify those operation parameters or cancel the operation.</para>
      <para>Alternatively, leave <unmanagedCodeEntityReference>Complete</unmanagedCodeEntityReference> event notification enabled. When your first Will event handler is called, return <legacyBold>adStatusUnwantedEvent</legacyBold>. You will subsequently receive only <unmanagedCodeEntityReference>Complete</unmanagedCodeEntityReference> events.</para>
      <para>Single <unmanagedCodeEntityReference>Complete</unmanagedCodeEntityReference> event handlers can be useful for managing asynchronous operations. Each asynchronous operation has an appropriate <unmanagedCodeEntityReference>Complete</unmanagedCodeEntityReference> event.</para>
      <para>For example, it can take a long time to populate a large <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink> object. If your application is appropriately written, you can start a <codeInline>Recordset.Open(...,adAsyncExecute)</codeInline> operation and continue with other processing. You will eventually be notified when the <legacyBold>Recordset</legacyBold> is populated by an <legacyBold>ExecuteComplete</legacyBold> event.</para>
    </content>
  </section>
  <section>
    <title>Single Event Handlers and Multiple Objects</title>
    <content>
      <para>The flexibility of a programming language like Microsoft Visual C++® enables you to have one event handler process events from multiple objects. For example, you could have one <legacyBold>Disconnect</legacyBold> event handler process events from several <legacyBold>Connection</legacyBold> objects. If one of the connections ended, the <legacyBold>Disconnect</legacyBold> event handler would be called. You could tell which connection caused the event because the event-handler object parameter would be set to the corresponding <legacyBold>Connection</legacyBold> object.</para>
      <alert class="note">
        <para>This technique cannot be used in Visual Basic because that language can correlate only one object to an event handler.</para>
      </alert>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="b34f4472-5e04-4a2c-ab64-38d6eca31a69">ADO Event Handler Summary</link>
<link xlink:href="eded7e8c-a25f-46a6-bc2b-32d89a54d1bc">ADO Event Instantiation by Language</link>
<link xlink:href="bd5c5afa-d301-4899-acda-40f98a6afa4d">Event Parameters</link>
<link xlink:href="f3327ea0-635a-43d4-bd78-c1674f62f1a2">Types of Events</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>