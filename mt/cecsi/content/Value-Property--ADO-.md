---
title: "Value Property (ADO)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: 48919c74-86d4-462e-99b9-8854ceb8d683
caps.latest.revision: 7
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
# Value Property (ADO)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Indicates the value assigned to a <legacyLink xlink:href="b10a72fc-3c4b-4186-a70b-993dc9f7a092">Field</legacyLink>, <legacyLink xlink:href="e010e794-7f0f-4026-8b5b-37328e437d63">Parameter</legacyLink>, or <legacyLink xlink:href="b2a4767c-03c7-4935-a3bc-df3e1a38a009">Property</legacyLink> object.</para>
  </introduction>
  <section>
    <title>Settings and Return Values</title>
    <content>
      <para>Sets or returns a <legacyBold>Variant</legacyBold> value that indicates the value of the object. Default value depends on the <legacyLink xlink:href="8a4c079f-9f4f-4545-801d-85983b8db71e">Type</legacyLink> property.</para>
    </content>
  </section>
  <languageReferenceRemarks>
    <content>
      <para>Use the <legacyBold>Value</legacyBold> property to set or return data from <legacyBold>Field</legacyBold> objects, to set or return parameter values with <legacyBold>Parameter</legacyBold> objects, or to set or return property settings with <legacyBold>Property</legacyBold> objects. Whether the <legacyBold>Value</legacyBold> property is read/write or read-only depends upon numerous factors — see the respective object topics for more information.</para>
      <para>ADO allows setting and returning long binary data with the <legacyBold>Value</legacyBold> property.</para>
      <alert class="note">
        <para>For <legacyBold>Parameter </legacyBold>objects, ADO reads the <legacyBold>Value</legacyBold> property only once from the provider. If a command contains a <legacyBold>Parameter</legacyBold> whose <legacyBold>Value</legacyBold> property is empty, and you create a <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink> from the command, ensure that you first close the <legacyBold>Recordset</legacyBold> before retrieving the <legacyBold>Value</legacyBold> property. Otherwise, for some providers, the <legacyBold>Value</legacyBold> property may be empty, and won't contain the correct value.</para>
        <para>For new <legacyBold>Field</legacyBold> objects that have been appended to the <legacyLink xlink:href="7c371474-b88f-4730-afa5-44163a0488d5">Fields</legacyLink> collection of a <legacyLink xlink:href="db83ed2c-a8e3-460c-8682-64667e4d5d01">Record</legacyLink> object, the <legacyBold>Value</legacyBold> property must be set before any other <legacyBold>Field</legacyBold> properties can be specified. First, a specific value for the <legacyBold>Value</legacyBold> property must have been assigned and <legacyLink xlink:href="6b2a9c31-1a7e-40db-8a53-30720d0f6cc1">Update</legacyLink> on the <legacyBold>Fields</legacyBold> collection called. Then, other properties such as <legacyLink xlink:href="8a4c079f-9f4f-4545-801d-85983b8db71e">Type</legacyLink> or <legacyLink xlink:href="acc15d40-68a6-4ba9-85bd-12d331aecaa6">Attributes</legacyLink> can be accessed.</para>
      </alert>
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
<link xlink:href="2d4fe651-ef09-461b-8884-a70b6af4362e">Visual Basic Example</link>
<link xlink:href="2a104245-56df-44f3-b9b7-b3d18643d57b">Visual C++ Example</link>
<link xlink:href="707be908-20ef-4bd6-a12c-8dc87fadd6ed">Visual J++ Example</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>