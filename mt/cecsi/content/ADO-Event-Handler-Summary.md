---
title: "ADO Event Handler Summary"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b34f4472-5e04-4a2c-ab64-38d6eca31a69
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
# ADO Event Handler Summary
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Two ADO objects can raise events: the <legacyLink xlink:href="ef6b1824-5b12-43db-89d7-8f3d13896d4d">Connection</legacyLink> object and the <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink> object. The <legacyBold>ConnectionEvent</legacyBold> family pertains to operations on the <legacyBold>Connection</legacyBold> object, and the <legacyBold>RecordsetEvent</legacyBold> family pertains to operations on the <legacyBold>Recordset</legacyBold> object.  </para>
    <list class="bullet">
      <listItem>
        <para>             <legacyBold>Connection Events</legacyBold>: Events are issued when a transaction on a connection begins, is committed, or is rolled back; when a <legacyLink xlink:href="a02c22fb-542d-465e-a629-30fd59dcbebf">Command</legacyLink> executes; when a warning occurs during a <legacyBold>Connection Event</legacyBold> operation; or when a <legacyBold>Connection</legacyBold> starts or ends.</para>
      </listItem>
      <listItem>
        <para>             <legacyBold>Recordset Events</legacyBold>: Events are issued around asynchronous fetch operations as well as when you navigate through the rows of a <legacyBold>Recordset</legacyBold> object, change a field in a row of a <legacyBold>Recordset</legacyBold>, change a row in a <legacyBold>Recordset</legacyBold>, open a <legacyBold>Recordset</legacyBold> with a server-side cursor, close a <legacyBold>Recordset</legacyBold>, or make any change whatsoever in the <legacyBold>Recordset</legacyBold>.</para>
      </listItem>
    </list>
    <para>The following tables summarize the events and their descriptions.</para>
    <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
      <thead>
        <tr>
          <TD>
            <para>ConnectionEvent</para>
          </TD>
          <TD>
            <para>Description</para>
          </TD>
        </tr>
      </thead>
      <tbody>
        <tr>
          <TD>
            <para>               <legacyLink xlink:href="ec4e4b38-e9c6-4757-b2ef-4e468ae5f1d8">BeginTransComplete, CommitTransComplete, RollbackTransComplete</legacyLink>             </para>
          </TD>
          <TD>
            <para>               <legacyBold>Transaction Management</legacyBold> — Notification that the current transaction on the connection has started, committed, or rolled back.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyLink xlink:href="da561d58-eb58-446c-a4fd-1838c76073c0">WillConnect</legacyLink>, <legacyLink xlink:href="568f5252-d069-4d99-a01b-2ada87ad1304">ConnectComplete, Disconnect</legacyLink></para>
          </TD>
          <TD>
            <para>               <legacyBold>Connection Management</legacyBold> — Notification that the current connection will start, has started, or has ended.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyLink xlink:href="dd755e46-f589-48a3-93a9-51ff998d44b5">WillExecute</legacyLink>, <legacyLink xlink:href="62470d42-e511-494c-bec4-ad4591734b7b">ExecuteComplete</legacyLink></para>
          </TD>
          <TD>
            <para>               <legacyBold>Command Execution Management</legacyBold> — Notification that the execution of the current command on the connection will start or has ended.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyLink xlink:href="468c87dd-e3bc-4084-9941-94d10743d4e9">InfoMessage</legacyLink>             </para>
          </TD>
          <TD>
            <para>               <legacyBold>Informational</legacyBold> — Notification that there is additional information about the current operation.</para>
          </TD>
        </tr>
      </tbody>
    </table>
    <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
      <thead>
        <tr>
          <TD>
            <para>RecordsetEvent</para>
          </TD>
          <TD>
            <para>Description</para>
          </TD>
        </tr>
      </thead>
      <tbody>
        <tr>
          <TD>
            <para>               <legacyLink xlink:href="301716fd-81fc-40eb-8a04-221ef7ab410e">FetchProgress</legacyLink>, <legacyLink xlink:href="a28d3858-566c-468d-b070-d1de4339fbea">FetchComplete</legacyLink></para>
          </TD>
          <TD>
            <para>               <legacyBold>Retrieval Status</legacyBold> — Notification of the progress of a data retrieval operation, or that the retrieval operation has completed. These events are only available if the <legacyBold>Recordset</legacyBold> was opened using a client-side cursor.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyLink xlink:href="3e49fb89-c45b-4d39-823e-3cc887c59b37">WillChangeField, FieldChangeComplete</legacyLink>             </para>
          </TD>
          <TD>
            <para>               <legacyBold>Field Change Management</legacyBold> — Notification that the value of the current field will change, or has changed.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyLink xlink:href="1a3d1042-4f30-4526-a0c7-853c242496db">WillMove, MoveComplete</legacyLink>, <legacyLink xlink:href="475de5e2-f634-4954-9edf-0027a6ba38d6">EndOfRecordset</legacyLink></para>
          </TD>
          <TD>
            <para>               <legacyBold>Navigation Management</legacyBold> — Notification that the current row position in a <legacyBold>Recordset</legacyBold> will change, has changed, or has reached the end of the <legacyBold>Recordset</legacyBold>.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyLink xlink:href="cbc369fd-63af-4a7d-96ae-efa91b78ca69">WillChangeRecord, RecordChangeComplete</legacyLink>             </para>
          </TD>
          <TD>
            <para>               <legacyBold>Row Change Management</legacyBold> — Notification that something in the current row of the <legacyBold>Recordset</legacyBold> will change, or has changed.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyLink xlink:href="d5d44659-e0d9-46d9-a297-99c43555082f">WillChangeRecordset, RecordsetChangeComplete</legacyLink>             </para>
          </TD>
          <TD>
            <para>               <legacyBold>Recordset Change Management</legacyBold> — Notification that something in the current <legacyBold>Recordset</legacyBold> will change, or has changed.</para>
          </TD>
        </tr>
      </tbody>
    </table>
  </introduction>
  <relatedTopics>
<link xlink:href="eded7e8c-a25f-46a6-bc2b-32d89a54d1bc">ADO Event Instantiation by Language</link>
<link xlink:href="0ded5ad9-8f83-4224-95af-38512783b972">ADO Events</link>
<link xlink:href="bd5c5afa-d301-4899-acda-40f98a6afa4d">Event Parameters</link>
<link xlink:href="a86c8a02-dd69-420d-8a47-0188b339858d">How Event Handlers Work Together</link>
<link xlink:href="f3327ea0-635a-43d4-bd78-c1674f62f1a2">Types of Events</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>