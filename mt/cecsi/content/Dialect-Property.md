---
title: "Dialect Property"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: 329c3a71-ba88-4009-b04f-2f52195a5957
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
# Dialect Property
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Indicates the dialect of the <legacyLink xlink:href="4dd7e82a-8da5-4a4e-b439-11a29286fa0e">CommandText</legacyLink> or <legacyLink xlink:href="f78f61b6-87e0-48dc-961e-83d0e20da58e">CommandStream</legacyLink> properties. The dialect defines the syntax and general rules that the provider uses to parse the string or stream.</para>
  </introduction>
  <section>
    <title>Settings and Return Values</title>
    <content>
      <para>The <unmanagedCodeEntityReference>Dialect</unmanagedCodeEntityReference> property contains a valid GUID that represents the dialect of the command text or stream. The default value for this property is {C8B521FB-5CF3-11CE-ADE5-00AA0044773D}, which indicates that the provider should choose how to interpret the command text or stream.</para>
    </content>
  </section>
  <languageReferenceRemarks>
    <content>
      <para>ADO does not query the provider when the user reads the value of this property; it returns a string representation of the value currently stored in the <legacyLink xlink:href="a02c22fb-542d-465e-a629-30fd59dcbebf">Command</legacyLink> object.</para>
      <para>When the user sets the <unmanagedCodeEntityReference>Dialect</unmanagedCodeEntityReference> property, ADO validates the GUID and raises an error if the value supplied is not a valid GUID. See the documentation for your provider to determine the GUID values supported by the <unmanagedCodeEntityReference>Dialect</unmanagedCodeEntityReference> property.</para>
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
<link xlink:href="f84a5ff3-0528-4ad7-9bea-9a15103378dd">Execute Method (ADO Command)</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>