---
title: "Attributes Property (ADO)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: acc15d40-68a6-4ba9-85bd-12d331aecaa6
caps.latest.revision: 13
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
# Attributes Property (ADO)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Indicates one or more characteristics of an object.</para>
  </introduction>
  <section>
    <title>Settings and Return Values</title>
    <content>
      <para>Sets or returns a <languageKeyword>Long</languageKeyword> value.</para>
      <para>For a <legacyLink xlink:href="ef6b1824-5b12-43db-89d7-8f3d13896d4d">Connection</legacyLink> object, the <unmanagedCodeEntityReference>Attributes</unmanagedCodeEntityReference> property is read/write, and its value can be the sum of one or more <legacyLink xlink:href="e7dcecd3-7dc7-445c-b922-f700c3067fbc">XactAttributeEnum</legacyLink> values. The default is zero (0).</para>
      <para>For a <legacyLink xlink:href="e010e794-7f0f-4026-8b5b-37328e437d63">Parameter</legacyLink> object, the <unmanagedCodeEntityReference>Attributes</unmanagedCodeEntityReference> property is read/write, and its value can be the sum of any one or more <legacyLink xlink:href="7ef6c728-5eda-4bde-8052-02d2db1d2cfe">ParameterAttributesEnum</legacyLink> values. The default is <legacyBold>adParamSigned</legacyBold>.</para>
      <para>For a <legacyLink xlink:href="b10a72fc-3c4b-4186-a70b-993dc9f7a092">Field</legacyLink> object, the <unmanagedCodeEntityReference>Attributes</unmanagedCodeEntityReference> property can be the sum of one or more <legacyLink xlink:href="6e34d886-005a-40dc-bd5c-6adcbf81e5cd">FieldAttributeEnum</legacyLink> values. It is normally read-only. However, for new <unmanagedCodeEntityReference>Field</unmanagedCodeEntityReference> objects that have been appended to the <legacyLink xlink:href="7c371474-b88f-4730-afa5-44163a0488d5">Fields</legacyLink> collection of a <legacyLink xlink:href="db83ed2c-a8e3-460c-8682-64667e4d5d01">Record</legacyLink>, <unmanagedCodeEntityReference>Attributes</unmanagedCodeEntityReference> is read/write only after the <legacyLink xlink:href="48919c74-86d4-462e-99b9-8854ceb8d683">Value</legacyLink> property for the <unmanagedCodeEntityReference>Field</unmanagedCodeEntityReference> has been specified and the new <unmanagedCodeEntityReference>Field</unmanagedCodeEntityReference> has been successfully added by the data provider by calling the <legacyLink xlink:href="6b2a9c31-1a7e-40db-8a53-30720d0f6cc1">Update</legacyLink> method of the <unmanagedCodeEntityReference>Fields</unmanagedCodeEntityReference> collection.</para>
      <para>For a <legacyLink xlink:href="b2a4767c-03c7-4935-a3bc-df3e1a38a009">Property</legacyLink> object, the <unmanagedCodeEntityReference>Attributes</unmanagedCodeEntityReference> property is read-only, and its value can be the sum of any one or more <legacyLink xlink:href="96a01955-a6b4-4cbf-9c73-52bcd1e9fb25">PropertyAttributesEnum</legacyLink> values.</para>
    </content>
  </section>
  <languageReferenceRemarks>
    <content>
      <para>Use the <unmanagedCodeEntityReference>Attributes</unmanagedCodeEntityReference> property to set or return characteristics of <unmanagedCodeEntityReference>Connection</unmanagedCodeEntityReference> objects, <unmanagedCodeEntityReference>Parameter</unmanagedCodeEntityReference> objects, <unmanagedCodeEntityReference>Field</unmanagedCodeEntityReference> objects, or <unmanagedCodeEntityReference>Property</unmanagedCodeEntityReference> objects.</para>
      <para>When you set multiple attributes, you can sum the appropriate constants. If you set the property value to a sum including incompatible constants, an error occurs.</para>
      <alert class="note">
        <para>
          <legacyBold>Remote Data Service Usage   </legacyBold>This property is not available on a client-side <unmanagedCodeEntityReference>Connection</unmanagedCodeEntityReference> object.</para>
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
                <link xlink:href="ef6b1824-5b12-43db-89d7-8f3d13896d4d">Connection Object</link>
              </para>
            </TD>
            <TD>
              <para>
                <link xlink:href="b10a72fc-3c4b-4186-a70b-993dc9f7a092">Field Object</link>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <link xlink:href="e010e794-7f0f-4026-8b5b-37328e437d63">Parameter Object</link>
              </para>
            </TD>
            <TD>
              <para>
                <link xlink:href="b2a4767c-03c7-4935-a3bc-df3e1a38a009">Property Object</link>
              </para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="258bdce3-1819-44a2-9217-105879c789ef">Visual Basic Example</link>
<link xlink:href="2db7c9ca-d7d0-4c8e-840b-b27d7933ec40">Visual C++ Example</link>
<link xlink:href="625f8bcb-a9bb-4534-8768-00a9bcbe7b7f">Visual J++ Example</link>
<link xlink:href="c648b5a8-d4f1-4d16-836e-3957feb03617">AppendChunk Method</link>
<link xlink:href="d4683472-4120-4236-8640-fa9ae289e23e">BeginTrans, CommitTrans, and RollbackTrans Methods</link>
<link xlink:href="fc268e22-205b-44a3-9038-ffed51e23e10">GetChunk Method</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>