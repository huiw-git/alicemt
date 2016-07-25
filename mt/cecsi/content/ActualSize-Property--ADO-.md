---
title: "ActualSize Property (ADO)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: 722803d0-cef5-4d4c-b79d-3f2f58052229
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
# ActualSize Property (ADO)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Indicates the actual length of a field’s value in bytes.</para>
  </introduction>
  <section>
    <title>Settings and Return Values</title>
    <content>
      <para>Returns a <legacyBold>Long</legacyBold> value.</para>
    </content>
  </section>
  <languageReferenceRemarks>
    <content>
      <para>Use the <legacyBold>ActualSize</legacyBold> property to return the actual length of a <legacyLink xlink:href="b10a72fc-3c4b-4186-a70b-993dc9f7a092">Field</legacyLink> object's value. For all fields, the <legacyBold>ActualSize</legacyBold> property is read-only. If ADO cannot determine the length of the <legacyBold>Field</legacyBold> object's value, the <legacyBold>ActualSize</legacyBold> property returns <legacyBold>adUnknown</legacyBold>.</para>
      <para>The <legacyBold>ActualSize</legacyBold> and <legacyLink xlink:href="3ee27314-a305-4fbc-8433-9ee9a909afd6">DefinedSize</legacyLink> properties are different, as shown in the following example. A <legacyBold>Field</legacyBold> object with a declared type of <legacyBold>adVarChar</legacyBold> and a maximum length of 50 characters returns a <legacyBold>DefinedSize</legacyBold> property value of 50, but the <legacyBold>ActualSize</legacyBold> property value it returns is the length of the data stored in the field for the current record. <legacyBold>Fields</legacyBold> with a <legacyBold>DefinedSize</legacyBold> greater than 255 bytes are treated as variable length columns.</para>
    </content>
  </languageReferenceRemarks>
  <section>
    <title>Applies To</title>
    <content>
      <para>
        <link xlink:href="b10a72fc-3c4b-4186-a70b-993dc9f7a092">Field</link>
      </para>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="bff2c273-b535-4b32-83b3-0336a406859c">Visual Basic Example</link>
<link xlink:href="05f7cc97-b806-41d2-939d-a955d10844c4">Visual C++ Example</link>
<link xlink:href="2a0936e6-6452-4fef-9295-50407a13d691">Visual J++ Example</link>
<link xlink:href="3ee27314-a305-4fbc-8433-9ee9a909afd6">DefinedSize Property</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>