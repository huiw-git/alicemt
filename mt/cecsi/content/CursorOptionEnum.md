---
title: "CursorOptionEnum"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: 4e10cda7-ce81-4466-94c2-844d38191cf1
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
# CursorOptionEnum
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Specifies what functionality the <legacyLink xlink:href="298fc41c-0b55-42fc-b373-c5133b4da6a5">Supports</legacyLink> method should test for.</para>
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
              <legacyBold>adAddNew</legacyBold>
            </para>
          </TD>
          <TD>
            <para>0x1000400</para>
          </TD>
          <TD>
            <para>Supports the <legacyLink xlink:href="a9f54be9-5763-45d0-a6eb-09981b03bc08">AddNew</legacyLink> method to add new records.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adApproxPosition</legacyBold>
            </para>
          </TD>
          <TD>
            <para>0x4000</para>
          </TD>
          <TD>
            <para>Supports the <legacyLink xlink:href="79f8ee5e-fc70-46d8-8c29-ebf943c66592">AbsolutePosition</legacyLink> and <legacyLink xlink:href="ddb58a35-ec3a-423c-a504-3c65e62c23d4">AbsolutePage</legacyLink> properties.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adBookmark</legacyBold>
            </para>
          </TD>
          <TD>
            <para>0x2000</para>
          </TD>
          <TD>
            <para>Supports the <legacyLink xlink:href="481dcc93-487b-490e-ac58-a1e9b2ebfd43">Bookmark</legacyLink> property to gain access to specific records.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adDelete</legacyBold>
            </para>
          </TD>
          <TD>
            <para>0x1000800</para>
          </TD>
          <TD>
            <para>Supports the <legacyLink xlink:href="1eb9209c-602c-4507-b0c2-6527a599b67d">Delete</legacyLink> method to delete records.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adFind</legacyBold>
            </para>
          </TD>
          <TD>
            <para>0x80000</para>
          </TD>
          <TD>
            <para>Supports the <legacyLink xlink:href="55c9810a-d8ca-46c2-a9dc-80e7ee7aa188">Find</legacyLink> method to locate a row in a <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink>.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adHoldRecords</legacyBold>
            </para>
          </TD>
          <TD>
            <para>0x100</para>
          </TD>
          <TD>
            <para>Retrieves more records or changes the next position without committing all pending changes.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adIndex</legacyBold>
            </para>
          </TD>
          <TD>
            <para>0x100000</para>
          </TD>
          <TD>
            <para>Supports the <legacyLink xlink:href="1c79e271-21ec-41a8-8163-c5e89f0001a7">Index</legacyLink> property to name an index.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adMovePrevious</legacyBold>
            </para>
          </TD>
          <TD>
            <para>0x200</para>
          </TD>
          <TD>
            <para>Supports the <legacyLink xlink:href="a61a01a7-5b33-4150-9126-21dfa63654cb">MoveFirst</legacyLink> and <legacyLink xlink:href="a61a01a7-5b33-4150-9126-21dfa63654cb">MovePrevious</legacyLink> methods, and <legacyLink xlink:href="13fe9381-d00b-4f4a-9162-83c3f21b3837">Move</legacyLink> or <legacyLink xlink:href="14b92860-4171-47d9-a413-dd60dd6a8880">GetRows</legacyLink> methods to move the current record position backward without requiring bookmarks.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adNotify</legacyBold>
            </para>
          </TD>
          <TD>
            <para>0x40000</para>
          </TD>
          <TD>
            <para>Indicates that the underlying data provider supports notifications (which determines whether <legacyBold>Recordset</legacyBold> events are supported).</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adResync</legacyBold>
            </para>
          </TD>
          <TD>
            <para>0x20000</para>
          </TD>
          <TD>
            <para>Supports the <legacyLink xlink:href="73b355d4-a4c0-434b-bfc4-039b1c76b32e">Resync</legacyLink> method to update the cursor with the data that is visible in the underlying database.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adSeek</legacyBold>
            </para>
          </TD>
          <TD>
            <para>0x200000</para>
          </TD>
          <TD>
            <para>Supports the <legacyLink xlink:href="129293d2-19d3-4940-bf64-483ee72fb4a1">Seek</legacyLink> method to locate a row in a <legacyBold>Recordset</legacyBold>.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adUpdate</legacyBold>
            </para>
          </TD>
          <TD>
            <para>0x1008000</para>
          </TD>
          <TD>
            <para>Supports the <legacyLink xlink:href="6b2a9c31-1a7e-40db-8a53-30720d0f6cc1">Update</legacyLink> method to modify existing data.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adUpdateBatch</legacyBold>
            </para>
          </TD>
          <TD>
            <para>0x10000</para>
          </TD>
          <TD>
            <para>Supports batch updating (<legacyLink xlink:href="23f9314c-b027-4a51-aeae-50caa2977740">UpdateBatch</legacyLink> and <legacyLink xlink:href="dbdc2574-e44e-4d95-b03d-4a5d9e9adf3c">CancelBatch</legacyLink> methods) to transmit groups of changes to the provider.</para>
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
              <para>AdoEnums.CursorOption.ADDNEW</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.CursorOption.APPROXPOSITION</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.CursorOption.BOOKMARK</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.CursorOption.DELETE</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.CursorOption.FIND</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.CursorOption.HOLDRECORDS</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.CursorOption.INDEX</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.CursorOption.MOVEPREVIOUS</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.CursorOption.NOTIFY </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.CursorOption.RESYNC</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.CursorOption.SEEK</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.CursorOption.UPDATE</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.CursorOption.UPDATEBATCH</para>
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
        <link xlink:href="298fc41c-0b55-42fc-b373-c5133b4da6a5">Supports Method</link>
      </para>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>