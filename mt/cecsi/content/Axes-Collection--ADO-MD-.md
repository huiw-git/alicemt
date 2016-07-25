---
title: "Axes Collection (ADO MD)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: 072fb21a-ec0f-4b02-9022-1cef3ad4bfff
caps.latest.revision: 9
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
# Axes Collection (ADO MD)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Contains the <legacyLink xlink:href="5f498c9a-b1e7-4e6e-9ae6-71eadaf9aada">Axis</legacyLink> objects that define a cellset.</para>
  </introduction>
  <languageReferenceRemarks>
    <content>
      <para>A <legacyLink xlink:href="5e2452c0-cac0-49b2-8099-836c35794d50">Cellset</legacyLink> object contains an <legacyBold>Axes</legacyBold> collection. Once the <legacyBold>Cellset</legacyBold> is opened, this collection will contain at least one <legacyBold>Axis</legacyBold>. See the <legacyLink xlink:href="5f498c9a-b1e7-4e6e-9ae6-71eadaf9aada">Axis</legacyLink> object for a more detailed explanation of how to use <legacyBold>Axis</legacyBold> objects.</para>
      <alert class="note">
        <para>The filter axis of a <legacyBold>Cellset</legacyBold> is not contained in the <legacyBold>Axes</legacyBold> collection. See the <legacyLink xlink:href="9c656963-531e-4cd1-b698-d5f42a9b7ba3">FilterAxis</legacyLink> property for more information.</para>
      </alert>
      <para>         <legacyBold>Axes</legacyBold> is a standard ADO collection. With the properties and methods of a collection, you can do the following:  </para>
      <list class="bullet">
        <listItem>
          <para>Obtain the number of objects in the collection with the <legacyLink xlink:href="da9ccd1f-d402-41a2-940c-45556fc5340d">Count</legacyLink> property.</para>
        </listItem>
        <listItem>
          <para>Return an object from the collection with the default <legacyLink xlink:href="e11484bb-c5c7-42d8-9bb8-21572125d727">Item</legacyLink> property.</para>
        </listItem>
        <listItem>
          <para>Update the objects in the collection from the provider with the <legacyLink xlink:href="089b7ca7-684f-4259-8032-5bd1ecc54426">Refresh</legacyLink> method.</para>
        </listItem>
      </list>
      <para>This section contains the following topic.  </para>
      <list class="bullet">
        <listItem>
          <para>
            <legacyLink xlink:href="be459530-6f28-458f-ad70-759eae3ae08c">Properties, Methods, and Events</legacyLink>           </para>
        </listItem>
      </list>
    </content>
  </languageReferenceRemarks>
  <relatedTopics>
<link xlink:href="2666ad1c-b48e-4b2c-b269-5a9f4e4a7810">Visual Basic Example</link>
<link xlink:href="5f498c9a-b1e7-4e6e-9ae6-71eadaf9aada">Axis Object</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>