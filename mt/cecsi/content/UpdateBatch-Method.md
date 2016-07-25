---
title: "UpdateBatch Method"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: 23f9314c-b027-4a51-aeae-50caa2977740
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
# UpdateBatch Method
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Writes all pending batch updates to disk.</para>
  </introduction>
  <syntaxSection>
    <legacySyntax>
<parameterReference>recordset</parameterReference><legacyBold>.UpdateBatch</legacyBold> <parameterReference>AffectRecords</parameterReference>, <parameterReference>PreserveStatus</parameterReference></legacySyntax>
  </syntaxSection>
  <parameters>
    <content>
      <definitionTable>
        <definedTerm> <legacyItalic>AffectRecords</legacyItalic> </definedTerm>
        <definition>
          <para>Optional. An <legacyLink xlink:href="1ab921a0-6c57-43b4-9291-701b2599f3e8">AffectEnum</legacyLink> value that indicates how many records the <unmanagedCodeEntityReference>UpdateBatch</unmanagedCodeEntityReference> method will affect.</para>
        </definition>
        <definedTerm>
          <legacyItalic>PreserveStatus </legacyItalic>
        </definedTerm>
        <definition>
          <para>Optional. A <languageKeyword>Boolean</languageKeyword> value that specifies whether or not local changes, as indicated by the <legacyLink xlink:href="41d70d89-880f-4850-9d17-19d9790cc8eb">Status</legacyLink> property, should be committed. If this value is set to <languageKeyword>True</languageKeyword>, the <unmanagedCodeEntityReference>Status</unmanagedCodeEntityReference> property of each record remains unchanged after the update is completed.</para>
        </definition>
      </definitionTable>
    </content>
  </parameters>
  <languageReferenceRemarks>
    <content>
      <para>Use the <unmanagedCodeEntityReference>UpdateBatch</unmanagedCodeEntityReference> method when modifying a <unmanagedCodeEntityReference>Recordset</unmanagedCodeEntityReference> object in batch update mode to transmit all changes made in a <unmanagedCodeEntityReference>Recordset</unmanagedCodeEntityReference> object to the underlying database.</para>
      <para>If the <unmanagedCodeEntityReference>Recordset</unmanagedCodeEntityReference> object supports batch updating, you can cache multiple changes to one or more records locally until you call the <unmanagedCodeEntityReference>UpdateBatch</unmanagedCodeEntityReference> method. If you are editing the current record or adding a new record when you call the <unmanagedCodeEntityReference>UpdateBatch</unmanagedCodeEntityReference> method, ADO will automatically call the <legacyLink xlink:href="6b2a9c31-1a7e-40db-8a53-30720d0f6cc1">Update</legacyLink> method to save any pending changes to the current record before transmitting the batched changes to the provider. You should use batch updating with either a keyset or static cursor only.</para>
      <alert class="note">
        <para>Specifying <legacyBold>adAffectGroup</legacyBold> as the value for this parameter will result in an error when there are no visible records in the current <unmanagedCodeEntityReference>Recordset</unmanagedCodeEntityReference> (such as a filter for which no records match).</para>
      </alert>
      <para>If the attempt to transmit changes fails for any or all records because of a conflict with the underlying data (for example, a record has already been deleted by another user), the provider returns warnings to the <legacyLink xlink:href="290819e1-7b39-4e1e-a93b-801257138b00">Errors</legacyLink> collection and a run-time error occurs. Use the <legacyLink xlink:href="80263a7a-5d21-45d1-84fc-34b7a9be4c22">Filter</legacyLink> property (<legacyBold>adFilterAffectedRecords</legacyBold>) and the <legacyLink xlink:href="41d70d89-880f-4850-9d17-19d9790cc8eb">Status</legacyLink> property to locate records with conflicts.</para>
      <para>To cancel all pending batch updates, use the <legacyLink xlink:href="dbdc2574-e44e-4d95-b03d-4a5d9e9adf3c">CancelBatch</legacyLink> method.</para>
      <para>If the <legacyLink xlink:href="d0e775d8-e353-46a1-ad10-ed4cc240dfaa">Unique Table</legacyLink> and <legacyLink xlink:href="8a3bb608-66d7-4128-a3ef-84cb0556de0d">Update Resync</legacyLink> dynamic properties are set, and the <unmanagedCodeEntityReference>Recordset</unmanagedCodeEntityReference> is the result of executing a JOIN operation on multiple tables, then the execution of the <unmanagedCodeEntityReference>UpdateBatch</unmanagedCodeEntityReference> method is implicitly followed by the <legacyLink xlink:href="73b355d4-a4c0-434b-bfc4-039b1c76b32e">Resync</legacyLink> method, depending on the settings of the <legacyLink xlink:href="8a3bb608-66d7-4128-a3ef-84cb0556de0d">Update Resync</legacyLink> property.</para>
      <para>The order in which the individual updates of a batch are performed on the data source is not necessarily the same as the order in which they were performed on the local <unmanagedCodeEntityReference>Recordset</unmanagedCodeEntityReference>. Update order is dependent upon the provider. Take this into account when coding updates that are related to one another, such as foreign key constraints on an insert or update.</para>
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
<link xlink:href="8e8728aa-267f-4468-9a04-8bb29457995c">Visual J++ Example</link>
<link xlink:href="dbdc2574-e44e-4d95-b03d-4a5d9e9adf3c">CancelBatch Method</link>
<link xlink:href="0a61ba7a-20b8-426a-91a0-9040e7c5a98a">Clear Method</link>
<link xlink:href="9920c14e-033a-4de1-8149-0ce9737a3246">LockType Property</link>
<link xlink:href="6b2a9c31-1a7e-40db-8a53-30720d0f6cc1">Update Method</link>
</relatedTopics>
</developerReferenceWithSyntaxDocument>