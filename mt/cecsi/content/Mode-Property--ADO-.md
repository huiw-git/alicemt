---
title: "Mode Property (ADO)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: 808661eb-0d7c-4e6d-8e40-9dc3bef3d77a
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
# Mode Property (ADO)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Indicates the available permissions for modifying data in a <legacyLink xlink:href="ef6b1824-5b12-43db-89d7-8f3d13896d4d">Connection</legacyLink>, <legacyLink xlink:href="db83ed2c-a8e3-460c-8682-64667e4d5d01">Record</legacyLink>, or <legacyLink xlink:href="0514531f-009d-4519-abc3-d727014a39f1">Stream</legacyLink> object.</para>
  </introduction>
  <section>
    <title>Settings and Return Values</title>
    <content>
      <para>Sets or returns a <legacyLink xlink:href="3792c294-5161-4538-a908-22a5fc50b85f">ConnectModeEnum</legacyLink> value. The default value for a <legacyBold>Connection</legacyBold> is <legacyBold>adModeUnknown</legacyBold>. The default value for a <legacyBold>Record</legacyBold> object is <legacyBold>adModeRead</legacyBold>. The default value for a <legacyBold>Stream</legacyBold> associated with an underlying source (opened with a URL as the source, or as the default <legacyBold>Stream</legacyBold> of a <legacyBold>Record</legacyBold>) is <legacyBold>adModeRead</legacyBold>. The default value for a <legacyBold>Stream</legacyBold> not associated with an underlying source (instantiated in memory) is <legacyBold>adModeUnknown</legacyBold>.</para>
    </content>
  </section>
  <languageReferenceRemarks>
    <content>
      <para>Use the <legacyBold>Mode</legacyBold> property to set or return the access permissions in use by the provider on the current connection. You can set the <legacyBold>Mode</legacyBold> property only when the <legacyBold>Connection</legacyBold> object is closed.</para>
      <para>For a <legacyBold>Stream</legacyBold> object, if the access mode is not specified, it is inherited from the source used to open the <legacyBold>Stream</legacyBold> object. For example, if a <legacyBold>Stream</legacyBold> is opened from a <legacyBold>Record</legacyBold> object, by default it is opened in the same mode as the <legacyBold>Record</legacyBold>.</para>
      <para>This property is read/write while the object is closed and read-only while the object is open.</para>
      <alert class="note">
        <para>
          <legacyBold>Remote Data Service Usage</legacyBold>   When used on a client-side <legacyBold>Connection</legacyBold> object, the <legacyBold>Mode</legacyBold> property can only be set to <legacyBold>adModeUnknown</legacyBold>.</para>
      </alert>
    </content>
  </languageReferenceRemarks>
  <section>
    <title>Applies To</title>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <tbody>
          <tr>
            <TD>
              <para>
                <link xlink:href="ef6b1824-5b12-43db-89d7-8f3d13896d4d">Connection</link>
              </para>
            </TD>
            <TD>
              <para>
                <link xlink:href="db83ed2c-a8e3-460c-8682-64667e4d5d01">Record</link>
              </para>
            </TD>
            <TD>
              <para>
                <link xlink:href="0514531f-009d-4519-abc3-d727014a39f1">Stream</link>
              </para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="3382fd41-0aa1-4091-97d3-624403111e07">Visual Basic Example</link>
<link xlink:href="92ddec5d-e3dc-4e8e-997a-c5417cceab69">Visual C++ Example</link>
<link xlink:href="7662d89a-c5f9-44db-8c93-606db48cdd96">Visual J++ Example</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>