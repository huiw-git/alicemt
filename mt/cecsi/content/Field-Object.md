---
title: "Field Object"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: b10a72fc-3c4b-4186-a70b-993dc9f7a092
caps.latest.revision: 8
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
# Field Object
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Represents a column of data with a common data type.</para>
  </introduction>
  <languageReferenceRemarks>
    <content>
      <para>Each <legacyBold>Field</legacyBold> object corresponds to a column in the <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink>. You use the <legacyLink xlink:href="48919c74-86d4-462e-99b9-8854ceb8d683">Value</legacyLink> property of <legacyBold>Field</legacyBold> objects to set or return data for the current record. Depending on the functionality the provider exposes, some collections, methods, or properties of a <legacyBold>Field</legacyBold> object may not be available.</para>
      <para>With the collections, methods, and properties of a <legacyBold>Field</legacyBold> object, you can do the following:

</para>
      <list class="bullet">
        <listItem>
          <para>Return the name of a field with the <legacyLink xlink:href="cfd0e29c-8310-44ab-85c3-5761184b865d">Name</legacyLink> property.</para>
        </listItem>
        <listItem>
          <para>View or change the data in the field with the <legacyBold>Value</legacyBold> property. <legacyBold>Value</legacyBold> is the default property of the <legacyBold>Field</legacyBold> object.</para>
        </listItem>
        <listItem>
          <para>Return the basic characteristics of a field with the <legacyLink xlink:href="8a4c079f-9f4f-4545-801d-85983b8db71e">Type</legacyLink>, <legacyLink xlink:href="1fa38e78-6b5b-414d-ba0a-3dd26b29b766">Precision</legacyLink>, and <legacyLink xlink:href="29a02992-64be-4fcd-be13-445cba205893">NumericScale</legacyLink> properties.</para>
        </listItem>
        <listItem>
          <para>Return the declared size of a field with the <legacyLink xlink:href="3ee27314-a305-4fbc-8433-9ee9a909afd6">DefinedSize</legacyLink> property.</para>
        </listItem>
        <listItem>
          <para>Return the actual size of the data in a given field with the <legacyLink xlink:href="722803d0-cef5-4d4c-b79d-3f2f58052229">ActualSize</legacyLink> property.</para>
        </listItem>
        <listItem>
          <para>Determine what types of functionality are supported for a given field with the <legacyLink xlink:href="acc15d40-68a6-4ba9-85bd-12d331aecaa6">Attributes</legacyLink> property and <legacyLink xlink:href="1d539aa8-ce0d-4418-ab03-8d0a3c1e9d82">Properties</legacyLink> collection.</para>
        </listItem>
        <listItem>
          <para>Manipulate the values of fields containing long binary or long character data with the <legacyLink xlink:href="c648b5a8-d4f1-4d16-836e-3957feb03617">AppendChunk</legacyLink> and <legacyLink xlink:href="fc268e22-205b-44a3-9038-ffed51e23e10">GetChunk</legacyLink> methods.</para>
        </listItem>
        <listItem>
          <para>If the provider supports batch updates, resolve discrepancies in field values during batch updating with the <legacyLink xlink:href="6e33c6ec-14d9-4b1d-ba9b-cb99862e7bac">OriginalValue</legacyLink> and <legacyLink xlink:href="00a0c8b8-8b63-433f-95b8-020ab05874a0">UnderlyingValue</legacyLink> properties.</para>
        </listItem>
      </list>
      <para>All of the metadata properties (<legacyBold>Name</legacyBold>, <legacyBold>Type</legacyBold>, <legacyBold>DefinedSize</legacyBold>, <legacyBold>Precision</legacyBold>, and <legacyBold>NumericScale</legacyBold>) are available before opening the <legacyBold>Field</legacyBold> object's <legacyBold>Recordset</legacyBold>. Setting them at that time is useful for dynamically constructing forms.</para>
      <para>This section contains the following topic.

</para>
      <list class="bullet">
        <listItem>
          <para>
            <legacyLink xlink:href="1e0fc395-14f3-499a-9309-701e9905729f">Field Object Properties, Methods, and Events</legacyLink>
          </para>
        </listItem>
      </list>
    </content>
  </languageReferenceRemarks>
  <relatedTopics>
<link xlink:href="7c371474-b88f-4730-afa5-44163a0488d5">Fields Collection</link>
<link xlink:href="1d539aa8-ce0d-4418-ab03-8d0a3c1e9d82">Properties Collection</link>
<link xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset Object</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>