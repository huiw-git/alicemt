---
title: "CompareEnum"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: bc8f710d-0621-4673-8d8e-0361e44abed0
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
# CompareEnum
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Specifies the relative position of two records represented by their bookmarks.</para>
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
              <legacyBold>adCompareEqual</legacyBold>
            </para>
          </TD>
          <TD>
            <para>1</para>
          </TD>
          <TD>
            <para>Indicates that the bookmarks are equal.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adCompareGreaterThan</legacyBold>
            </para>
          </TD>
          <TD>
            <para>2</para>
          </TD>
          <TD>
            <para>Indicates that the first bookmark is after the second.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adCompareLessThan</legacyBold>
            </para>
          </TD>
          <TD>
            <para>0</para>
          </TD>
          <TD>
            <para>Indicates that the first bookmark is before the second.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adCompareNotComparable</legacyBold>
            </para>
          </TD>
          <TD>
            <para>4</para>
          </TD>
          <TD>
            <para>Indicates that the bookmarks cannot be compared.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adCompareNotEqual</legacyBold>
            </para>
          </TD>
          <TD>
            <para>3</para>
          </TD>
          <TD>
            <para>Indicates that the bookmarks are not equal and not ordered.</para>
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
              <para>AdoEnums.Compare.EQUAL</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.Compare.GREATERTHAN</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.Compare.LESSTHAN</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.Compare.NOTCOMPARABLE</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.Compare.NOTEQUAL</para>
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
        <link xlink:href="d0b64286-2cc4-4a22-8f1d-9aefeebbcbc6">CompareBookmarks Method (ADO)</link>
      </para>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="d0b64286-2cc4-4a22-8f1d-9aefeebbcbc6">CompareBookmarks Method</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>