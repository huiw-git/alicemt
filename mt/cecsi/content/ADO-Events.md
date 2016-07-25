---
title: "ADO Events"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0ded5ad9-8f83-4224-95af-38512783b972
caps.latest.revision: 9
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
# ADO Events
<?xml version="1.0" encoding="utf-8"?>
<developerOrientationDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
      <tbody>
        <tr>
          <TD>
            <para>             <legacyLink xlink:href="ec4e4b38-e9c6-4757-b2ef-4e468ae5f1d8">BeginTransComplete</legacyLink>           </para>
          </TD>
          <TD>
            <para>Called after the <legacyBold>BeginTrans</legacyBold> operation.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>             <legacyLink xlink:href="ec4e4b38-e9c6-4757-b2ef-4e468ae5f1d8">CommitTransComplete</legacyLink>           </para>
          </TD>
          <TD>
            <para>Called after the <legacyBold>CommitTrans</legacyBold> operation.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>             <legacyLink xlink:href="568f5252-d069-4d99-a01b-2ada87ad1304">ConnectComplete</legacyLink>           </para>
          </TD>
          <TD>
            <para>Called after a connection starts.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>             <legacyLink xlink:href="568f5252-d069-4d99-a01b-2ada87ad1304">Disconnect</legacyLink>           </para>
          </TD>
          <TD>
            <para>Called after a connection ends.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>             <legacyLink xlink:href="475de5e2-f634-4954-9edf-0027a6ba38d6">EndOfRecordset</legacyLink>           </para>
          </TD>
          <TD>
            <para>Called when there is an attempt to move to a row past the end of the <legacyBold>Recordset</legacyBold>.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>             <legacyLink xlink:href="62470d42-e511-494c-bec4-ad4591734b7b">ExecuteComplete</legacyLink>           </para>
          </TD>
          <TD>
            <para>Called after a command has finished executing.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>             <legacyLink xlink:href="a28d3858-566c-468d-b070-d1de4339fbea">FetchComplete</legacyLink>           </para>
          </TD>
          <TD>
            <para>Called after all the records in a lengthy asynchronous operation have been retrieved into the <legacyBold>Recordset</legacyBold>.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>             <legacyLink xlink:href="301716fd-81fc-40eb-8a04-221ef7ab410e">FetchProgress</legacyLink>           </para>
          </TD>
          <TD>
            <para>Called periodically during a lengthy asynchronous operation to report how many rows have currently been retrieved into the <legacyBold>Recordset</legacyBold>.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>             <legacyLink xlink:href="3e49fb89-c45b-4d39-823e-3cc887c59b37">FieldChangeComplete</legacyLink>           </para>
          </TD>
          <TD>
            <para>Called after the value of one or more <legacyBold>Field</legacyBold> objects has changed.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>             <legacyLink xlink:href="468c87dd-e3bc-4084-9941-94d10743d4e9">InfoMessage</legacyLink>           </para>
          </TD>
          <TD>
            <para>Called whenever a warning occurs during a <legacyBold>ConnectionEvent</legacyBold> operation.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>             <legacyLink xlink:href="1a3d1042-4f30-4526-a0c7-853c242496db">MoveComplete</legacyLink>           </para>
          </TD>
          <TD>
            <para>Called after the current position in the <legacyBold>Recordset</legacyBold> changes.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>             <legacyLink xlink:href="cbc369fd-63af-4a7d-96ae-efa91b78ca69">RecordChangeComplete</legacyLink>           </para>
          </TD>
          <TD>
            <para>Called after one or more records change.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>             <legacyLink xlink:href="d5d44659-e0d9-46d9-a297-99c43555082f">RecordsetChangeComplete</legacyLink>           </para>
          </TD>
          <TD>
            <para>Called after the <legacyBold>Recordset</legacyBold> has changed.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>             <legacyLink xlink:href="ec4e4b38-e9c6-4757-b2ef-4e468ae5f1d8">RollbackTransComplete</legacyLink>           </para>
          </TD>
          <TD>
            <para>Called after the <legacyBold>RollbackTrans</legacyBold> operation.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>             <legacyLink xlink:href="3e49fb89-c45b-4d39-823e-3cc887c59b37">WillChangeField</legacyLink>           </para>
          </TD>
          <TD>
            <para>Called before a pending operation changes the value of one or more <legacyBold>Field</legacyBold> objects in the <legacyBold>Recordset</legacyBold>.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>             <legacyLink xlink:href="cbc369fd-63af-4a7d-96ae-efa91b78ca69">WillChangeRecord</legacyLink>           </para>
          </TD>
          <TD>
            <para>Called before one or more records (rows) in the <legacyBold>Recordset</legacyBold> change.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>             <legacyLink xlink:href="d5d44659-e0d9-46d9-a297-99c43555082f">WillChangeRecordset</legacyLink>           </para>
          </TD>
          <TD>
            <para>Called before a pending operation changes the <legacyBold>Recordset</legacyBold>.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>             <legacyLink xlink:href="da561d58-eb58-446c-a4fd-1838c76073c0">WillConnect</legacyLink>           </para>
          </TD>
          <TD>
            <para>Called before a connection starts.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>             <legacyLink xlink:href="dd755e46-f589-48a3-93a9-51ff998d44b5">WillExecute</legacyLink>           </para>
          </TD>
          <TD>
            <para>Called just before a pending command executes on this connection and affords the user an opportunity to examine and modify the pending execution parameters.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>             <legacyLink xlink:href="1a3d1042-4f30-4526-a0c7-853c242496db">WillMove</legacyLink>           </para>
          </TD>
          <TD>
            <para>The <legacyBold>WillMove</legacyBold> event is called <legacyItalic>before</legacyItalic> a pending operation changes the current position in the <legacyBold>Recordset</legacyBold>.</para>
          </TD>
        </tr>
      </tbody>
    </table>
  </introduction>
  <relatedTopics>
<link xlink:href="bfd96a4b-c913-45aa-9e4c-ec86ac364f3a">ADO API Reference</link>
<link xlink:href="b5e1d26d-b41d-4e35-8c7c-972426473dfb">ADO Collections</link>
<link xlink:href="d7b06d72-f792-4328-93a2-5006b9e2c581">ADO Dynamic Properties</link>
<link xlink:href="c97ed131-1a93-463c-9e61-22f029b0c474">ADO Enumerated Constants</link>
<link xlink:href="0ce201c3-6657-4c87-ae81-0d7dc5b5a431">ADO Errors</link>
<link xlink:href="e9003457-0762-48b3-942f-0820266b158f">ADO Event Model, Synchronous and Asynchronous Operations</link>
<link xlink:href="a38c5670-ba28-44f3-bd5b-fcb46880e904">ADO Methods</link>
<link xlink:href="4aca9838-1ec6-4084-bd63-dc2d17d8ab7d">ADO Object Model</link>
<link xlink:href="d0b7e254-c89f-4406-b846-a060ef038c30">ADO Objects</link>
<link xlink:href="0ac0d1a7-6c7a-4f4c-b115-428935e0f98b">ADO Properties</link>
</relatedTopics>
</developerOrientationDocument>