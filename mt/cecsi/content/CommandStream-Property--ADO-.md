---
title: "CommandStream Property (ADO)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: f78f61b6-87e0-48dc-961e-83d0e20da58e
caps.latest.revision: 12
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
# CommandStream Property (ADO)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Indicates the stream used as the input for a <legacyLink xlink:href="a02c22fb-542d-465e-a629-30fd59dcbebf">Command</legacyLink> object.</para>
  </introduction>
  <section>
    <title>Settings and Return Values</title>
    <content>
      <para>Sets or returns the stream used as the input for a <unmanagedCodeEntityReference>Command</unmanagedCodeEntityReference> object. The format for this stream is provider-specific; see your provider's documentation for details. This property is similar to the <legacyLink xlink:href="4dd7e82a-8da5-4a4e-b439-11a29286fa0e">CommandText</legacyLink> property, which used to specify a string for the input of a <unmanagedCodeEntityReference>Command</unmanagedCodeEntityReference>.</para>
    </content>
  </section>
  <languageReferenceRemarks>
    <content>
      <para>
        <unmanagedCodeEntityReference>CommandStream</unmanagedCodeEntityReference> and <unmanagedCodeEntityReference>CommandText</unmanagedCodeEntityReference> are mutually exclusive. When the user sets the <unmanagedCodeEntityReference>CommandStream</unmanagedCodeEntityReference> property, the <unmanagedCodeEntityReference>CommandText</unmanagedCodeEntityReference> property will be set to the empty string (""). If the user sets the <unmanagedCodeEntityReference>CommandText</unmanagedCodeEntityReference> property, the <unmanagedCodeEntityReference>CommandStream</unmanagedCodeEntityReference> property will be set to <languageKeyword>Nothing</languageKeyword>.</para>
      <para>The behaviors of the <legacyBold>Command.Parameters.Refresh</legacyBold> and <legacyBold>Command.Prepare</legacyBold> methods are defined by the provider. The values of parameters in a stream can not be refreshed.</para>
      <para>The input stream is not available to other ADO objects that return the source of a <unmanagedCodeEntityReference>Command</unmanagedCodeEntityReference>. For example, if the <legacyLink xlink:href="a05ba2c9-2821-4343-8607-4de9b764ec91">Source</legacyLink> of a <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink> is set to a <unmanagedCodeEntityReference>Command</unmanagedCodeEntityReference> object that has a stream as its input, <legacyBold>Recordset.Source</legacyBold> continues to return the <unmanagedCodeEntityReference>CommandText</unmanagedCodeEntityReference> property, which contains an empty string (""), instead of the stream contents of the <unmanagedCodeEntityReference>CommandStream</unmanagedCodeEntityReference> property.</para>
      <para>When using a command stream (as specified by <unmanagedCodeEntityReference>CommandStream</unmanagedCodeEntityReference>), the only valid <legacyLink xlink:href="4b1feb9c-a855-40fe-a906-efe688687e9f">CommandTypeEnum</legacyLink> values for the <legacyLink xlink:href="ca44809c-8647-48b6-a7fb-0be70a02f53e">CommandType</legacyLink> property are <legacyBold>adCmdText</legacyBold> and <legacyBold>adCmdUnknown</legacyBold>. Any other value causes an error.</para>
    </content>
  </languageReferenceRemarks>
  <section>
    <title>Applies To</title>
    <content>
      <para>
        <link xlink:href="a02c22fb-542d-465e-a629-30fd59dcbebf">Command Object</link>
      </para>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="4dd7e82a-8da5-4a4e-b439-11a29286fa0e">CommandText Property</link>
<link xlink:href="329c3a71-ba88-4009-b04f-2f52195a5957">Dialect Property</link>
<link xlink:href="4b1feb9c-a855-40fe-a906-efe688687e9f">CommandTypeEnum</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>