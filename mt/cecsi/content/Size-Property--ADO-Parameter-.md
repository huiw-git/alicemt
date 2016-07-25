---
title: "Size Property (ADO Parameter)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: e6bad449-ebdb-4dd3-886a-9e6f1e7ee5d2
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
# Size Property (ADO Parameter)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Indicates the maximum size, in bytes or characters, of a <legacyLink xlink:href="e010e794-7f0f-4026-8b5b-37328e437d63">Parameter</legacyLink> object.</para>
  </introduction>
  <section>
    <title>Settings and Return Values</title>
    <content>
      <para>Sets or returns a <languageKeyword>Long</languageKeyword> value that indicates the maximum size in bytes or characters of a value in a <legacyBold>Parameter</legacyBold> object.</para>
    </content>
  </section>
  <languageReferenceRemarks>
    <content>
      <para>Use the <legacyBold>Size</legacyBold> property to determine the maximum size for values written to or read from the <legacyLink xlink:href="48919c74-86d4-462e-99b9-8854ceb8d683">Value</legacyLink> property of a <legacyBold>Parameter</legacyBold> object.</para>
      <para>If you specify a variable-length data type for a <legacyBold>Parameter</legacyBold> object (for example, any <legacyBold>String</legacyBold> type, such as <legacyBold>adVarChar</legacyBold>), you must set the object's <legacyBold>Size</legacyBold> property before appending it to the <legacyLink xlink:href="497cae10-3913-422a-9753-dcbb0a639b1b">Parameters</legacyLink> collection; otherwise, an error occurs.</para>
      <para>If you have already appended the <legacyBold>Parameter</legacyBold> object to the <legacyBold>Parameters</legacyBold> collection of a <legacyLink xlink:href="a02c22fb-542d-465e-a629-30fd59dcbebf">Command</legacyLink> object and you change its type to a variable-length data type, you must set the <legacyBold>Parameter</legacyBold> object's <legacyBold>Size</legacyBold> property before executing the <legacyBold>Command</legacyBold> object; otherwise, an error occurs.</para>
      <para>If you use the <legacyLink xlink:href="089b7ca7-684f-4259-8032-5bd1ecc54426">Refresh</legacyLink> method to obtain parameter information from the provider and it returns one or more variable-length data type <legacyBold>Parameter</legacyBold> objects, ADO may allocate memory for the parameters based on their maximum potential size, which could cause an error during execution. To prevent an error, you should explicitly set the <legacyBold>Size</legacyBold> property for these parameters before executing the command.</para>
      <para>The <legacyBold>Size</legacyBold> property is read/write.</para>
    </content>
  </languageReferenceRemarks>
  <section>
    <title>Applies To</title>
    <content>
      <para>
        <link xlink:href="e010e794-7f0f-4026-8b5b-37328e437d63">Parameter</link>
      </para>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="dade4531-0bcc-4a52-8f86-b110ba2a3f9d">Visual Basic Example</link>
<link xlink:href="0d9917c4-9ef0-4d7a-b4ce-4f1fa6ce1817">Visual C++ Example</link>
<link xlink:href="69a4a219-8d52-401b-9e92-2ef415f68b05">Visual J++ Example</link>
<link xlink:href="ea74e2a3-c965-43aa-9076-26a084b48ad8">JScriptExample</link>
<link xlink:href="a487c241-d953-4c31-ae7e-6358d5cf6733">Size Property (ADO Stream)</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>