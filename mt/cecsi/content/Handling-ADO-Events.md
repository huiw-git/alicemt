---
title: "Handling ADO Events"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e9003457-0762-48b3-942f-0820266b158f
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
# Handling ADO Events
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The ADO event model supports certain synchronous and asynchronous ADO operations that issue <legacyItalic>events</legacyItalic>, or notifications, before the operation starts or after it completes. An event is actually a call to an event-handler routine that you define in your application.</para>
    <para>If you provide handler functions or procedures for the group of events that occur before the operation starts, you can examine or modify the parameters that were passed to the operation. Because it has not been executed yet, you can either cancel the operation or allow it to complete.</para>
    <para>The events that occur after an operation completes are especially important if you use ADO asynchronously. For example, an application that starts an asynchronous <legacyLink xlink:href="3236749c-4b71-4235-89e2-ccdfaaa9319d">Recordset.Open</legacyLink> operation is notified by an execution complete event when the operation concludes.</para>
    <para>Using the ADO event model adds some overhead to your application but provides far more flexibility than other methods of dealing with asynchronous operations, such as monitoring the <legacyLink xlink:href="0b993bac-2653-40b1-bcbb-5b57b6aae2bf">State</legacyLink> property of an object with a loop.</para>
    <alert class="note">
      <para>To handle events, ADO needs to have a message pump or be used in a single-threaded apartment (STA) model. ADO events are internally handled by creating a hidden window. ADO posts messages to this window when events need to be fired. This is done to ensure that events are sent to the thread that called <unmanagedCodeEntityReference>IConnectionPoint::Advise</unmanagedCodeEntityReference> on the connection point. This architecture can cause problems when the thread that should receive the notifications does not pump window messages. Potential problems include ADO events not being delivered to the thread and global window broadcasts timing out and possibly slowing down the entire system because the hidden windows do not process the messages. STA threads typically have a message pump running so this issue does not manifest itself on STA threads. MTA threads, however, do not typically have a message pump so the issue will typically manifest itself on MTA threads.</para>
    </alert>
    <para>This section contains the following topics.</para>
    <list class="bullet">
      <listItem>
        <para>
          <legacyLink xlink:href="b34f4472-5e04-4a2c-ab64-38d6eca31a69">ADO Event Handler Summary</legacyLink>
        </para>
      </listItem>
      <listItem>
        <para>
          <legacyLink xlink:href="f3327ea0-635a-43d4-bd78-c1674f62f1a2">Types of Events</legacyLink>
        </para>
      </listItem>
      <listItem>
        <para>
          <legacyLink xlink:href="bd5c5afa-d301-4899-acda-40f98a6afa4d">Event Parameters</legacyLink>
        </para>
      </listItem>
      <listItem>
        <para>
          <legacyLink xlink:href="a86c8a02-dd69-420d-8a47-0188b339858d">How Event Handlers Work Together</legacyLink>
        </para>
      </listItem>
      <listItem>
        <para>
          <legacyLink xlink:href="eded7e8c-a25f-46a6-bc2b-32d89a54d1bc">ADO Event Instantiation by Language</legacyLink>
        </para>
      </listItem>
    </list>
  </introduction>
  <relatedTopics>
<link xlink:href="b34f4472-5e04-4a2c-ab64-38d6eca31a69">ADO Event Handler Summary</link>
<link xlink:href="eded7e8c-a25f-46a6-bc2b-32d89a54d1bc">ADO Event Instantiation by Language</link>
<link xlink:href="0ded5ad9-8f83-4224-95af-38512783b972">ADO Events</link>
<link xlink:href="bd5c5afa-d301-4899-acda-40f98a6afa4d">Event Parameters</link>
<link xlink:href="f3327ea0-635a-43d4-bd78-c1674f62f1a2">Types of Events</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>