---
title: "CommandType Property (ADO)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: ca44809c-8647-48b6-a7fb-0be70a02f53e
caps.latest.revision: 11
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
# CommandType Property (ADO)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Indicates the type of a <legacyLink xlink:href="a02c22fb-542d-465e-a629-30fd59dcbebf">Command</legacyLink> object.</para>
  </introduction>
  <section>
    <title>Settings and Return Values</title>
    <content>
      <para>Sets or returns one or more <legacyLink xlink:href="4b1feb9c-a855-40fe-a906-efe688687e9f">CommandTypeEnum</legacyLink> values.</para>
      <alert class="note">
        <para>Do not use the <unmanagedCodeEntityReference>CommandTypeEnum</unmanagedCodeEntityReference> values of <legacyBold>adCmdFile</legacyBold> or <legacyBold>adCmdTableDirect</legacyBold> with <unmanagedCodeEntityReference>CommandType</unmanagedCodeEntityReference>. These values can only be used as options with the <legacyLink xlink:href="3236749c-4b71-4235-89e2-ccdfaaa9319d">Open</legacyLink> and <legacyLink xlink:href="d81ab76f-1aa8-4ccf-92ec-b65254dc3ea1">Requery</legacyLink> methods of a <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink>.</para>
      </alert>
    </content>
  </section>
  <languageReferenceRemarks>
    <content>
      <para>Use the <unmanagedCodeEntityReference>CommandType</unmanagedCodeEntityReference> property to optimize evaluation of the <legacyLink xlink:href="4dd7e82a-8da5-4a4e-b439-11a29286fa0e">CommandText</legacyLink> property.</para>
      <para>If the <unmanagedCodeEntityReference>CommandType</unmanagedCodeEntityReference> property value is set to the default value, <legacyBold>adCmdUnknown</legacyBold>, you may experience diminished performance because ADO must make calls to the provider to determine if the <unmanagedCodeEntityReference>CommandText</unmanagedCodeEntityReference> property is an SQL statement, a stored procedure, or a table name. If you know what type of command you are using, setting the <unmanagedCodeEntityReference>CommandType</unmanagedCodeEntityReference> property instructs ADO to go directly to the relevant code. If the <unmanagedCodeEntityReference>CommandType</unmanagedCodeEntityReference> property does not match the type of command in the <unmanagedCodeEntityReference>CommandText</unmanagedCodeEntityReference> property, an error occurs when you call the <legacyLink xlink:href="f84a5ff3-0528-4ad7-9bea-9a15103378dd">Execute</legacyLink> method.</para>
    </content>
  </languageReferenceRemarks>
  <section>
    <title>Applies To</title>
    <content>
      <para>
        <link xlink:href="a02c22fb-542d-465e-a629-30fd59dcbebf">Command</link>
      </para>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="dade4531-0bcc-4a52-8f86-b110ba2a3f9d">Visual Basic Example</link>
<link xlink:href="0d9917c4-9ef0-4d7a-b4ce-4f1fa6ce1817">Visual C++ Example</link>
<link xlink:href="69a4a219-8d52-401b-9e92-2ef415f68b05">Visual J++ Example</link>
<link xlink:href="ea74e2a3-c965-43aa-9076-26a084b48ad8">JScriptExample</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>