---
title: "SeekEnum"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: f0ec0c92-8253-47c6-9a14-e5dbccbad219
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
# SeekEnum
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Specifies the type of <legacyLink xlink:href="129293d2-19d3-4940-bf64-483ee72fb4a1">Seek</legacyLink> to execute.</para>
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
              <legacyBold>adSeekFirstEQ</legacyBold>
            </para>
          </TD>
          <TD>
            <para>1</para>
          </TD>
          <TD>
            <para>Seeks the first key equal to <legacyItalic>KeyValues</legacyItalic>.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adSeekLastEQ</legacyBold>
            </para>
          </TD>
          <TD>
            <para>2</para>
          </TD>
          <TD>
            <para>Seeks the last key equal to <legacyItalic>KeyValues</legacyItalic>.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adSeekAfterEQ</legacyBold>
            </para>
          </TD>
          <TD>
            <para>4</para>
          </TD>
          <TD>
            <para>Seeks either a key equal to <legacyItalic>KeyValues</legacyItalic> or just after where that match would have occurred.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adSeekAfter</legacyBold>
            </para>
          </TD>
          <TD>
            <para>8</para>
          </TD>
          <TD>
            <para>Seeks a key just after where a match with <legacyItalic>KeyValues </legacyItalic>would have occurred.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adSeekBeforeEQ</legacyBold>
            </para>
          </TD>
          <TD>
            <para>16</para>
          </TD>
          <TD>
            <para>Seeks either a key equal to <legacyItalic>KeyValues</legacyItalic>or just before where that match would have occurred.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adSeekBefore</legacyBold>
            </para>
          </TD>
          <TD>
            <para>32</para>
          </TD>
          <TD>
            <para>Seeks a key just before where a match with <legacyItalic>KeyValues </legacyItalic>would have occurred.</para>
          </TD>
        </tr>
      </tbody>
    </table>
  </introduction>
  <section>
    <title>ADO/WFC Equivalent</title>
    <content>
      <para>Package: <legacyBold>com.ms.wfc.data</legacyBold></para>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>Constant</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>AdoEnums.Seek.FIRSTEQ</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.Seek.LASTEQ</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.Seek.AFTEREQ</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.Seek.AFTER</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.Seek.BEFOREEQ</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.Seek.BEFORE</para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <section>
    <title>Applies To</title>
    <content>
      <para>
        <link xlink:href="129293d2-19d3-4940-bf64-483ee72fb4a1">Seek Method</link>
      </para>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>