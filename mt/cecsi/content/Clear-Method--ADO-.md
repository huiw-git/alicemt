---
title: "Clear Method (ADO)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: 0a61ba7a-20b8-426a-91a0-9040e7c5a98a
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
# Clear Method (ADO)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Removes all the <legacyLink xlink:href="a175d453-fa55-4f49-9ede-a26d83177919">Error</legacyLink> objects from the <legacyLink xlink:href="290819e1-7b39-4e1e-a93b-801257138b00">Errors</legacyLink> collection.</para>
  </introduction>
  <syntaxSection>
    <legacySyntax>
<parameterReference>Errors.</parameterReference><legacyBold>Clear</legacyBold></legacySyntax>
  </syntaxSection>
  <languageReferenceRemarks>
    <content>
      <para>Use the <unmanagedCodeEntityReference>Clear</unmanagedCodeEntityReference> method on the <legacyLink xlink:href="290819e1-7b39-4e1e-a93b-801257138b00">Errors</legacyLink> collection to remove all existing <legacyLink xlink:href="a175d453-fa55-4f49-9ede-a26d83177919">Error</legacyLink> objects from the collection. When an error occurs, ADO automatically clears the <unmanagedCodeEntityReference>Errors</unmanagedCodeEntityReference> collection and fills it with <unmanagedCodeEntityReference>Error</unmanagedCodeEntityReference> objects based on the new error.</para>
      <para>Some properties and methods return warnings that appear as <unmanagedCodeEntityReference>Error</unmanagedCodeEntityReference> objects in the <unmanagedCodeEntityReference>Errors</unmanagedCodeEntityReference> collection but do not halt a program's execution. Before you call the <legacyLink xlink:href="73b355d4-a4c0-434b-bfc4-039b1c76b32e">Resync</legacyLink>, <legacyLink xlink:href="23f9314c-b027-4a51-aeae-50caa2977740">UpdateBatch</legacyLink>, or <legacyLink xlink:href="dbdc2574-e44e-4d95-b03d-4a5d9e9adf3c">CancelBatch</legacyLink> methods on a <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink> object; the <legacyLink xlink:href="663defab-5545-4973-9036-24d5882c9737">Open</legacyLink> method on a <legacyLink xlink:href="ef6b1824-5b12-43db-89d7-8f3d13896d4d">Connection</legacyLink> object; or set the <legacyLink xlink:href="80263a7a-5d21-45d1-84fc-34b7a9be4c22">Filter</legacyLink> property on a <unmanagedCodeEntityReference>Recordset</unmanagedCodeEntityReference> object, call the <unmanagedCodeEntityReference>Clear</unmanagedCodeEntityReference> method on the <unmanagedCodeEntityReference>Errors</unmanagedCodeEntityReference> collection. That way, you can read the <legacyLink xlink:href="da9ccd1f-d402-41a2-940c-45556fc5340d">Count</legacyLink> property of the <unmanagedCodeEntityReference>Errors</unmanagedCodeEntityReference> collection to test for returned warnings.</para>
    </content>
  </languageReferenceRemarks>
  <section>
    <title>Applies To</title>
    <content>
      <para>
        <link xlink:href="290819e1-7b39-4e1e-a93b-801257138b00">Errors</link>
      </para>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="ed5e1b60-3769-4b26-a253-1d721e37941d">Visual Basic Example</link>
<link xlink:href="3a7bbf07-2fca-4892-95f4-eec93f2d5e91">VBScript Example</link>
<link xlink:href="ada6acc1-82eb-4cfa-8f2f-617a916ffd8d">Visual C++ Example</link>
<link xlink:href="3c92cb19-c13b-4bb3-b4cd-75dc8f42057c">Visual J++ Example</link>
<link xlink:href="dbdc2574-e44e-4d95-b03d-4a5d9e9adf3c">CancelBatch Method</link>
<link xlink:href="25bedc25-c51c-4cab-96ce-930b959965d9">Delete Method (ADO Fields Collection)</link>
<link xlink:href="160c575e-df63-4ade-a2d3-5fd8f72e70cc">Delete Method (ADO Parameters Collection)</link>
<link xlink:href="1eb9209c-602c-4507-b0c2-6527a599b67d">Delete Method (ADO Recordset)</link>
<link xlink:href="80263a7a-5d21-45d1-84fc-34b7a9be4c22">Filter Property</link>
<link xlink:href="73b355d4-a4c0-434b-bfc4-039b1c76b32e">Resync Method</link>
<link xlink:href="23f9314c-b027-4a51-aeae-50caa2977740">UpdateBatch Method</link>
</relatedTopics>
</developerReferenceWithSyntaxDocument>