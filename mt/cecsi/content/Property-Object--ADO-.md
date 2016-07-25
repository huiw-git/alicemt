---
title: "Property Object (ADO)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: b2a4767c-03c7-4935-a3bc-df3e1a38a009
caps.latest.revision: 5
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
# Property Object (ADO)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Represents a dynamic characteristic of an ADO object that is defined by the provider.</para>
  </introduction>
  <languageReferenceRemarks>
    <content>
      <para>ADO objects have two types of properties: built-in and dynamic.</para>
      <para>Built-in properties are those properties implemented in ADO and immediately available to any new object, using the <codeInline>MyObject.Property</codeInline> syntax. They do not appear as <legacyBold>Property</legacyBold> objects in an object's <legacyLink xlink:href="1d539aa8-ce0d-4418-ab03-8d0a3c1e9d82">Properties</legacyLink> collection, so although you can change their values, you cannot modify their characteristics.</para>
      <para>Dynamic properties are defined by the underlying data provider, and appear in the <legacyBold>Properties</legacyBold> collection for the appropriate ADO object. For example, a property specific to the provider may indicate if a <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink> object supports transactions or updating. These additional properties will appear as <legacyBold>Property</legacyBold> objects in that <legacyBold>Recordset</legacyBold> object's <legacyBold>Properties</legacyBold> collection. Dynamic properties can be referenced only through the collection, using the <codeInline>MyObject.Properties(0)</codeInline> or <codeInline>MyObject.Properties("Name")</codeInline> syntax.</para>
      <para>You cannot delete either kind of property.</para>
      <para>A dynamic <legacyBold>Property</legacyBold> object has four built-in properties of its own:  </para>
      <list class="bullet">
        <listItem>
          <para>The <legacyLink xlink:href="cfd0e29c-8310-44ab-85c3-5761184b865d">Name</legacyLink> property is a string that identifies the property.</para>
        </listItem>
        <listItem>
          <para>The <legacyLink xlink:href="8a4c079f-9f4f-4545-801d-85983b8db71e">Type</legacyLink> property is an integer that specifies the property data type.</para>
        </listItem>
        <listItem>
          <para>The <legacyLink xlink:href="48919c74-86d4-462e-99b9-8854ceb8d683">Value</legacyLink> property is a variant that contains the property setting. <legacyBold>Value</legacyBold> is the default property for a <legacyBold>Property</legacyBold> object.</para>
        </listItem>
        <listItem>
          <para>The <legacyLink xlink:href="acc15d40-68a6-4ba9-85bd-12d331aecaa6">Attributes</legacyLink> property is a long value that indicates characteristics of the property specific to the provider.</para>
        </listItem>
      </list>
      <para>This section contains the following topic.  </para>
      <list class="bullet">
        <listItem>
          <para>
            <legacyLink xlink:href="21f67a7d-6273-4648-9abd-2236650efa4c">Property Object Properties, Methods, and Events</legacyLink>           </para>
        </listItem>
      </list>
    </content>
  </languageReferenceRemarks>
  <relatedTopics>
<link xlink:href="a02c22fb-542d-465e-a629-30fd59dcbebf">Command Object</link>
<link xlink:href="ef6b1824-5b12-43db-89d7-8f3d13896d4d">Connection Object</link>
<link xlink:href="b10a72fc-3c4b-4186-a70b-993dc9f7a092">Field Object</link>
<link xlink:href="1d539aa8-ce0d-4418-ab03-8d0a3c1e9d82">Properties Collection</link>
<link xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset Object</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>