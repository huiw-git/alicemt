---
title: "CancelUpdate Method (ADO)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: eaa856cc-c786-462e-890c-c896261b1741
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
# CancelUpdate Method (ADO)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Cancels any changes made to the current or new row of a <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink> object, or the <legacyLink xlink:href="7c371474-b88f-4730-afa5-44163a0488d5">Fields</legacyLink> collection of a <legacyLink xlink:href="db83ed2c-a8e3-460c-8682-64667e4d5d01">Record</legacyLink> object, before calling the <legacyLink xlink:href="6b2a9c31-1a7e-40db-8a53-30720d0f6cc1">Update</legacyLink> method.</para>
  </introduction>
  <syntaxSection>
    <legacySyntax>
<parameterReference>recordset</parameterReference>.<legacyBold>CancelUpdate</legacyBold><parameterReference>record.Fields</parameterReference>.<legacyBold>CancelUpdate</legacyBold></legacySyntax>
  </syntaxSection>
  <languageReferenceRemarks>
    <content />
    <sections>
      <section>
        <title>Recordset</title>
        <content>
          <para>Use the <unmanagedCodeEntityReference>CancelUpdate</unmanagedCodeEntityReference> method to cancel any changes made to the current row or to discard a newly added row. You cannot cancel changes to the current row or a new row after you call the <unmanagedCodeEntityReference>Update</unmanagedCodeEntityReference> method, unless the changes are either part of a transaction that you can roll back with the <legacyLink xlink:href="d4683472-4120-4236-8640-fa9ae289e23e">RollbackTrans</legacyLink> method, or part of a batch update. In the case of a batch update, you can cancel the <unmanagedCodeEntityReference>Update</unmanagedCodeEntityReference> with the <unmanagedCodeEntityReference>CancelUpdate</unmanagedCodeEntityReference> or <legacyLink xlink:href="dbdc2574-e44e-4d95-b03d-4a5d9e9adf3c">CancelBatch</legacyLink> method.</para>
          <para>If you are adding a new row when you call the <unmanagedCodeEntityReference>CancelUpdate</unmanagedCodeEntityReference> method, the current row becomes the row that was current before the <legacyLink xlink:href="a9f54be9-5763-45d0-a6eb-09981b03bc08">AddNew</legacyLink> call.</para>
          <para>If you are in edit mode and want to move off the current record (for example, by using the <legacyLink xlink:href="13fe9381-d00b-4f4a-9162-83c3f21b3837">Move</legacyLink>, <legacyLink xlink:href="ab1fa449-a695-4987-b1ee-bc68f89418dd">NextRecordset</legacyLink>, or <legacyLink xlink:href="3cdf27d1-a180-4cff-8e42-95dec5fb1b55">Close</legacyLink> methods), you can use <unmanagedCodeEntityReference>CancelUpdate</unmanagedCodeEntityReference> to cancel any pending changes. You may need to do this if the update cannot successfully be posted to the data source. For example, an attempted delete that fails due to referential integrity violations will leave the <unmanagedCodeEntityReference>Recordset</unmanagedCodeEntityReference> in edit mode after a call to <legacyLink xlink:href="1eb9209c-602c-4507-b0c2-6527a599b67d">Delete</legacyLink>.</para>
        </content>
      </section>
      <section>
        <title>Record</title>
        <content>
          <para>The <unmanagedCodeEntityReference>CancelUpdate</unmanagedCodeEntityReference> method cancels any pending insertions or deletions of <legacyLink xlink:href="b10a72fc-3c4b-4186-a70b-993dc9f7a092">Field</legacyLink> objects, and cancels pending updates of existing fields and restores them to their original values. The <legacyLink xlink:href="41d70d89-880f-4850-9d17-19d9790cc8eb">Status</legacyLink> property of all fields in the <unmanagedCodeEntityReference>Fields</unmanagedCodeEntityReference> collection is set to <legacyBold>adFieldOK</legacyBold>.</para>
        </content>
      </section>
    </sections>
  </languageReferenceRemarks>
  <section>
    <title>Applies To</title>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <tbody>
          <tr>
            <TD>
              <para>
                <link xlink:href="7c371474-b88f-4730-afa5-44163a0488d5">Fields</link>
              </para>
            </TD>
            <TD>
              <para>
                <link xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</link>
              </para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="55bedd08-7440-4da4-b854-4ac9ef2fdedb">Visual Basic Example</link>
<link xlink:href="cc59d23a-2f38-42f9-8b65-ed89009e87ec">Visual C++ Example</link>
<link xlink:href="f93099ae-797d-4f0d-ac28-81405b2892e1">Visual J++ Example</link>
<link xlink:href="a9f54be9-5763-45d0-a6eb-09981b03bc08">AddNew Method</link>
<link xlink:href="e0db4e15-6787-41e2-8f13-9e9b524d620a">Cancel Method</link>
<link xlink:href="560b5b3d-fba9-4275-8920-9c3e186134f7">Cancel Method (RDS)</link>
<link xlink:href="dbdc2574-e44e-4d95-b03d-4a5d9e9adf3c">CancelBatch Method</link>
<link xlink:href="76d8a6e9-bc6c-4ea0-8e7a-2bae5ed06650">CancelUpdate Method (RDS)</link>
<link xlink:href="a1b04bb2-8c8b-47f9-8477-bfd0368b6f68">EditMode Property</link>
<link xlink:href="6b2a9c31-1a7e-40db-8a53-30720d0f6cc1">Update Method</link>
</relatedTopics>
</developerReferenceWithSyntaxDocument>