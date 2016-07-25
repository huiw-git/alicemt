---
title: "Types of Events"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f3327ea0-635a-43d4-bd78-c1674f62f1a2
caps.latest.revision: 8
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
# Types of Events
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>There are two basic types of events. "Will Events," which are called before an operation starts, usually include "Will" in their names — for example, <legacyBold>WillChangeRecordset</legacyBold> or <legacyBold>WillConnect</legacyBold>. Events that are called after an event has been completed usually include "Complete" in their names — for example, <legacyBold>RecordChangeComplete</legacyBold> or <legacyBold>ConnectComplete</legacyBold>. Exceptions exist — such as <legacyBold>InfoMessage</legacyBold>
			— but these occur after the associated operation has completed. </para>
  </introduction>
  <section>
    <title>Will Events</title>
    <content>
      <para>Event handlers called before the operation starts offer you the opportunity to examine or modify the operation parameters, and then either cancel the operation or allow it to complete. These event-handler routines usually have names of the form <legacyBold>Will</legacyBold><legacyBold><legacyItalic>Event</legacyItalic></legacyBold>.</para>
    </content>
  </section>
  <section>
    <title>Complete Events</title>
    <content>
      <para>Event handlers called after an operation completes can notify your application that an operation has concluded. Such an event handler is also notified when a Will event handler cancels a pending operation. These event-handler routines usually have names of the form <legacyBold><legacyItalic>Event</legacyItalic></legacyBold><legacyBold>Complete</legacyBold>.</para>
      <para>Will and Complete events are typically used in pairs.</para>
    </content>
  </section>
  <section>
    <title>Other Events</title>
    <content>
      <para>The other event handlers — that is, events whose names are not of the form <legacyBold>Will</legacyBold><legacyBold><legacyItalic>Event</legacyItalic></legacyBold> or <legacyBold><legacyItalic>Event</legacyItalic></legacyBold><legacyBold>Complete</legacyBold>
			— are called only after an operation completes. These events are <legacyBold>Disconnect</legacyBold>, <legacyBold>EndOfRecordset</legacyBold>, and <legacyBold>InfoMessage</legacyBold>.</para>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="b34f4472-5e04-4a2c-ab64-38d6eca31a69">ADO Event Handler Summary</link>
<link xlink:href="eded7e8c-a25f-46a6-bc2b-32d89a54d1bc">ADO Event Instantiation by Language</link>
<link xlink:href="bd5c5afa-d301-4899-acda-40f98a6afa4d">Event Parameters</link>
<link xlink:href="a86c8a02-dd69-420d-8a47-0188b339858d">How Event Handlers Work Together</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>