---
title: "Name Property (ADO)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: cfd0e29c-8310-44ab-85c3-5761184b865d
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
# Name Property (ADO)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Indicates the name of an object.</para>
  </introduction>
  <section>
    <title>Settings and Return Values</title>
    <content>
      <para>Sets or returns a <languageKeyword>String</languageKeyword> value that indicates the name of an object.</para>
    </content>
  </section>
  <languageReferenceRemarks>
    <content>
      <para>Use the <legacyBold>Name</legacyBold> property to assign a name to or retrieve the name of a <legacyBold>Command</legacyBold>, <legacyBold>Property</legacyBold>, <legacyBold>Field</legacyBold>, or <legacyBold>Parameter</legacyBold> object.</para>
      <para>The value is read/write on a <legacyBold>Command</legacyBold> object and read-only on a <legacyBold>Property</legacyBold> object.</para>
      <para>For a <legacyBold>Field</legacyBold> object, <legacyBold>Name</legacyBold> is normally read-only. However, for new <legacyBold>Field</legacyBold> objects that have been appended to the <legacyLink xlink:href="7c371474-b88f-4730-afa5-44163a0488d5">Fields</legacyLink> collection of a <legacyLink xlink:href="db83ed2c-a8e3-460c-8682-64667e4d5d01">Record</legacyLink>, <legacyBold>Name</legacyBold> is read/write only after the <legacyLink xlink:href="48919c74-86d4-462e-99b9-8854ceb8d683">Value</legacyLink> property for the <legacyBold>Field</legacyBold> has been specified and the data provider has successfully added the new <legacyBold>Field</legacyBold> by calling the <legacyLink xlink:href="6b2a9c31-1a7e-40db-8a53-30720d0f6cc1">Update</legacyLink> method of the <legacyBold>Fields</legacyBold> collection.</para>
      <para>For <legacyBold>Parameter</legacyBold> objects not yet appended to the <legacyLink xlink:href="497cae10-3913-422a-9753-dcbb0a639b1b">Parameters</legacyLink> collection, the <legacyBold>Name</legacyBold> property is read/write. For appended <legacyBold>Parameter</legacyBold> objects and all other objects, the <legacyBold>Name</legacyBold> property is read-only. Names do not have to be unique within a collection.</para>
      <para>You can retrieve the <legacyBold>Name</legacyBold> property of an object by an ordinal reference, after which you can refer to the object directly by name. For example, if <codeInline>rstMain.Properties(20).Name</codeInline> yields <codeInline>Updatability</codeInline>, you can subsequently refer to this property as <codeInline>rstMain.Properties("Updatability")</codeInline>.</para>
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
                <link xlink:href="b10a72fc-3c4b-4186-a70b-993dc9f7a092">Field Object</link>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <link xlink:href="e010e794-7f0f-4026-8b5b-37328e437d63">Parameter Object</link>
              </para>
            </TD>
            <TD>
              <para>
                <link xlink:href="b2a4767c-03c7-4935-a3bc-df3e1a38a009">Property Object</link>
              </para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="258bdce3-1819-44a2-9217-105879c789ef">Visual Basic Example</link>
<link xlink:href="2db7c9ca-d7d0-4c8e-840b-b27d7933ec40">Visual C++ Example</link>
<link xlink:href="625f8bcb-a9bb-4534-8768-00a9bcbe7b7f">Visual J++ Example</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>