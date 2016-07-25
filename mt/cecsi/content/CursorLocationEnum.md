---
title: "CursorLocationEnum"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: acb255ff-1734-4b70-89bb-aef862b4c63b
caps.latest.revision: 11
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
# CursorLocationEnum
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Specifies the location of the cursor service.</para>
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
              <legacyBold>adUseClient</legacyBold>
            </para>
          </TD>
          <TD>
            <para>3</para>
          </TD>
          <TD>
            <para>Uses client-side cursors supplied by a local cursor library. Local cursor services often will allow many features that driver-supplied cursors may not, so using this setting may provide an advantage with respect to features that will be enabled. For backward compatibility, the synonym <legacyBold>adUseClientBatch</legacyBold> is also supported.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adUseNone</legacyBold>
            </para>
          </TD>
          <TD>
            <para>1</para>
          </TD>
          <TD>
            <para>Does not use cursor services. (This constant is obsolete and appears solely for the sake of backward compatibility.)</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adUseServer</legacyBold>
            </para>
          </TD>
          <TD>
            <para>2</para>
          </TD>
          <TD>
            <para>Default. Uses cursors supplied by the data provider or driver. These cursors are sometimes very flexible and allow for additional sensitivity to changes others make to the data source. However, some features of the <link xlink:href="1ac3bd9b-2d45-4cc8-88ec-bd8a218cfb49">The Microsoft Cursor Service for OLE DB</link>, such as disassociated </para>
            <para>
              <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink> objects, cannot be simulated with server-side cursors and these features will be unavailable with this setting.</para>
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
              <para>AdoEnums.CursorLocation.CLIENT</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.CursorLocation.NONE</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.CursorLocation.SERVER</para>
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
        <link xlink:href="39c8d86e-7ee9-4182-be5e-aad5ce952f84">CursorLocation Property</link>
      </para>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>