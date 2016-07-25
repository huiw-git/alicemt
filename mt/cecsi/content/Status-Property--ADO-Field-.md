---
title: "Status Property (ADO Field)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: 8cd1f7f4-0a3a-4f07-b8ba-6582e70140ad
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
# Status Property (ADO Field)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Indicates the status of a <legacyLink xlink:href="b10a72fc-3c4b-4186-a70b-993dc9f7a092">Field</legacyLink> object.</para>
  </introduction>
  <section>
    <title>Return Value</title>
    <content>
      <para>Returns a <legacyLink xlink:href="e06da1e2-303f-41b2-a3b0-61e233da152c">FieldStatusEnum</legacyLink> value. The default value is <legacyBold>adFieldOK</legacyBold>.</para>
    </content>
  </section>
  <languageReferenceRemarks>
    <content />
    <sections>
      <section>
        <title>Record Field Status</title>
        <content>
          <para>Changes to the value of a <legacyBold>Field</legacyBold> object in the Fields collection of a <legacyLink xlink:href="db83ed2c-a8e3-460c-8682-64667e4d5d01">Record</legacyLink> object are cached until the object's <legacyLink xlink:href="6b2a9c31-1a7e-40db-8a53-30720d0f6cc1">Update</legacyLink> method is called. At that point, if the change to the Field's value caused an error, OLE DB raises the error <legacyBold>DB_E_ERRORSOCCURRED</legacyBold> (2147749409). The Status property of any of the <legacyBold>Field</legacyBold> objects in the <legacyBold>Fields</legacyBold> collection that caused the error will contain a value from the <legacyLink xlink:href="e06da1e2-303f-41b2-a3b0-61e233da152c">FieldStatusEnum</legacyLink> describing the cause of the problem.</para>
          <para>To enhance performance, additions and deletions to the <legacyLink xlink:href="7c371474-b88f-4730-afa5-44163a0488d5">Fields</legacyLink> collections of the <legacyBold>Record</legacyBold> object are cached until the <legacyBold>Update</legacyBold> method is called, and then the changes are made in a batch optimistic update. If the <legacyBold>Update</legacyBold> method is not called, the server is not updated. If any updates fail then an OLE DB provider error (DB_E_ERRORSOCCURRED) is returned and the <legacyBold>Status</legacyBold> property indicates the combined values of the operation and error status code. For example, <legacyBold>adFieldPendingInsert</legacyBold> <legacyBold>OR</legacyBold> <legacyBold>adFieldPermissionDenied</legacyBold>. The <legacyBold>Status</legacyBold> property for each <legacyBold>Field</legacyBold> can be used to determine why the <legacyBold>Field</legacyBold> was not added, modified, or deleted.</para>
          <para>Many types of problems encountered when adding, modifying, or deleting a <legacyBold>Field</legacyBold> are reported through the <legacyBold>Status</legacyBold> property. For example, if the user deletes a <legacyBold>Field</legacyBold>, it is marked for deletion from the <legacyBold>Fields</legacyBold> collection. If the subsequent <legacyBold>Update</legacyBold> returns an error because the user tried to delete a <legacyBold>Field</legacyBold> for which they do not have permission, the <legacyBold>Field</legacyBold> will have a <legacyBold>Status</legacyBold> of <legacyBold>adFieldPermissionDenied</legacyBold> <legacyBold>OR</legacyBold> <legacyBold>adFieldPendingDelete</legacyBold>. Calling the <legacyLink xlink:href="eaa856cc-c786-462e-890c-c896261b1741">CancelUpdate</legacyLink> method restores original values and sets the <legacyBold>Status</legacyBold> to <legacyBold>adFieldOK</legacyBold>.</para>
          <para>Similarly, the <legacyBold>Update</legacyBold> method may return an error because a new <legacyBold>Field</legacyBold> was added and given an inappropriate value. In that case the new <legacyBold>Field</legacyBold> will be in the <legacyBold>Fields</legacyBold> collection and have a status of <legacyBold>adFieldPendingInsert</legacyBold> and perhaps <legacyBold>adFieldCantCreate</legacyBold> (depending upon your provider). You can supply an appropriate value for the new <legacyBold>Field</legacyBold> and call <legacyBold>Update</legacyBold> again.</para>
        </content>
      </section>
      <section>
        <title>Recordset Field Status</title>
        <content>
          <para>Changes to the value of a <legacyBold>Field</legacyBold> object in the Fields collection of either a <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink> are cached until the object's <legacyLink xlink:href="6b2a9c31-1a7e-40db-8a53-30720d0f6cc1">Update</legacyLink> method is called. At that point, if the change to the Field's value caused an error, OLE DB raises the error <legacyBold>DB_E_ERRORSOCCURRED</legacyBold> (2147749409). The Status property of any of the <legacyBold>Field</legacyBold> objects in the <legacyBold>Fields</legacyBold> collection that caused the error will contain a value from the <legacyLink xlink:href="e06da1e2-303f-41b2-a3b0-61e233da152c">FieldStatusEnum</legacyLink> describing the cause of the problem.</para>
        </content>
      </section>
    </sections>
  </languageReferenceRemarks>
  <section>
    <title>Applies To</title>
    <content>
      <para>
        <link xlink:href="b10a72fc-3c4b-4186-a70b-993dc9f7a092">Field</link>
      </para>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="fdd09b60-39c7-44be-8008-e891a031f80e">Visual Basic Example</link>
<link xlink:href="194ce221-49bd-4474-ba34-91453d329381">Visual C++ Example</link>
<link xlink:href="d35cb991-2c5b-4d91-bc07-62104242cae7">Visual J++ Example</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>