---
title: "IsolationLevelEnum"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: 8e17a7bc-b8a3-4ae2-b6c9-ce088ad31fdf
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
# IsolationLevelEnum
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Specifies the level of transaction isolation for a <legacyLink xlink:href="ef6b1824-5b12-43db-89d7-8f3d13896d4d">Connection</legacyLink> object.</para>
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
              <legacyBold>adXactUnspecified</legacyBold>
            </para>
          </TD>
          <TD>
            <para>-1</para>
          </TD>
          <TD>
            <para>Indicates that the provider is using a different isolation level than specified, but that the level cannot be determined.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adXactChaos</legacyBold>
            </para>
          </TD>
          <TD>
            <para>16</para>
          </TD>
          <TD>
            <para>Indicates that pending changes from more highly isolated transactions cannot be overwritten.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adXactBrowse</legacyBold>
            </para>
          </TD>
          <TD>
            <para>256</para>
          </TD>
          <TD>
            <para>Indicates that from one transaction you can view uncommitted changes in other transactions.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adXactReadUncommitted</legacyBold>
            </para>
          </TD>
          <TD>
            <para>256</para>
          </TD>
          <TD>
            <para>Same as <legacyBold>adXactBrowse</legacyBold>.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adXactCursorStability</legacyBold>
            </para>
          </TD>
          <TD>
            <para>4096</para>
          </TD>
          <TD>
            <para>Indicates that from one transaction you can view changes in other transactions only after they have been committed.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adXactReadCommitted</legacyBold>
            </para>
          </TD>
          <TD>
            <para>4096</para>
          </TD>
          <TD>
            <para>Same as <legacyBold>adXactCursorStability</legacyBold>.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adXactRepeatableRead</legacyBold>
            </para>
          </TD>
          <TD>
            <para>65536</para>
          </TD>
          <TD>
            <para>Indicates that from one transaction you cannot see changes made in other transactions, but that requerying can retrieve new <legacyBold>Recordset</legacyBold> objects.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adXactIsolated</legacyBold>
            </para>
          </TD>
          <TD>
            <para>1048576</para>
          </TD>
          <TD>
            <para>Indicates that transactions are conducted in isolation of other transactions.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adXactSerializable</legacyBold>
            </para>
          </TD>
          <TD>
            <para>1048576</para>
          </TD>
          <TD>
            <para>Same as <legacyBold>adXactIsolated</legacyBold>.</para>
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
              <para>AdoEnums.IsolationLevel.UNSPECIFIED</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.IsolationLevel.CHAOS</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.IsolationLevel.BROWSE</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.IsolationLevel.READUNCOMMITTED</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.IsolationLevel.CURSORSTABILITY</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.IsolationLevel.READCOMMITTED</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.IsolationLevel.REPEATABLEREAD</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.IsolationLevel.ISOLATED</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.IsolationLevel.SERIALIZABLE</para>
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
        <link xlink:href="ea84e4b2-fbf2-4eef-b9ce-796b22e21800">IsolationLevel Property</link>
      </para>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>