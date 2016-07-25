---
title: "ParameterDirectionEnum"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: c66aa6e6-d4f0-4f0f-9640-e08ae6cfdef3
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
# ParameterDirectionEnum
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Specifies whether the <legacyLink xlink:href="e010e794-7f0f-4026-8b5b-37328e437d63">Parameter</legacyLink> represents an input parameter, an output parameter, both an input and an output parameter, or the return value from a stored procedure.</para>
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
              <legacyBold>adParamInput</legacyBold>
            </para>
          </TD>
          <TD>
            <para>1</para>
          </TD>
          <TD>
            <para>Default. Indicates that the parameter represents an input parameter.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adParamInputOutput</legacyBold>
            </para>
          </TD>
          <TD>
            <para>3</para>
          </TD>
          <TD>
            <para>Indicates that the parameter represents both an input and output parameter.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adParamOutput</legacyBold>
            </para>
          </TD>
          <TD>
            <para>2</para>
          </TD>
          <TD>
            <para>Indicates that the parameter represents an output parameter. </para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adParamReturnValue</legacyBold>
            </para>
          </TD>
          <TD>
            <para>4</para>
          </TD>
          <TD>
            <para>Indicates that the parameter represents a return value.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adParamUnknown</legacyBold>
            </para>
          </TD>
          <TD>
            <para>0</para>
          </TD>
          <TD>
            <para>Indicates that the parameter direction is unknown.</para>
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
              <para>AdoEnums.ParameterDirection.INPUT</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.ParameterDirection.INPUTOUTPUT</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.ParameterDirection.OUTPUT</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.ParameterDirection.RETURNVALUE</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.ParameterDirection.UNKNOWN</para>
            </TD>
          </tr>
        </tbody>
      </table>
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
                <link xlink:href="9666fdcc-0544-4ed7-a97b-c415f2a56d7e">CreateParameter Method</link>
              </para>
            </TD>
            <TD>
              <para>
                <link xlink:href="d5732578-3434-4dcd-a9f7-db1abd1b3b94">Direction Property</link>
              </para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>