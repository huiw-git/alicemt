---
title: "Prompt Property-Dynamic (ADO)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: c4f001b5-8d16-4d39-a42e-c0e2faaaceaf
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
# Prompt Property-Dynamic (ADO)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Specifies whether the OLE DB provider should prompt the user for initialization information.</para>
  </introduction>
  <section>
    <title>Settings and Return Values</title>
    <content>
      <para>Sets and returns a <legacyLink xlink:href="21026e24-62b7-4cc9-8aef-62c1fc6cba75">ConnectPromptEnum</legacyLink> value.</para>
    </content>
  </section>
  <languageReferenceRemarks>
    <content>
      <para>
        <legacyBold>Prompt</legacyBold> is a dynamic property, which may be appended to the <legacyLink xlink:href="ef6b1824-5b12-43db-89d7-8f3d13896d4d">Connection</legacyLink> object's <legacyLink xlink:href="1d539aa8-ce0d-4418-ab03-8d0a3c1e9d82">Properties</legacyLink> collection by the OLE DB provider. To prompt for initialization information, OLE DB providers will typically display a dialog box to the user.</para>
      <para>Dynamic properties of a <legacyLink xlink:href="ef6b1824-5b12-43db-89d7-8f3d13896d4d">Connection</legacyLink> object are lost when the <legacyBold>Connection</legacyBold> is closed. The <legacyBold>Prompt</legacyBold> property must be reset before re-opening the <legacyBold>Connection</legacyBold> to use a value other than the default.</para>
      <alert class="note">
        <para>Do not specify that the provider should prompt the user in scenarios in which the user will not be able to respond to the dialog box. For example, the user will not be able to respond if the application is running on a server system instead of on the user's client, or if the application is running on a system with no user logged on. In these cases, the application will wait indefinitely for a response and seem to lock up.</para>
      </alert>
    </content>
  </languageReferenceRemarks>
  <section>
    <title>Usage</title>
    <content>
      <code>Set cn = New Connection
cn.Provider = "SQLOLEDB"
cn.Properties("Prompt") = adPromptNever    ' do not prompt the user</code>
    </content>
  </section>
  <section>
    <title>Applies To</title>
    <content>
      <para>
        <link xlink:href="ef6b1824-5b12-43db-89d7-8f3d13896d4d">Connection Object</link>
      </para>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>