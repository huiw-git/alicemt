---
title: "CursorType Property (ADO)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: b62c66ca-58d5-430e-9257-eb38c65e48c2
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
# CursorType Property (ADO)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Indicates the type of cursor used in a <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink> object.</para>
  </introduction>
  <section>
    <title>Settings and Return Values</title>
    <content>
      <para>Sets or returns a <legacyLink xlink:href="ffc6e245-4471-42ae-84dd-e85bddfce983">CursorTypeEnum</legacyLink> value. The default value is <legacyBold>adOpenForwardOnly</legacyBold>.</para>
    </content>
  </section>
  <languageReferenceRemarks>
    <content>
      <para>Use the <legacyBold>CursorType</legacyBold> property to specify the type of cursor that should be used when opening the <legacyBold>Recordset</legacyBold> object.</para>
      <para>Only a setting of <legacyBold>adOpenStatic</legacyBold> is supported if the <legacyLink xlink:href="39c8d86e-7ee9-4182-be5e-aad5ce952f84">CursorLocation</legacyLink> property is set to <legacyBold>adUseClient</legacyBold>. If an unsupported value is set, then no error will result; the closest supported <legacyBold>CursorType</legacyBold> will be used instead.</para>
      <para>If a provider does not support the requested cursor type, it may return another cursor type. The <legacyBold>CursorType</legacyBold> property will change to match the actual cursor type in use when the <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink> object is open. To verify specific functionality of the returned cursor, use the <legacyLink xlink:href="298fc41c-0b55-42fc-b373-c5133b4da6a5">Supports</legacyLink> method. After you close the <legacyBold>Recordset</legacyBold>, the <legacyBold>CursorType</legacyBold> property reverts to its original setting.</para>
      <para>The following chart shows the provider functionality (identified by <legacyBold>Supports</legacyBold> method constants) required for each cursor type.</para>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>For a Recordset of this CursorType</para>
            </TD>
            <TD>
              <para>The Supports method must return True for all of these constants</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>
                <legacyBold>adOpenForwardOnly</legacyBold>             </para>
            </TD>
            <TD>
              <para>none</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyBold>adOpenKeyset</legacyBold>             </para>
            </TD>
            <TD>
              <para>
                <legacyBold>adBookmark</legacyBold>, <legacyBold>adHoldRecords</legacyBold>, <legacyBold>adMovePrevious</legacyBold>, <legacyBold>adResync</legacyBold></para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyBold>adOpenDynamic</legacyBold>             </para>
            </TD>
            <TD>
              <para>
                <legacyBold>adMovePrevious</legacyBold>             </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyBold>adOpenStatic</legacyBold>             </para>
            </TD>
            <TD>
              <para>
                <legacyBold>adBookmark</legacyBold>, <legacyBold>adHoldRecords</legacyBold>, <legacyBold>adMovePrevious</legacyBold>, <legacyBold>adResync</legacyBold></para>
            </TD>
          </tr>
        </tbody>
      </table>
      <alert class="note">
        <para>Although <legacyBold>Supports</legacyBold>(<legacyBold>adUpdateBatch</legacyBold>) may be true for dynamic and forward-only cursors, for batch updates you should use either a keyset or static cursor. Set the <legacyLink xlink:href="9920c14e-033a-4de1-8149-0ce9737a3246">LockType</legacyLink> property to <legacyBold>adLockBatchOptimistic</legacyBold> and the <legacyBold>CursorLocation</legacyBold> property to <legacyBold>adUseClient</legacyBold> to enable the Cursor Service for OLE DB, which is required for batch updates.</para>
      </alert>
      <para>The <legacyBold>CursorType</legacyBold> property is read/write when the <legacyBold>Recordset</legacyBold> is closed and read-only when it is open.</para>
      <alert class="note">
        <para>  <legacyBold>Remote Data Service Usage</legacyBold>   When used on a client-side <legacyBold>Recordset</legacyBold> object, the <legacyBold>CursorType</legacyBold> property can be set only to <legacyBold>adOpenStatic</legacyBold>.</para>
      </alert>
    </content>
  </languageReferenceRemarks>
  <section>
    <title>Applies To</title>
    <content>
      <para>
        <link xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</link>
      </para>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="2cb4a304-f40a-4897-8b93-82c2d8e93500">Visual Basic Example</link>
<link xlink:href="b2a80e44-03d8-426e-81b6-dd9dfc30e181">Visual C++ Example</link>
<link xlink:href="c222016e-415d-485e-86c5-e29feac4297a">Visual J++ Example</link>
<link xlink:href="298fc41c-0b55-42fc-b373-c5133b4da6a5">Supports Method</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>