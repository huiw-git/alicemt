---
title: "PropertyAttributesEnum"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: 96a01955-a6b4-4cbf-9c73-52bcd1e9fb25
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
# PropertyAttributesEnum
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Specifies the attributes of a <legacyLink xlink:href="b2a4767c-03c7-4935-a3bc-df3e1a38a009">Property</legacyLink> object.</para>
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
              <legacyBold>adPropNotSupported</legacyBold>
            </para>
          </TD>
          <TD>
            <para>0</para>
          </TD>
          <TD>
            <para>Indicates that the property is not supported by the provider.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adPropRequired</legacyBold>
            </para>
          </TD>
          <TD>
            <para>1</para>
          </TD>
          <TD>
            <para>Indicates that the user must specify a value for this property before the data source is initialized.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adPropOptional</legacyBold>
            </para>
          </TD>
          <TD>
            <para>2</para>
          </TD>
          <TD>
            <para>Indicates that the user does not need to specify a value for this property before the data source is initialized.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adPropRead</legacyBold>
            </para>
          </TD>
          <TD>
            <para>512</para>
          </TD>
          <TD>
            <para>Indicates that the user can read the property.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adPropWrite</legacyBold>
            </para>
          </TD>
          <TD>
            <para>1024</para>
          </TD>
          <TD>
            <para>Indicates that the user can set the property.</para>
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
              <para>AdoEnums.PropertyAttributes.NOTSUPPORTED</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.PropertyAttributes.REQUIRED</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.PropertyAttributes.OPTIONAL</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.PropertyAttributes.READ</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.PropertyAttributes.WRITE</para>
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
        <link xlink:href="acc15d40-68a6-4ba9-85bd-12d331aecaa6">Attributes Property</link>
      </para>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>