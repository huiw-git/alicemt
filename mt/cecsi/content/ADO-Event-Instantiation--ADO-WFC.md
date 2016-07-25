---
title: "ADO Event Instantiation: ADO/WFC"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9ee4be21-657b-407a-afa4-0b27a6b096ce
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
# ADO Event Instantiation: ADO/WFC
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>ADO for Windows Foundation Classes (ADO/WFC) builds on the ADO event model and presents a simplified application programming interface. In general, ADO/WFC intercepts ADO events, consolidates the event parameters into a single event class, and then calls your event handler.</para>
    <procedure>
      <title>To use ADO events in ADO/WFC</title>
      <steps class="ordered">
        <step>
          <content>
            <para>Define your own event handler to process an event. For example, if you wanted to process the <legacyBold>ConnectComplete</legacyBold> event in the <legacyBold>ConnectionEvent</legacyBold> family, you might use this code: </para>
            <code>public void onConnectComplete(Object sender,ConnectionEvent e)
{
    System.out.println("onConnectComplete:" + e);
}</code>
          </content>
        </step>
        <step>
          <content>
            <para>Define a handler object to represent your event handler. The handler object should be of data type <legacyBold>ConnectEventHandler</legacyBold> for an event of type <legacyBold>ConnectionEvent</legacyBold>, or data type <legacyBold>RecordsetEventHandler</legacyBold> for an event of type <legacyBold>RecordsetEvent</legacyBold>. For example, code the following for your <legacyBold>ConnectComplete</legacyBold> event handler: </para>
            <code>    ConnectionEventHandler handler = 
        new ConnectionEventHandler(this, "onConnectComplete");</code>
            <para>The first argument of the <legacyBold>ConnectionEventHandler</legacyBold> constructor is a reference to the class that contains the event handler named in the second argument.  </para>
            <para>The Microsoft Visual J++ compiler also supports an equivalent syntax:  </para>
            <code>    ConnectionEventHandler handler = 
        new ConnectionEventHandler(this.onConnectComplete);</code>
            <para>The single argument is a reference to the desired class (<legacyBold>this</legacyBold>) and method within the class (<legacyBold>onConnectComplete</legacyBold>). </para>
          </content>
        </step>
        <step>
          <content>
            <para>Add your event handler to a list of handlers designated to process a particular type of event. Use the method with a name such as <legacyBold>addOn</legacyBold><legacyItalic>EventName</legacyItalic>(<legacyItalic>handler</legacyItalic>).</para>
          </content>
        </step>
        <step>
          <content>
            <para>ADO/WFC internally implements all the ADO event handlers. Therefore, an event caused by a <legacyBold>Connection</legacyBold> or <legacyBold>Recordset</legacyBold> operation is intercepted by an ADO/WFC event handler. </para>
            <para>The ADO/WFC event handler passes ADO <legacyBold>ConnectionEvent</legacyBold> parameters in an instance of the ADO/WFC <legacyBold>ConnectionEvent</legacyBold> class, or ADO <legacyBold>RecordsetEvent</legacyBold> parameters in an instance of the ADO/WFC <legacyBold>RecordsetEvent</legacyBold> class. These ADO/WFC classes consolidate the ADO event parameters; that is, each ADO/WFC class contains one data member for each unique parameter in all the ADO <legacyBold>ConnectionEvent</legacyBold> or <legacyBold>RecordsetEvent</legacyBold> methods. </para>
          </content>
        </step>
        <step>
          <content>
            <para>ADO/WFC then calls your event handler with the ADO/WFC event object. For example, your <legacyBold>onConnectComplete</legacyBold> handler has a signature like this: </para>
            <code>    public void onConnectComplete(Object sender,ConnectionEvent e)</code>
            <para>The first argument is the type of object that sent the event (<legacyLink xlink:href="ef6b1824-5b12-43db-89d7-8f3d13896d4d">Connection</legacyLink> or <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink>), and the second argument is the ADO/WFC event object (<legacyBold>ConnectionEvent</legacyBold> or <legacyBold>RecordsetEvent</legacyBold>).  </para>
            <para>The signature of your event handler is simpler than an ADO event. However, you must still understand the ADO event model to know what parameters apply to an event and how to respond. </para>
          </content>
        </step>
        <step>
          <content>
            <para>Return from your event handler to the ADO/WFC handler for the ADO event. ADO/WFC copies pertinent ADO/WFC event data members back to the ADO event parameters, and then the ADO event handler returns.</para>
          </content>
        </step>
        <step>
          <content>
            <para>When you are finished processing, remove your handler from the list of ADO/WFC event handlers. Use the method with a name such as <legacyBold>removeOn</legacyBold><legacyItalic>EventName</legacyItalic>(<legacyItalic>handler</legacyItalic>).</para>
          </content>
        </step>
      </steps>
    </procedure>
  </introduction>
  <relatedTopics>
<link xlink:href="b34f4472-5e04-4a2c-ab64-38d6eca31a69">ADO Event Handler Summary</link>
<link xlink:href="1fdfa42e-897e-4770-b320-ab3720adabcc">ADO/WFC Programming </link>
<link xlink:href="a14bbc36-87ec-409d-97b3-393b66b1b8e3">ADO/WFC Syntax Index</link>
<link xlink:href="bd5c5afa-d301-4899-acda-40f98a6afa4d">Event Parameters</link>
<link xlink:href="a86c8a02-dd69-420d-8a47-0188b339858d">How Event Handlers Work Together</link>
<link xlink:href="f3327ea0-635a-43d4-bd78-c1674f62f1a2">Types of Events</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>