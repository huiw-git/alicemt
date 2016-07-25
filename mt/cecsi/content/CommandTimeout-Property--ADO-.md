---
title: "CommandTimeout Property (ADO)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: c611f857-d6b0-4dca-8925-f4a02e769eb0
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
# CommandTimeout Property (ADO)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Indicates how long to wait while executing a command before terminating the attempt and generating an error.</para>
  </introduction>
  <section>
    <title>Settings and Return Values</title>
    <content>
      <para>Sets or returns a <languageKeyword>Long</languageKeyword> value that indicates, in seconds, how long to wait for a command to execute. Default is 30.</para>
    </content>
  </section>
  <languageReferenceRemarks>
    <content>
      <para>Use the <legacyBold>CommandTimeout</legacyBold> property on a <legacyLink xlink:href="ef6b1824-5b12-43db-89d7-8f3d13896d4d">Connection</legacyLink> object or <legacyLink xlink:href="a02c22fb-542d-465e-a629-30fd59dcbebf">Command</legacyLink> object to allow the cancellation of an <legacyLink xlink:href="f84a5ff3-0528-4ad7-9bea-9a15103378dd">Execute</legacyLink> method call, due to delays from network traffic or heavy server use. If the interval set in the <legacyBold>CommandTimeout</legacyBold> property elapses before the command completes execution, an error occurs and ADO cancels the command. If you set the property to zero, ADO will wait indefinitely until the execution is complete. Make sure the provider and data source to which you are writing code support the <legacyBold>CommandTimeout</legacyBold> functionality.</para>
      <para>The <legacyBold>CommandTimeout</legacyBold> setting on a <legacyBold>Connection</legacyBold> object has no effect on the <legacyBold>CommandTimeout</legacyBold> setting on a <legacyBold>Command</legacyBold> object on the same <legacyBold>Connection</legacyBold>; that is, the <legacyBold>Command</legacyBold> object's <legacyBold>CommandTimeout</legacyBold> property does not inherit the value of the <legacyBold>Connection</legacyBold> object's <legacyBold>CommandTimeout</legacyBold> value.</para>
      <para>On a <legacyBold>Connection</legacyBold> object, the <legacyBold>CommandTimeout</legacyBold> property remains read/write after the <legacyBold>Connection</legacyBold> is opened.</para>
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
                <link xlink:href="a02c22fb-542d-465e-a629-30fd59dcbebf">Command Object</link>
              </para>
            </TD>
            <TD>
              <para>
                <link xlink:href="ef6b1824-5b12-43db-89d7-8f3d13896d4d">Connection Object</link>
              </para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="dade4531-0bcc-4a52-8f86-b110ba2a3f9d">Visual Basic Example</link>
<link xlink:href="0d9917c4-9ef0-4d7a-b4ce-4f1fa6ce1817">Visual C++ Example</link>
<link xlink:href="69a4a219-8d52-401b-9e92-2ef415f68b05">Visual J++ Example</link>
<link xlink:href="ea74e2a3-c965-43aa-9076-26a084b48ad8">JScriptExample</link>
<link xlink:href="8904a403-1383-4b4b-b53d-5c01d6f5deac">ConnectionTimeout Property</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>