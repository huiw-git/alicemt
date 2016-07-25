---
title: "Type Property (ADO)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: 8a4c079f-9f4f-4545-801d-85983b8db71e
caps.latest.revision: 6
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
# Type Property (ADO)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Indicates the operational type or data type of a <legacyLink xlink:href="e010e794-7f0f-4026-8b5b-37328e437d63">Parameter</legacyLink>, <legacyLink xlink:href="b10a72fc-3c4b-4186-a70b-993dc9f7a092">Field</legacyLink>, or <legacyLink xlink:href="b2a4767c-03c7-4935-a3bc-df3e1a38a009">Property</legacyLink> object.</para>
  </introduction>
  <section>
    <title>Settings and Return Values</title>
    <content>
      <para>Sets or returns a <legacyLink xlink:href="2c57eca6-9336-4b06-ba10-9fef5926b1d0">DataTypeEnum</legacyLink> value.</para>
    </content>
  </section>
  <languageReferenceRemarks>
    <content>
      <para>For <legacyBold>Parameter</legacyBold> objects, the <legacyBold>Type</legacyBold> property is read/write. For new <legacyBold>Field</legacyBold> objects that have been appended to the <legacyLink xlink:href="7c371474-b88f-4730-afa5-44163a0488d5">Fields</legacyLink> collection of a <legacyLink xlink:href="db83ed2c-a8e3-460c-8682-64667e4d5d01">Record</legacyLink>, <legacyBold>Type</legacyBold> is read/write only after the <legacyLink xlink:href="48919c74-86d4-462e-99b9-8854ceb8d683">Value</legacyLink> property for the <legacyBold>Field</legacyBold> has been specified and the data provider has successfully added the new <legacyBold>Field</legacyBold> by calling the <legacyLink xlink:href="6b2a9c31-1a7e-40db-8a53-30720d0f6cc1">Update</legacyLink> method of the <legacyBold>Fields</legacyBold> collection.</para>
      <para>For all other objects, the <legacyBold>Type</legacyBold> property is read-only.</para>
    </content>
  </languageReferenceRemarks>
  <section>
    <title>Applies To</title>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <tbody>
          <tr>
            <TD>
              <para>
                <link xlink:href="b10a72fc-3c4b-4186-a70b-993dc9f7a092">Field</link>
              </para>
            </TD>
            <TD>
              <para>
                <link xlink:href="e010e794-7f0f-4026-8b5b-37328e437d63">Parameter</link>
              </para>
            </TD>
            <TD>
              <para>
                <link xlink:href="b2a4767c-03c7-4935-a3bc-df3e1a38a009">Property</link>
              </para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="accb72f5-a3bd-4a7e-92b6-6da0783b4b75">Visual Basic Example</link>
<link xlink:href="a4e23508-fbf3-4468-be55-212e7238802b">Visual C++ Example</link>
<link xlink:href="17438bac-468c-47ff-9028-325660e1b261">Visual J++ Example</link>
<link xlink:href="790e46a2-13d2-451e-a8be-130bd9a206a4">RecordType Property</link>
<link xlink:href="f6a17e8c-7a28-48d0-bded-76b9e0cf7639">Type Property (ADO Stream)</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>