---
title: "Source Property (ADO Error)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: 4044ba15-f013-4c4c-9fe1-b4410fe9a778
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
# Source Property (ADO Error)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Indicates the name of the object or application that originally generated an error.</para>
  </introduction>
  <section>
    <title>Return Value</title>
    <content>
      <para>Returns a <languageKeyword>String</languageKeyword> value that indicates the name of an object or application.</para>
    </content>
  </section>
  <languageReferenceRemarks>
    <content>
      <para>Use the <legacyBold>Source</legacyBold> property on an <legacyLink xlink:href="a175d453-fa55-4f49-9ede-a26d83177919">Error</legacyLink> object to determine the name of the object or application that originally generated an error. This could be the object's class name or programmatic ID. For errors in ADO, the property value will be <legacyBold>ADODB.</legacyBold><legacyItalic>ObjectName</legacyItalic>, where <legacyItalic>ObjectName</legacyItalic> is the name of the object that triggered the error. For ADOX and ADO MD, the value will be <legacyBold>ADOX.</legacyBold><legacyItalic>ObjectName </legacyItalic>and <legacyBold>ADOMD.</legacyBold><legacyItalic>ObjectName, </legacyItalic>respectively.</para>
      <para>Based on the error documentation from the <legacyBold>Source</legacyBold>, <legacyLink xlink:href="f92323c5-dd11-4a63-a505-d9014a0f067f">Number</legacyLink>, and <legacyLink xlink:href="4b5d6790-6c29-42aa-bf78-d9cfb8ad7965">Description</legacyLink> properties of <legacyBold>Error</legacyBold> objects, you can write code that will handle the error appropriately.</para>
      <para>The <legacyBold>Source</legacyBold> property is read-only for <legacyBold>Error</legacyBold> objects.</para>
    </content>
  </languageReferenceRemarks>
  <section>
    <title>Applies To</title>
    <content>
      <para>
        <link xlink:href="a175d453-fa55-4f49-9ede-a26d83177919">Error</link>
      </para>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="5c728458-d85c-497c-afcf-2cfa36c3342a">Visual Basic Example</link>
<link xlink:href="5321fc0f-cd0c-4e2a-a5bc-0008fba86b59">Visual C++ Example</link>
<link xlink:href="7fd0eebc-99f4-490e-9b62-0b62b1884d6b">Visual J++ Example</link>
<link xlink:href="4b5d6790-6c29-42aa-bf78-d9cfb8ad7965">Description Property</link>
<link xlink:href="2b9ef441-993c-44d4-8f87-fac0979dac1d">HelpContext, HelpFile Properties</link>
<link xlink:href="f92323c5-dd11-4a63-a505-d9014a0f067f">Number Property</link>
<link xlink:href="2c18279e-6f35-4af0-b12e-8f1543d9ed20">Source Property (ADO Record)</link>
<link xlink:href="a05ba2c9-2821-4343-8607-4de9b764ec91">Source Property (ADO Recordset)</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>