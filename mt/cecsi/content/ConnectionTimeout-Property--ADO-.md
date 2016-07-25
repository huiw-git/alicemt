---
title: "ConnectionTimeout Property (ADO)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: 8904a403-1383-4b4b-b53d-5c01d6f5deac
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
# ConnectionTimeout Property (ADO)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Indicates how long to wait while establishing a connection before terminating the attempt and generating an error.</para>
  </introduction>
  <section>
    <title>Settings and Return Values</title>
    <content>
      <para>Sets or returns a <legacyBold>Long</legacyBold> value that indicates, in seconds, how long to wait for the connection to open. Default is 15.</para>
    </content>
  </section>
  <languageReferenceRemarks>
    <content>
      <para>Use the <legacyBold>ConnectionTimeout</legacyBold> property on a <legacyLink xlink:href="ef6b1824-5b12-43db-89d7-8f3d13896d4d">Connection</legacyLink> object if delays from network traffic or heavy server use make it necessary to abandon a connection attempt. If the time from the <legacyBold>ConnectionTimeout</legacyBold> property setting elapses prior to the opening of the connection, an error occurs and ADO cancels the attempt. If you set the property to zero, ADO will wait indefinitely until the connection is opened. Make sure the provider to which you are writing code supports the <legacyBold>ConnectionTimeout</legacyBold> functionality.</para>
      <para>The <legacyBold>ConnectionTimeout</legacyBold> property is read/write when the connection is closed and read-only when it is open.</para>
    </content>
  </languageReferenceRemarks>
  <section>
    <title>Applies To</title>
    <content>
      <para>
        <link xlink:href="ef6b1824-5b12-43db-89d7-8f3d13896d4d">Connection</link>
      </para>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="4de7336a-b5ea-43f1-b750-5fa302b5b756">Visual Basic Example</link>
<link xlink:href="c6bd2609-4c49-462f-a1aa-7bee0f615adb">Visual C++ Example</link>
<link xlink:href="4c1e61ed-6569-44a9-b0c8-75b820a64cb6">Visual J++ Example</link>
<link xlink:href="c611f857-d6b0-4dca-8925-f4a02e769eb0">CommandTimeout Property</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>