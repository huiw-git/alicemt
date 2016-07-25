---
title: "ConnectPromptEnum"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: 21026e24-62b7-4cc9-8aef-62c1fc6cba75
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
# ConnectPromptEnum
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Specifies whether a dialog box should be displayed to prompt for missing parameters when opening a connection to a data source.</para>
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
              <legacyBold>adPromptAlways</legacyBold> </para>
          </TD>
          <TD>
            <para>1</para>
          </TD>
          <TD>
            <para>Prompts always.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adPromptComplete</legacyBold> </para>
          </TD>
          <TD>
            <para>2</para>
          </TD>
          <TD>
            <para>Prompts if more information is required.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adPromptCompleteRequired</legacyBold> </para>
          </TD>
          <TD>
            <para>3</para>
          </TD>
          <TD>
            <para>Prompts if more information is required but optional parameters are not allowed.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adPromptNever</legacyBold>
            </para>
          </TD>
          <TD>
            <para>4</para>
          </TD>
          <TD>
            <para>Never prompts.</para>
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
              <para>AdoEnums.ConnectPrompt.ALWAYS</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.ConnectPrompt.COMPLETE</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.ConnectPrompt.COMPLETEREQUIRED</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.ConnectPrompt.NEVER</para>
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
        <link xlink:href="c4f001b5-8d16-4d39-a42e-c0e2faaaceaf">Prompt Property — Dynamic (ADO)</link>
      </para>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>