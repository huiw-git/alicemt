---
title: "Determining Edit Mode"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4c7e010d-08cd-4e22-9b32-23c36f02f88c
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
# Determining Edit Mode
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>ADO maintains an editing buffer associated with the current record. The <legacyBold>EditMode</legacyBold> property indicates whether changes have been made to this buffer or whether a new record has been created. Use <legacyBold>EditMode</legacyBold> to determine the editing status of the current record. You can test for pending changes if an editing process has been interrupted and determine whether you need to use the <legacyBold>Update</legacyBold> or <legacyBold>CancelUpdate</legacyBold> method.</para>
    <para>         <legacyBold>EditMode</legacyBold> returns one of the <legacyBold>EditModeEnum</legacyBold> constants, which are listed in the following table.</para>
    <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
      <thead>
        <tr>
          <TD>
            <para>Constant</para>
          </TD>
          <TD>
            <para>Description</para>
          </TD>
        </tr>
      </thead>
      <tbody>
        <tr>
          <TD>
            <para>               <legacyBold>adEditNone</legacyBold>             </para>
          </TD>
          <TD>
            <para>Indicates that no editing operation is in progress.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyBold>adEditInProgress</legacyBold>             </para>
          </TD>
          <TD>
            <para>Indicates that data in the current record has been modified but not saved.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyBold>adEditAdd</legacyBold>             </para>
          </TD>
          <TD>
            <para>Indicates that the <legacyBold>AddNew</legacyBold> method has been called, and the current record in the copy buffer is a new record that has not been saved to the database.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyBold>adEditDelete</legacyBold>             </para>
          </TD>
          <TD>
            <para>Indicates that the current record has been deleted.</para>
          </TD>
        </tr>
      </tbody>
    </table>
    <para>         <legacyBold>EditMode</legacyBold> can return a valid value only if there is a current record. <legacyBold>EditMode</legacyBold> will return an error if <legacyBold>BOF</legacyBold> or <legacyBold>EOF</legacyBold> is <legacyBold>True</legacyBold> or if the current record has been deleted.</para>
  </introduction>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>