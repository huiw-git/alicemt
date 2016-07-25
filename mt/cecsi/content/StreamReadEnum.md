---
title: "StreamReadEnum"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: cfa1b416-003a-436f-a21b-bd2397e54db3
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
# StreamReadEnum
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Specifies whether the whole stream or the next line should be read from a <legacyLink xlink:href="0514531f-009d-4519-abc3-d727014a39f1">Stream</legacyLink> object.</para>
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
              <legacyBold>adReadAll</legacyBold> </para>
          </TD>
          <TD>
            <para>-1</para>
          </TD>
          <TD>
            <para>Default. Reads all bytes from the stream, from the current position onwards to the <legacyLink xlink:href="57e08c5f-f3ed-4ecd-8c66-50b83b1031d1">EOS</legacyLink> marker. This is the only valid <legacyBold>StreamReadEnum</legacyBold> value with binary streams (<legacyLink xlink:href="f6a17e8c-7a28-48d0-bded-76b9e0cf7639">Type</legacyLink> is <legacyBold>adTypeBinary</legacyBold>).</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adReadLine</legacyBold> </para>
          </TD>
          <TD>
            <para>-2</para>
          </TD>
          <TD>
            <para>Reads the next line from the stream (designated by the <legacyLink xlink:href="0b20fbb8-6b83-48ec-b442-f96c8a4bafbb">LineSeparator</legacyLink> property).</para>
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
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <tbody>
          <tr>
            <TD>
              <para>
                <link xlink:href="838502de-80f1-4eeb-8838-dd3d9403e567">Read Method</link>
              </para>
            </TD>
            <TD>
              <para>
                <link xlink:href="be5a409e-cf87-4859-9ea5-713401755a77">ReadText Method</link>
              </para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>