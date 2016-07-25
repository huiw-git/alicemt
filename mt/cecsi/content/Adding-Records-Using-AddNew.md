---
title: "Adding Records Using AddNew"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: cab4adff-f22f-4fb1-9217-f8138c795268
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
# Adding Records Using AddNew
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This is the basic syntax of the <legacyBold>AddNew</legacyBold> method:</para>
    <para>
      <legacyItalic>recordset</legacyItalic>.AddNew <legacyItalic>FieldList</legacyItalic>, <legacyItalic>Values</legacyItalic></para>
    <para>The <legacyItalic>FieldList</legacyItalic> and <legacyItalic>Values</legacyItalic> arguments are optional. <legacyItalic>FieldList</legacyItalic> is either a single name or an array of names or ordinal positions of the fields in the new record.</para>
    <para>The <legacyItalic>Values</legacyItalic> argument is either a single value or an array of values for the fields in the new record.</para>
    <para>Typically, when you intend to add a single record, you will call the <legacyBold>AddNew</legacyBold> method without any arguments. Specifically, you will call <legacyBold>AddNew</legacyBold>; set the <legacyBold>Value</legacyBold> of each field in the new record; and then call <legacyBold>Update</legacyBold> or <legacyBold>UpdateBatch</legacyBold>, or both. You can make sure that your <legacyBold>Recordset</legacyBold> supports adding new records by using the <legacyBold>Supports</legacyBold> property with the <legacyBold>adAddNew</legacyBold> enumerated constant. </para>
    <para>The following code uses this technique to add a new Shipper to the sample <legacyBold>Recordset</legacyBold>. SQL Server supplies the ShipperID field value automatically. Therefore, the code does not try to supply a field value for the new records.</para>
    <code>    'BeginAddNew1.1
    If objRs.Supports(adAddNew) Then
        With objRs
            .AddNew
            .Fields("CompanyName") = "Sample Shipper"
            .Fields("Phone") = "(931) 555-6334"
            .Update
        End With
    End If
    'EndAddNew1.1</code>
  </introduction>
  <languageReferenceRemarks>
    <content>
      <para>Because this code uses a disconnected <legacyBold>Recordset</legacyBold> with a client-side cursor in batch mode, you must reconnect the <legacyBold>Recordset</legacyBold> to the data source with a new <legacyBold>Connection</legacyBold> object before you can call the <legacyBold>UpdateBatch</legacyBold> method to post changes to the database. This is easily done by using the new function <legacyBold>GetNewConnection</legacyBold>.</para>
    </content>
  </languageReferenceRemarks>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>