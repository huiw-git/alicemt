---
title: "ObjectStateEnum"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: 32746558-097b-4749-989e-519aadf7e3f4
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
# ObjectStateEnum
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Specifies whether an object is open or closed, connecting to a data source, executing a command, or retrieving data.</para>
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
              <legacyBold>adStateClosed</legacyBold>
            </para>
          </TD>
          <TD>
            <para>0</para>
          </TD>
          <TD>
            <para>Indicates that the object is closed.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adStateOpen</legacyBold>
            </para>
          </TD>
          <TD>
            <para>1</para>
          </TD>
          <TD>
            <para>Indicates that the object is open.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adStateConnecting</legacyBold>
            </para>
          </TD>
          <TD>
            <para>2</para>
          </TD>
          <TD>
            <para>Indicates that the object is connecting.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adStateExecuting</legacyBold>
            </para>
          </TD>
          <TD>
            <para>4</para>
          </TD>
          <TD>
            <para>Indicates that the object is executing a command.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adStateFetching</legacyBold>
            </para>
          </TD>
          <TD>
            <para>8</para>
          </TD>
          <TD>
            <para>Indicates that the rows of the object are being retrieved.</para>
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
              <para>AdoEnums.ObjectState.CLOSED</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.ObjectState.OPEN</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.ObjectState.CONNECTING</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.ObjectState.EXECUTING</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.ObjectState.FETCHING</para>
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
                <link xlink:href="06d480ca-9eb6-4570-a45d-a73539bddd32">State Property</link>
              </para>
            </TD>
            <TD>
              <para>
                <link xlink:href="0b993bac-2653-40b1-bcbb-5b57b6aae2bf">State Property</link>
              </para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>