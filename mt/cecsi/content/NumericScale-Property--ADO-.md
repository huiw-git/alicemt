---
title: "NumericScale Property (ADO)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: 29a02992-64be-4fcd-be13-445cba205893
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
# NumericScale Property (ADO)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Indicates the scale of numeric values in a <legacyLink xlink:href="e010e794-7f0f-4026-8b5b-37328e437d63">Parameter</legacyLink> or <legacyLink xlink:href="b10a72fc-3c4b-4186-a70b-993dc9f7a092">Field</legacyLink> object.</para>
  </introduction>
  <section>
    <title>Settings and Return Values</title>
    <content>
      <para>Sets or returns a <languageKeyword>Byte</languageKeyword> value that indicates the number of decimal places to which numeric values will be resolved.</para>
    </content>
  </section>
  <languageReferenceRemarks>
    <content>
      <para>Use the <unmanagedCodeEntityReference>NumericScale</unmanagedCodeEntityReference> property to determine how many digits to the right of the decimal point will be used to represent values for a numeric <unmanagedCodeEntityReference>Parameter</unmanagedCodeEntityReference> or <unmanagedCodeEntityReference>Field</unmanagedCodeEntityReference> object.</para>
      <para>For <unmanagedCodeEntityReference>Parameter</unmanagedCodeEntityReference> objects, the <unmanagedCodeEntityReference>NumericScale</unmanagedCodeEntityReference> property is read/write.</para>
      <para>For a <unmanagedCodeEntityReference>Field</unmanagedCodeEntityReference><legacyBold> </legacyBold>object, <unmanagedCodeEntityReference>NumericScale</unmanagedCodeEntityReference> is normally read-only. However, for new <unmanagedCodeEntityReference>Field</unmanagedCodeEntityReference> objects that have been appended to the <legacyLink xlink:href="7c371474-b88f-4730-afa5-44163a0488d5">Fields</legacyLink> collection of a <legacyLink xlink:href="db83ed2c-a8e3-460c-8682-64667e4d5d01">Record</legacyLink>, <unmanagedCodeEntityReference>NumericScale</unmanagedCodeEntityReference> is read/write only after the <legacyLink xlink:href="48919c74-86d4-462e-99b9-8854ceb8d683">Value</legacyLink> property for the <unmanagedCodeEntityReference>Field</unmanagedCodeEntityReference> has been specified and the data provider has successfully added the new <unmanagedCodeEntityReference>Field</unmanagedCodeEntityReference> by calling the <legacyLink xlink:href="6b2a9c31-1a7e-40db-8a53-30720d0f6cc1">Update</legacyLink> method of the <legacyLink xlink:href="7c371474-b88f-4730-afa5-44163a0488d5">Fields</legacyLink> collection.</para>
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
                <link xlink:href="e010e794-7f0f-4026-8b5b-37328e437d63">Parameter</link>
              </para>
            </TD>
            <TD>
              <para>
                <link xlink:href="b10a72fc-3c4b-4186-a70b-993dc9f7a092">Field</link>
              </para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="9c1e2322-c225-49d1-a120-a343f23cea73">Visual Basic Example</link>
<link xlink:href="55d91ba8-4d80-4df6-af8e-060a19ddc138">Visual C++ Example</link>
<link xlink:href="ca9f10d2-b5d1-449b-807b-649ef4fbf0bb">Visual J++ Example</link>
<link xlink:href="1fa38e78-6b5b-414d-ba0a-3dd26b29b766">Precision Property</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>