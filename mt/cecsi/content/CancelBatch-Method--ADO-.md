---
title: "CancelBatch Method (ADO)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: dbdc2574-e44e-4d95-b03d-4a5d9e9adf3c
caps.latest.revision: 12
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
# CancelBatch Method (ADO)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Cancels a pending batch update.</para>
  </introduction>
  <syntaxSection>
    <legacySyntax>
<parameterReference>recordset</parameterReference>.<legacyBold>CancelBatch</legacyBold><parameterReference>AffectRecords</parameterReference></legacySyntax>
  </syntaxSection>
  <parameters>
    <content>
      <definitionTable>
        <definedTerm> <legacyItalic>AffectRecords</legacyItalic> </definedTerm>
        <definition>
          <para>Optional. An <legacyLink xlink:href="1ab921a0-6c57-43b4-9291-701b2599f3e8">AffectEnum</legacyLink> value that indicates how many records the <unmanagedCodeEntityReference>CancelBatch</unmanagedCodeEntityReference> method will affect.</para>
        </definition>
      </definitionTable>
    </content>
  </parameters>
  <languageReferenceRemarks>
    <content>
      <para>Use the <unmanagedCodeEntityReference>CancelBatch</unmanagedCodeEntityReference> method to cancel any pending updates in a <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink> in batch update mode. If the <unmanagedCodeEntityReference>Recordset</unmanagedCodeEntityReference> is in immediate update mode, calling <unmanagedCodeEntityReference>CancelBatch</unmanagedCodeEntityReference> without <legacyBold>adAffectCurrent</legacyBold> generates an error.</para>
      <para>If you are editing the current record or are adding a new record when you call <unmanagedCodeEntityReference>CancelBatch</unmanagedCodeEntityReference>, ADO first calls the <legacyLink xlink:href="eaa856cc-c786-462e-890c-c896261b1741">CancelUpdate</legacyLink> method to cancel any cached changes. After that, all pending changes in the <unmanagedCodeEntityReference>Recordset</unmanagedCodeEntityReference> are canceled.</para>
      <para>The current record may be indeterminable after a <unmanagedCodeEntityReference>CancelBatch</unmanagedCodeEntityReference> call, especially if you were in the process of adding a new record. For this reason, it is prudent to set the current record position to a known location in the <unmanagedCodeEntityReference>Recordset</unmanagedCodeEntityReference> after the <unmanagedCodeEntityReference>CancelBatch</unmanagedCodeEntityReference> call. For example, call the <legacyLink xlink:href="a61a01a7-5b33-4150-9126-21dfa63654cb">MoveFirst</legacyLink> method.</para>
      <para>If the attempt to cancel the pending updates fails because of a conflict with the underlying data (for example, if a record has been deleted by another user), the provider returns warnings to the <legacyLink xlink:href="290819e1-7b39-4e1e-a93b-801257138b00">Errors</legacyLink> collection but does not halt program execution. A run-time error occurs only if there are conflicts on all the requested records. Use the <legacyLink xlink:href="80263a7a-5d21-45d1-84fc-34b7a9be4c22">Filter</legacyLink> property (<legacyBold>adFilterAffectedRecords</legacyBold>) and the <legacyLink xlink:href="41d70d89-880f-4850-9d17-19d9790cc8eb">Status</legacyLink> property to locate records with conflicts.</para>
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
<link xlink:href="41625f6f-e12d-4d8d-9f60-0729ce64c31e">Visual Basic Example</link>
<link xlink:href="bcb1468e-18bb-41b8-8902-6ee05b786eec">Visual C++ Example</link>
<link xlink:href="e0db4e15-6787-41e2-8f13-9e9b524d620a">Cancel Method</link>
<link xlink:href="560b5b3d-fba9-4275-8920-9c3e186134f7">Cancel Method (RDS)</link>
<link xlink:href="eaa856cc-c786-462e-890c-c896261b1741">CancelUpdate Method</link>
<link xlink:href="76d8a6e9-bc6c-4ea0-8e7a-2bae5ed06650">CancelUpdate Method (RDS)</link>
<link xlink:href="0a61ba7a-20b8-426a-91a0-9040e7c5a98a">Clear Method</link>
<link xlink:href="9920c14e-033a-4de1-8149-0ce9737a3246">LockType Property</link>
<link xlink:href="23f9314c-b027-4a51-aeae-50caa2977740">UpdateBatch Method</link>
</relatedTopics>
</developerReferenceWithSyntaxDocument>