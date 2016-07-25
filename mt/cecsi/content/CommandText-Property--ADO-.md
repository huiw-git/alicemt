---
title: "CommandText Property (ADO)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: 4dd7e82a-8da5-4a4e-b439-11a29286fa0e
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
# CommandText Property (ADO)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Indicates the text of a command to be issued against a provider.</para>
  </introduction>
  <section>
    <title>Settings and Return Values</title>
    <content>
      <para>Gets or sets a <languageKeyword>String</languageKeyword> value that contains a provider command, such as an SQL statement, a table name, a relative URL, or a stored procedure call. The default is the empty string ("").</para>
    </content>
  </section>
  <languageReferenceRemarks>
    <content>
      <para>Use the <unmanagedCodeEntityReference>CommandText</unmanagedCodeEntityReference> property to set or return the text of a command represented by a <legacyLink xlink:href="a02c22fb-542d-465e-a629-30fd59dcbebf">Command</legacyLink> object. Usually this will be an SQL statement, but can also be any other type of command statement recognized by the provider, such as a stored procedure call. An SQL statement must be of the particular dialect or version supported by the provider's query processor.</para>
      <para>If the <legacyLink xlink:href="11ca8825-765e-4bb4-a6ce-3f6564ad8755">Prepared</legacyLink> property of the <unmanagedCodeEntityReference>Command</unmanagedCodeEntityReference> object is set to <languageKeyword>True</languageKeyword> and the <unmanagedCodeEntityReference>Command</unmanagedCodeEntityReference> object is bound to an open connection when you set the <unmanagedCodeEntityReference>CommandText</unmanagedCodeEntityReference> property, ADO prepares the query (that is, a compiled form of the query that is stored by the provider) when you call the <legacyLink xlink:href="f84a5ff3-0528-4ad7-9bea-9a15103378dd">Execute</legacyLink> or <legacyLink xlink:href="663defab-5545-4973-9036-24d5882c9737">Open</legacyLink> methods.</para>
      <para>Depending on the <legacyLink xlink:href="ca44809c-8647-48b6-a7fb-0be70a02f53e">CommandType</legacyLink> property setting, ADO may alter the <unmanagedCodeEntityReference>CommandText</unmanagedCodeEntityReference> property. You can read the <unmanagedCodeEntityReference>CommandText</unmanagedCodeEntityReference> property at any time to see the actual command text that ADO will use during execution.</para>
      <para>Use the <unmanagedCodeEntityReference>CommandText</unmanagedCodeEntityReference> property to set or return a relative URL that specifies a resource, such as a file or directory. The resource is relative to a location specified explicitly by an absolute URL, or implicitly by an open <legacyLink xlink:href="ef6b1824-5b12-43db-89d7-8f3d13896d4d">Connection</legacyLink> object.</para>
      <alert class="note">
        <para>URLs using the http scheme will automatically invoke the <legacyLink xlink:href="66a208d9-b580-4655-a41e-1d36e5b5bfca">Microsoft OLE DB Provider for Internet Publishing</legacyLink>. For more information, see <legacyLink xlink:href="6a34a7ef-50cc-4c3d-82f7-106b9a8f3caf">Absolute and Relative URLs</legacyLink>.</para>
      </alert>
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
<link xlink:href="d81ab76f-1aa8-4ccf-92ec-b65254dc3ea1">Requery Method</link>
<link xlink:href="ea74e2a3-c965-43aa-9076-26a084b48ad8">JScriptExample</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>