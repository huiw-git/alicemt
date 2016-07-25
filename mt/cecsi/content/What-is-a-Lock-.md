---
title: "What is a Lock?"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f8989555-28c6-4c17-9bf8-7f44a8a5c407
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
# What is a Lock?
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Locking is the process by which a DBMS restricts access to a row in a multi-user environment. When a row or column is exclusively locked, other users are not permitted to access the locked data until the lock is released. This ensures that two users cannot simultaneously update the same column in a row.</para>
    <para>Locks can be very expensive from a resource perspective and should be used only when required to preserve data integrity. In a database where hundreds or thousands of users could be trying to access a record every second — such as a database connected to the Internet — unnecessary locking could quickly result in slower performance in your application.</para>
    <para>You can control how the data source and the ADO cursor library manage concurrency by choosing the appropriate locking option.</para>
    <para>Set the <legacyBold>LockType</legacyBold> property before opening a <legacyBold>Recordset</legacyBold> to specify what type of locking the provider should use when opening it. Read the property to return the type of locking in use on an open <legacyBold>Recordset</legacyBold> object.</para>
    <para>Providers might not support all lock types. If a provider cannot support the requested <legacyBold>LockType</legacyBold> setting, it will substitute another type of locking. To determine the actual locking functionality available in a <legacyBold>Recordset</legacyBold> object, use the <legacyLink xlink:href="298fc41c-0b55-42fc-b373-c5133b4da6a5">Supports</legacyLink> method with <legacyBold>adUpdate</legacyBold> and <legacyBold>adUpdateBatch</legacyBold>.</para>
    <para>The <legacyBold>adLockPessimistic</legacyBold> setting is not supported if the <legacyLink xlink:href="39c8d86e-7ee9-4182-be5e-aad5ce952f84">CursorLocation</legacyLink> property is set to <legacyBold>adUseClient.</legacyBold> If an unsupported value is set, no error will result; the closest supported <legacyBold>LockType</legacyBold> will be used instead.</para>
    <para>The <legacyBold>LockType</legacyBold> property is read/write when the <legacyBold>Recordset</legacyBold> is closed, and read-only when it is open.</para>
    <para>This section contains the following topics.  </para>
    <list class="bullet">
      <listItem>
        <para>             <legacyLink xlink:href="12a978c0-b8a0-4ef0-87f0-a43c13659272">Types of Locks</legacyLink>           </para>
      </listItem>
    </list>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>