---
title: "RecordCreateOptionsEnum"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: 6d746670-0850-4065-9cd4-168dea1d3ea9
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
# RecordCreateOptionsEnum
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Specifies whether an existing <legacyBold>Record</legacyBold> should be opened or a new <legacyBold>Record</legacyBold> created for the <legacyLink xlink:href="db83ed2c-a8e3-460c-8682-64667e4d5d01">Record</legacyLink> object <legacyLink xlink:href="ab79a623-88a9-40b6-a017-a658bf19b778">Open</legacyLink> method. The values can be combined with an AND operator.</para>
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
              <legacyBold>adCreateCollection</legacyBold>
            </para>
          </TD>
          <TD>
            <para>0x2000</para>
          </TD>
          <TD>
            <para>Creates a new <legacyBold>Record</legacyBold> at the node specified by <legacyItalic>Source</legacyItalic> parameter, instead of opening an existing <legacyBold>Record</legacyBold>. If the source points to an existing node, then a run-time error occurs, unless <legacyBold>adCreateCollection</legacyBold> is combined with <legacyBold>adOpenIfExists</legacyBold> or <legacyBold>adCreateOverwrite</legacyBold>.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adCreateNonCollection</legacyBold>
            </para>
          </TD>
          <TD>
            <para>0</para>
          </TD>
          <TD>
            <para>Creates a new <legacyBold>Record</legacyBold> of type <legacyLink xlink:href="f557e537-015d-4ba7-8a41-a6f00b366a91">adSimpleRecord</legacyLink>.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adCreateOverwrite</legacyBold>
            </para>
          </TD>
          <TD>
            <para>0x4000000</para>
          </TD>
          <TD>
            <para>Modifies the creation flags <legacyBold>adCreateCollection</legacyBold>, <legacyBold>adCreateNonCollection</legacyBold>, and <legacyBold>adCreateStructDoc</legacyBold>. When OR is used with this value and one of the creation flag values, if the source URL points to an existing node or <legacyBold>Record</legacyBold>, then the existing <legacyBold>Record</legacyBold> is overwritten and a new one is created in its place. This value cannot be used together with <legacyBold>adOpenIfExists</legacyBold>.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adCreateStructDoc</legacyBold>
            </para>
          </TD>
          <TD>
            <para>0x80000000</para>
          </TD>
          <TD>
            <para>Creates a new <legacyBold>Record</legacyBold> of type <legacyLink xlink:href="f557e537-015d-4ba7-8a41-a6f00b366a91">adStructDoc</legacyLink>, instead of opening an existing <legacyBold>Record</legacyBold>.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adFailIfNotExists</legacyBold>
            </para>
          </TD>
          <TD>
            <para>-1</para>
          </TD>
          <TD>
            <para>Default. Results in a run-time error if <legacyItalic>Source </legacyItalic>points to a non-existent node.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adOpenIfExists</legacyBold>
            </para>
          </TD>
          <TD>
            <para>0x2000000</para>
          </TD>
          <TD>
            <para>Modifies the creation flags <legacyBold>adCreateCollection</legacyBold>, <legacyBold>adCreateNonCollection</legacyBold>, and <legacyBold>adCreateStructDoc</legacyBold>. When OR is used with this value and one of the creation flag values, if the source URL points to an existing node or <legacyBold>Record</legacyBold> object, then the provider must open the existing <legacyBold>Record</legacyBold> instead of creating a new one. This value cannot be used together with <legacyBold>adCreateOverwrite</legacyBold>.</para>
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
        <link xlink:href="ab79a623-88a9-40b6-a017-a658bf19b778">Open Method (ADO Record)</link>
      </para>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>