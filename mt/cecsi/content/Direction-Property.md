---
title: "Direction Property"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: d5732578-3434-4dcd-a9f7-db1abd1b3b94
caps.latest.revision: 13
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
# Direction Property
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Indicates whether the <legacyLink xlink:href="e010e794-7f0f-4026-8b5b-37328e437d63">parameter</legacyLink> represents an input parameter, an output parameter, an input and an output parameter, or if the parameter is the return value from a stored procedure.</para>
  </introduction>
  <section>
    <title>Settings and Return Values</title>
    <content>
      <para>Sets or returns a <legacyLink xlink:href="c66aa6e6-d4f0-4f0f-9640-e08ae6cfdef3">ParameterDirectionEnum</legacyLink> value.</para>
    </content>
  </section>
  <languageReferenceRemarks>
    <content>
      <para>Use the <unmanagedCodeEntityReference>Direction</unmanagedCodeEntityReference> property to specify how a parameter is passed to or from a procedure. The <unmanagedCodeEntityReference>Direction</unmanagedCodeEntityReference> property is read/write; this allows you to work with providers that don't return this information or to set this information when you don't want ADO to make an extra call to the provider to retrieve parameter information.</para>
      <para>Not all providers can determine the direction of parameters in their stored procedures. In these cases, you must set the <unmanagedCodeEntityReference>Direction</unmanagedCodeEntityReference> property before you execute the query.</para>
    </content>
  </languageReferenceRemarks>
  <section>
    <title>Applies To</title>
    <content>
      <para>
        <link xlink:href="e010e794-7f0f-4026-8b5b-37328e437d63">Parameter</link>
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