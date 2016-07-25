---
title: "IsolationLevel Property"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: ea84e4b2-fbf2-4eef-b9ce-796b22e21800
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
# IsolationLevel Property
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Indicates the level of isolation for a <legacyLink xlink:href="ef6b1824-5b12-43db-89d7-8f3d13896d4d">Connection</legacyLink> object.</para>
  </introduction>
  <section>
    <title>Settings and Return Values</title>
    <content>
      <para>Sets or returns an <legacyLink xlink:href="8e17a7bc-b8a3-4ae2-b6c9-ce088ad31fdf">IsolationLevelEnum</legacyLink> value. The default is <legacyBold>adXactReadCommitted</legacyBold>.</para>
    </content>
  </section>
  <languageReferenceRemarks>
    <content>
      <para>Use the <legacyBold>IsolationLevel</legacyBold> property to set the isolation level of a <legacyBold>Connection</legacyBold> object. The setting does not take effect until the next time you call the <legacyLink xlink:href="d4683472-4120-4236-8640-fa9ae289e23e">BeginTrans</legacyLink> method. If the level of isolation you request is unavailable, the provider may return the next greater level of isolation without updating the <legacyBold>IsolationLevel</legacyBold> property.</para>
      <para>The <legacyBold>IsolationLevel</legacyBold> property is read/write.</para>
      <alert class="note">
        <para>
          <legacyBold>Remote Data Service Usage</legacyBold>   When used on a client-side <legacyBold>Connection</legacyBold> object, the <legacyBold>IsolationLevel</legacyBold> property can be set only to <legacyBold>adXactUnspecified</legacyBold>. Because users are working with disconnected <legacyBold>Recordset</legacyBold> objects on a client-side cache, there may be multiuser issues. For instance, when two different users try to update the same record, Remote Data Service simply allows the user who updates the record first to "win." The second user's update request will fail with an error.</para>
      </alert>
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
<link xlink:href="3382fd41-0aa1-4091-97d3-624403111e07">Visual Basic Example</link>
<link xlink:href="92ddec5d-e3dc-4e8e-997a-c5417cceab69">Visual C++ Example</link>
<link xlink:href="7662d89a-c5f9-44db-8c93-606db48cdd96">Visual J++ Example</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>