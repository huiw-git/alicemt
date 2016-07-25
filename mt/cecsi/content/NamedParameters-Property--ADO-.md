---
title: "NamedParameters Property (ADO)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: 42409387-026c-435f-a9b1-bf4167095875
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
# NamedParameters Property (ADO)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Indicates whether parameter names should be passed to the provider.</para>
  </introduction>
  <languageReferenceRemarks>
    <content>
      <para>When this property is true, ADO passes the value of the <unmanagedCodeEntityReference>Name</unmanagedCodeEntityReference> property of each parameter in the <unmanagedCodeEntityReference>Parameter</unmanagedCodeEntityReference> collection for the <legacyLink xlink:href="a02c22fb-542d-465e-a629-30fd59dcbebf">Command Object</legacyLink>. The provider uses a parameter name to match parameters in the <unmanagedCodeEntityReference>CommandText</unmanagedCodeEntityReference> or <unmanagedCodeEntityReference>CommandStream</unmanagedCodeEntityReference> properties. If this property is false (the default), parameter names are ignored and the provider uses the order of parameters to match values to parameters in the <unmanagedCodeEntityReference>CommandText</unmanagedCodeEntityReference> or <unmanagedCodeEntityReference>CommandStream</unmanagedCodeEntityReference> properties.</para>
    </content>
  </languageReferenceRemarks>
  <section>
    <title>Applies To</title>
    <content>
      <para>
        <link xlink:href="a02c22fb-542d-465e-a629-30fd59dcbebf">Command Object (ADO)</link>
      </para>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="4dd7e82a-8da5-4a4e-b439-11a29286fa0e">CommandText Property</link>
<link xlink:href="f78f61b6-87e0-48dc-961e-83d0e20da58e">CommandStream Property</link>
<link xlink:href="497cae10-3913-422a-9753-dcbb0a639b1b">Parameters Collection</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>