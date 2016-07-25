---
title: "StreamWriteEnum"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: bdbf3405-a0bd-4f02-85d4-e3fe8da3f3f7
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
# StreamWriteEnum
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Specifies whether a line separator is appended to the string written to a <legacyLink xlink:href="0514531f-009d-4519-abc3-d727014a39f1">Stream</legacyLink> object.</para>
    <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
      <thead>
        <tr>
          <TD>
            <para>Constant</para>
          </TD>
          <TD>
            <para>Value</para>
          </TD>
          <TD>
            <para>Description</para>
          </TD>
        </tr>
      </thead>
      <tbody>
        <tr>
          <TD>
            <para>
              <legacyBold>adWriteChar</legacyBold> </para>
          </TD>
          <TD>
            <para>0</para>
          </TD>
          <TD>
            <para>Default. Writes the specified text string (specified by the <legacyItalic>Data</legacyItalic> parameter) to the <legacyBold>Stream </legacyBold>object.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adWriteLine</legacyBold> </para>
          </TD>
          <TD>
            <para>1</para>
          </TD>
          <TD>
            <para>Writes a text string and a line separator character to a <legacyBold>Stream </legacyBold>object. If the <legacyLink xlink:href="0b20fbb8-6b83-48ec-b442-f96c8a4bafbb">LineSeparator</legacyLink> property is not defined, then this returns a run-time error.</para>
          </TD>
        </tr>
      </tbody>
    </table>
  </introduction>
  <section>
    <title>ADO/WFC Equivalent</title>
    <content>
      <para>These constants do not have ADO/WFC equivalents.</para>
    </content>
  </section>
  <section>
    <title>Applies To</title>
    <content>
      <para>
        <link xlink:href="7a669048-13f4-4574-a2b1-985e089729d5">WriteText Method</link>
      </para>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>