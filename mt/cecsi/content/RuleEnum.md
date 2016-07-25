---
title: "RuleEnum"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: 738fd3ff-3daf-483d-a0b9-88bef1be54c1
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
# RuleEnum
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Specifies the rule to follow when a <legacyLink xlink:href="55f116fe-4d56-4892-bffe-0cdd6fc727c9">Key</legacyLink> is deleted.</para>
  </introduction>
  <section>
    <content>
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
                <legacyBold>adRICascade</legacyBold>             </para>
            </TD>
            <TD>
              <para>1</para>
            </TD>
            <TD>
              <para>Cascade changes.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyBold>adRINone</legacyBold>             </para>
            </TD>
            <TD>
              <para>0</para>
            </TD>
            <TD>
              <para>Default. No action is taken.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyBold>adRISetDefault</legacyBold>             </para>
            </TD>
            <TD>
              <para>3</para>
            </TD>
            <TD>
              <para>Foreign key value is set to the default.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyBold>adRISetNull</legacyBold>             </para>
            </TD>
            <TD>
              <para>2</para>
            </TD>
            <TD>
              <para>Foreign key value is set to null.</para>
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
        <link xlink:href="87bd4c0a-cae3-4007-a939-4193acaa00ac">DeleteRule Property</link>
      </para>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>