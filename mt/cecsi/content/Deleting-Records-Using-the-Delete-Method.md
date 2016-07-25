---
title: "Deleting Records Using the Delete Method"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: bfed5cfa-7f57-463b-9da2-0c612a079d30
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
# Deleting Records Using the Delete Method
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Using the <legacyBold>Delete</legacyBold> method marks the current record or a group of records in a <legacyBold>Recordset</legacyBold> object for deletion. If the <legacyBold>Recordset</legacyBold> object does not allow record deletion, an error occurs. If you are in immediate update mode, deletions occur in the database immediately. If a record cannot be successfully deleted (due to database integrity violations, for example), the record will remain in edit mode after the call to <legacyBold>Update. </legacyBold>This means that you must cancel the update using <legacyLink xlink:href="eaa856cc-c786-462e-890c-c896261b1741">CancelUpdate</legacyLink> before moving off the current record (for example, using <legacyLink xlink:href="3cdf27d1-a180-4cff-8e42-95dec5fb1b55">Close</legacyLink>, <legacyLink xlink:href="13fe9381-d00b-4f4a-9162-83c3f21b3837">Move</legacyLink>, or <legacyLink xlink:href="ab1fa449-a695-4987-b1ee-bc68f89418dd">NextRecordset</legacyLink>).</para>
    <para>If you are in batch update mode, the records are marked for deletion from the cache and the actual deletion happens when you call the <legacyBold>UpdateBatch</legacyBold> method. (To view the deleted records, set the <legacyBold>Filter</legacyBold> property to <legacyBold>adFilterAffectedRecords</legacyBold> after <legacyBold>Delete</legacyBold> is called.)</para>
    <para>Attempting to retrieve field values from the deleted record generates an error. After deleting the current record, the deleted record remains current until you move to a different record. Once you move away from the deleted record, it is no longer accessible.</para>
    <para>If you nest deletions in a transaction, you can recover deleted records by using the <legacyBold>RollbackTrans</legacyBold> method. If you are in batch update mode, you can cancel a pending deletion or group of pending deletions by using the <legacyBold>CancelBatch</legacyBold> method.</para>
    <para>If the attempt to delete records fails because of a conflict with the underlying data (for example, a record has already been deleted by another user), the provider returns warnings to the <legacyBold>Errors</legacyBold> collection but does not halt program execution. A run-time error occurs only if there are conflicts on all the requested records.</para>
    <para>If the <legacyBold>Unique Table</legacyBold> dynamic property is set and the <legacyBold>Recordset</legacyBold> is the result of executing a JOIN operation on multiple tables, the <legacyBold>Delete</legacyBold> method will delete rows only from the table named in the <legacyBold>Unique Table</legacyBold> property.</para>
    <para>The <legacyBold>Delete</legacyBold> method takes an optional argument that allows you to specify which records are affected by the <legacyBold>Delete</legacyBold> operation. The only valid values for this argument are either of the following ADO <legacyBold>AffectEnum</legacyBold> enumerated constants:  </para>
    <list class="bullet">
      <listItem>
        <para>             <legacyBold>adAffectCurrent   </legacyBold>Affects only the current record.</para>
      </listItem>
      <listItem>
        <para>             <legacyBold>adAffectGroup   </legacyBold>Affects only records that satisfy the current <legacyBold>Filter</legacyBold> property setting. The <legacyBold>Filter</legacyBold> property must be set to a <legacyBold>FilterGroupEnum</legacyBold> value or an array of <legacyBold>Bookmarks</legacyBold> to use this option.</para>
      </listItem>
    </list>
    <para>The following code shows an example of specifying <legacyBold>adAffectGroup</legacyBold> when calling the <legacyBold>Delete</legacyBold> method. This example adds some records to the sample <legacyBold>Recordset</legacyBold> and updates the database. Then it filters the <legacyBold>Recordset</legacyBold> using the <legacyBold>adFilterAffectedRecords</legacyBold> filter enumerated constant, which leaves only the newly added records visible in the <legacyBold>Recordset.</legacyBold> Finally, it calls the <legacyBold>Delete</legacyBold> method and specifies that all of the records that satisfy the current <legacyBold>Filter</legacyBold> property setting (the new records) should be deleted.</para>
    <code>'BeginDeleteGroup
    'add some bogus records
    With objRs
        For i = 0 To 8
            .AddNew
            .Fields("CompanyName") = "Shipper Number " &amp; i + 1
            .Fields("Phone") = "(425) 555-000" &amp; (i + 1)
            .Update
        Next i
        
        ' update
        .UpdateBatch
        
        'filter on newly added records
        .Filter = adFilterAffectedRecords
        Debug.Print "Deleting the " &amp; .RecordCount &amp; _
                    " records you just added."
        
        'delete the newly added bogus records
        .Delete adAffectGroup
        .Filter = adFilterNone
        Debug.Print .RecordCount &amp; " records remain."
    End With
'EndDeleteGroup</code>
  </introduction>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>