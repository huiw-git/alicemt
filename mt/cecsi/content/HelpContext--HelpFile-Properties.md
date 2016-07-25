---
title: "HelpContext, HelpFile Properties"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: 2b9ef441-993c-44d4-8f87-fac0979dac1d
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
# HelpContext, HelpFile Properties
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Indicates the Help file and topic associated with an <legacyLink xlink:href="a175d453-fa55-4f49-9ede-a26d83177919">Error</legacyLink> object.</para>
  </introduction>
  <section>
    <title>Return Values</title>
    <content>
      <list class="bullet">
        <listItem>
          <para>
            <legacyBold>HelpContextID</legacyBold>     Returns a context ID, as a <languageKeyword>Long</languageKeyword> value, for a topic in a Help file.</para>
        </listItem>
        <listItem>
          <para>
            <legacyBold>HelpFile</legacyBold>     Returns a <languageKeyword>String</languageKeyword> value that evaluates to a fully resolved path to a Help file.</para>
        </listItem>
      </list>
    </content>
  </section>
  <languageReferenceRemarks>
    <content>
      <para>If a Help file is specified in the <unmanagedCodeEntityReference>HelpFile</unmanagedCodeEntityReference> property, the <unmanagedCodeEntityReference>HelpContext</unmanagedCodeEntityReference> property is used to automatically display the Help topic it identifies. If there is no relevant help topic available, the <unmanagedCodeEntityReference>HelpContext</unmanagedCodeEntityReference> property returns zero and the <unmanagedCodeEntityReference>HelpFile</unmanagedCodeEntityReference> property returns a zero-length string ("").</para>
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
<link xlink:href="f92323c5-dd11-4a63-a505-d9014a0f067f">Number Property</link>
<link xlink:href="4044ba15-f013-4c4c-9fe1-b4410fe9a778">Source Property (ADO Error)</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>