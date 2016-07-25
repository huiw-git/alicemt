---
title: "DefinedSize Property"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: 3ee27314-a305-4fbc-8433-9ee9a909afd6
caps.latest.revision: 11
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
# DefinedSize Property
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Indicates the data capacity of a <legacyLink xlink:href="b10a72fc-3c4b-4186-a70b-993dc9f7a092">Field</legacyLink> object.</para>
  </introduction>
  <section>
    <title>Return Value</title>
    <content>
      <para>Returns a <languageKeyword>Long</languageKeyword> value that reflects the defined size of a field, which depends on the data type of the field object; see <legacyLink xlink:href="8a4c079f-9f4f-4545-801d-85983b8db71e">Type</legacyLink> for more information. For a field that uses a fixed-length data type, the return value is the size of the data type in bytes. For a field that uses a variable-length data type, this is one of the following:</para>
      <list class="ordered">
        <listItem>
          <para>The maximum length of the field in characters (for <legacyBold>adVarChar</legacyBold> and <legacyBold>adVarWChar</legacyBold>) or in bytes (for <legacyBold>adVarBinary</legacyBold>, and <legacyBold>adVarNumeric</legacyBold>) if the field has a defined length. For example, <legacyBold>adVarChar(5)</legacyBold> field has a maximum length of 5.</para>
        </listItem>
        <listItem>
          <para>The maximum length of the data type in characters (for <legacyBold>adChar</legacyBold> and <legacyBold>adWChar</legacyBold>) or in bytes (for <legacyBold>adBinary</legacyBold> and <legacyBold>adNumeric</legacyBold>) if the field does not have a defined length.</para>
        </listItem>
        <listItem>
          <para>~0 (bitwise, the value is not 0; all bits are set to 1) if neither the field nor the data type has a defined maximum length.</para>
        </listItem>
        <listItem>
          <para>For data types that do not have a length, this is set to ~0 (bitwise, the value is not 0; all bits are set to 1).</para>
        </listItem>
      </list>
    </content>
  </section>
  <languageReferenceRemarks>
    <content>
      <para>Use the <legacyBold>DefinedSize</legacyBold> property to determine the data capacity of a <legacyBold>Field</legacyBold> object.</para>
      <para>The <legacyBold>DefinedSize</legacyBold> and <legacyLink xlink:href="722803d0-cef5-4d4c-b79d-3f2f58052229">ActualSize</legacyLink> properties are different. For example, consider a <legacyBold>Field</legacyBold> object with a declared type of <legacyBold>adVarChar</legacyBold> and a <legacyBold>DefinedSize</legacyBold> property value of 50, containing a single character. The <legacyBold>ActualSize</legacyBold> property value it returns is the length in bytes of the single character.</para>
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
<link xlink:href="722803d0-cef5-4d4c-b79d-3f2f58052229">ActualSize Property</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>