---
title: "Prepared Property (ADO)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: 11ca8825-765e-4bb4-a6ce-3f6564ad8755
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
# Prepared Property (ADO)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Indicates whether to save a compiled version of a <legacyLink xlink:href="a02c22fb-542d-465e-a629-30fd59dcbebf">Command</legacyLink> before execution.</para>
  </introduction>
  <section>
    <title>Settings and Return Values</title>
    <content>
      <para>Sets or returns a <languageKeyword>Boolean</languageKeyword> value that, if set to <languageKeyword>True</languageKeyword>, indicates that the command should be prepared.</para>
    </content>
  </section>
  <languageReferenceRemarks>
    <content>
      <para>Use the <unmanagedCodeEntityReference>Prepared</unmanagedCodeEntityReference> property to have the provider save a prepared (or compiled) version of the query specified in the <legacyLink xlink:href="4dd7e82a-8da5-4a4e-b439-11a29286fa0e">CommandText</legacyLink> property before a <legacyLink xlink:href="a02c22fb-542d-465e-a629-30fd59dcbebf">Command</legacyLink> object's first execution. This may slow a command's first execution, but once the provider compiles a command, the provider will use the compiled version of the command for any subsequent executions, which will result in improved performance.</para>
      <para>If the property is <languageKeyword>False</languageKeyword>, the provider will execute the <unmanagedCodeEntityReference>Command</unmanagedCodeEntityReference> object directly without creating a compiled version.</para>
      <para>If the provider does not support command preparation, it may return an error when this property is set to <languageKeyword>True</languageKeyword>. If the provider does not return an error, it simply ignores the request to prepare the command and sets the <unmanagedCodeEntityReference>Prepared</unmanagedCodeEntityReference> property to <languageKeyword>False</languageKeyword>.</para>
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
<link xlink:href="e3a3db2d-7f73-4288-ad08-5468f251d610">Visual Basic Example</link>
<link xlink:href="f697ac1a-f125-42b5-bbf6-762a7fa30ae3">Visual C++ Example</link>
<link xlink:href="fc52ea7c-1b3b-4874-9db9-4d2e01d794c3">Visual J++ Example</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>