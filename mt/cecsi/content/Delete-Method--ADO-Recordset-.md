---
title: "Delete Method (ADO Recordset)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: 1eb9209c-602c-4507-b0c2-6527a599b67d
caps.latest.revision: 13
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
# Delete Method (ADO Recordset)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Deletes the current record or a group of records.</para>
  </introduction>
  <syntaxSection>
    <legacySyntax>
<parameterReference>recordset</parameterReference>.<legacyBold>Delete </legacyBold><parameterReference>AffectRecords</parameterReference></legacySyntax>
  </syntaxSection>
  <parameters>
    <content>
      <definitionTable>
        <definedTerm> <legacyItalic>AffectRecords</legacyItalic> </definedTerm>
        <definition>
          <para>An <legacyLink xlink:href="1ab921a0-6c57-43b4-9291-701b2599f3e8">AffectEnum</legacyLink> value that determines how many records the <unmanagedCodeEntityReference>Delete</unmanagedCodeEntityReference> method will affect. The default value is <legacyBold>adAffectCurrent</legacyBold>.</para>
          <alert class="note">
            <para>
              <legacyBold>adAffectAll</legacyBold> and <legacyBold>adAffectAllChapters</legacyBold> are not valid arguments to <unmanagedCodeEntityReference>Delete</unmanagedCodeEntityReference>.</para>
          </alert>
        </definition>
      </definitionTable>
    </content>
  </parameters>
  <languageReferenceRemarks>
    <content>
      <para>Using the <unmanagedCodeEntityReference>Delete</unmanagedCodeEntityReference> method marks the current record or a group of records in a <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink> object for deletion. If the <unmanagedCodeEntityReference>Recordset</unmanagedCodeEntityReference> object doesn't allow record deletion, an error occurs. If you are in immediate update mode, deletions occur in the database immediately. If a record cannot be successfully deleted (due to database integrity violations, for example), the record will remain in edit mode after the call to <legacyLink xlink:href="6b2a9c31-1a7e-40db-8a53-30720d0f6cc1">Update</legacyLink>. This means that you must cancel the update with <legacyLink xlink:href="eaa856cc-c786-462e-890c-c896261b1741">CancelUpdate</legacyLink> before moving off the current record (for example, with <legacyLink xlink:href="3cdf27d1-a180-4cff-8e42-95dec5fb1b55">Close</legacyLink>, <legacyLink xlink:href="13fe9381-d00b-4f4a-9162-83c3f21b3837">Move</legacyLink>, or <legacyLink xlink:href="ab1fa449-a695-4987-b1ee-bc68f89418dd">NextRecordset</legacyLink>).</para>
      <para>If you are in batch update mode, the records are marked for deletion from the cache and the actual deletion happens when you call the <legacyLink xlink:href="23f9314c-b027-4a51-aeae-50caa2977740">UpdateBatch</legacyLink> method. Use the <legacyLink xlink:href="80263a7a-5d21-45d1-84fc-34b7a9be4c22">Filter</legacyLink> property to view the deleted records.</para>
      <para>Retrieving field values from the deleted record generates an error. After deleting the current record, the deleted record remains current until you move to a different record. Once you move away from the deleted record, it is no longer accessible.</para>
      <para>If you nest deletions in a transaction, you can recover deleted records with the <legacyLink xlink:href="d4683472-4120-4236-8640-fa9ae289e23e">RollbackTrans</legacyLink> method. If you are in batch update mode, you can cancel a pending deletion or group of pending deletions with the <legacyLink xlink:href="dbdc2574-e44e-4d95-b03d-4a5d9e9adf3c">CancelBatch</legacyLink> method.</para>
      <para>If the attempt to delete records fails because of a conflict with the underlying data (for example, a record has already been deleted by another user), the provider returns warnings to the <legacyLink xlink:href="290819e1-7b39-4e1e-a93b-801257138b00">Errors</legacyLink> collection but does not halt program execution. A run-time error occurs only if there are conflicts on all the requested records.</para>
      <para>If the <legacyLink xlink:href="d0e775d8-e353-46a1-ad10-ed4cc240dfaa">Unique Table</legacyLink> dynamic property is set, and the <unmanagedCodeEntityReference>Recordset</unmanagedCodeEntityReference> is the result of executing a JOIN operation on multiple tables, then the <unmanagedCodeEntityReference>Delete</unmanagedCodeEntityReference> method will only delete rows from the table named in the <legacyLink xlink:href="d0e775d8-e353-46a1-ad10-ed4cc240dfaa">Unique Table</legacyLink> property.</para>
    </content>
  </languageReferenceRemarks>
  <section>
    <title>Applies To</title>
    <content>
      <para>
        <link xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset Object</link>
      </para>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="0c80e71b-9e3f-4d05-ab2a-9e78798dad88">Visual Basic Example</link>
<link xlink:href="78935d6d-1c1a-4306-a83a-1763210c69f9">VBScript Example</link>
<link xlink:href="7cc78fb5-2701-49dc-bc22-06613b10cecb">Visual C++ Example</link>
<link xlink:href="838c4bcb-bd78-4c98-a3ac-b8bf6e750db2">Visual J++ Example</link>
<link xlink:href="25bedc25-c51c-4cab-96ce-930b959965d9">Delete Method (ADO Fields Collection)</link>
<link xlink:href="160c575e-df63-4ade-a2d3-5fd8f72e70cc">Delete Method (ADO Parameters Collection)</link>
<link xlink:href="2726498c-dbd8-4266-983b-ae7d62c39142">DeleteRecord Method</link>
</relatedTopics>
</developerReferenceWithSyntaxDocument>