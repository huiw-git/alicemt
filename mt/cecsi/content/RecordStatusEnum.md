---
title: "RecordStatusEnum"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: 506fdd70-4452-4e83-95d5-c94311988dfa
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
# RecordStatusEnum
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Specifies the <legacyLink xlink:href="41d70d89-880f-4850-9d17-19d9790cc8eb">status</legacyLink> of a record with regard to batch updates and other bulk operations.</para>
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
              <legacyBold>adRecCanceled</legacyBold>
            </para>
          </TD>
          <TD>
            <para>0x100</para>
          </TD>
          <TD>
            <para>Indicates that the record was not saved because the operation was canceled.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adRecCantRelease</legacyBold>
            </para>
          </TD>
          <TD>
            <para>0x400</para>
          </TD>
          <TD>
            <para>Indicates that the new record was not saved because the existing record was locked.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adRecConcurrencyViolation</legacyBold>
            </para>
          </TD>
          <TD>
            <para>0x800</para>
          </TD>
          <TD>
            <para>Indicates that the record was not saved because optimistic concurrency was in use.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adRecDBDeleted</legacyBold>
            </para>
          </TD>
          <TD>
            <para>0x40000</para>
          </TD>
          <TD>
            <para>Indicates that the record has already been deleted from the data source.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adRecDeleted</legacyBold>
            </para>
          </TD>
          <TD>
            <para>0x4</para>
          </TD>
          <TD>
            <para>Indicates that the record was deleted.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adRecIntegrityViolation</legacyBold>
            </para>
          </TD>
          <TD>
            <para>0x1000</para>
          </TD>
          <TD>
            <para>Indicates that the record was not saved because the user violated integrity constraints.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adRecInvalid</legacyBold>
            </para>
          </TD>
          <TD>
            <para>0x10</para>
          </TD>
          <TD>
            <para>Indicates that the record was not saved because its bookmark is invalid.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adRecMaxChangesExceeded</legacyBold>
            </para>
          </TD>
          <TD>
            <para>0x2000</para>
          </TD>
          <TD>
            <para>Indicates that the record was not saved because there were too many pending changes.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adRecModified</legacyBold>
            </para>
          </TD>
          <TD>
            <para>0x2</para>
          </TD>
          <TD>
            <para>Indicates that the record was modified.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adRecMultipleChanges</legacyBold>
            </para>
          </TD>
          <TD>
            <para>0x40</para>
          </TD>
          <TD>
            <para>Indicates that the record was not saved because it would have affected multiple records.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adRecNew</legacyBold>
            </para>
          </TD>
          <TD>
            <para>0x1</para>
          </TD>
          <TD>
            <para>Indicates that the record is new.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adRecObjectOpen</legacyBold>
            </para>
          </TD>
          <TD>
            <para>0x4000</para>
          </TD>
          <TD>
            <para>Indicates that the record was not saved because of a conflict with an open storage object.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adRecOK</legacyBold>
            </para>
          </TD>
          <TD>
            <para>0</para>
          </TD>
          <TD>
            <para>Indicates that the record was successfully updated.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adRecOutOfMemory</legacyBold>
            </para>
          </TD>
          <TD>
            <para>0x8000</para>
          </TD>
          <TD>
            <para>Indicates that the record was not saved because the computer has run out of memory.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adRecPendingChanges</legacyBold>
            </para>
          </TD>
          <TD>
            <para>0x80</para>
          </TD>
          <TD>
            <para>Indicates that the record was not saved because it refers to a pending insert.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adRecPermissionDenied</legacyBold>
            </para>
          </TD>
          <TD>
            <para>0x10000</para>
          </TD>
          <TD>
            <para>Indicates that the record was not saved because the user has insufficient permissions.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adRecSchemaViolation</legacyBold>
            </para>
          </TD>
          <TD>
            <para>0x20000</para>
          </TD>
          <TD>
            <para>Indicates that the record was not saved because it violates the structure of the underlying database.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>
              <legacyBold>adRecUnmodified</legacyBold>
            </para>
          </TD>
          <TD>
            <para>0x8</para>
          </TD>
          <TD>
            <para>Indicates that the record was not modified.</para>
          </TD>
        </tr>
      </tbody>
    </table>
  </introduction>
  <section>
    <title>ADO/WFC Equivalent</title>
    <content>
      <para>AdoEnums.RecordStatus.</para>
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
              <para>AdoEnums.RecordStatus.CANCELED</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.RecordStatus.CANTRELEASE</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.RecordStatus.CONCURRENCYVIOLATION</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.RecordStatus.DBDELETED</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.RecordStatus.DELETED</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.RecordStatus.INTEGRITYVIOLATION</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.RecordStatus.INVALID</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.RecordStatus.MAXCHANGESEXCEEDED</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.RecordStatus.MODIFIED</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.RecordStatus.MULTIPLECHANGES</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.RecordStatus.NEW</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.RecordStatus.OBJECTOPEN</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.RecordStatus.OK</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.RecordStatus.OUTOFMEMORY</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.RecordStatus.PENDINGCHANGES</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.RecordStatus.PERMISSIONDENIED</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.RecordStatus.SCHEMAVIOLATION</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>AdoEnums.RecordStatus.UNMODIFIED</para>
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
        <link xlink:href="41d70d89-880f-4850-9d17-19d9790cc8eb">Status Property (ADO Recordset)</link>
      </para>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>