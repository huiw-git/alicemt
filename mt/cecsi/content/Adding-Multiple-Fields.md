---
title: "Adding Multiple Fields"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f3648ef4-9f36-4991-a868-83a617389844
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
# Adding Multiple Fields
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Occasionally, it might be more efficient to pass in an array of fields and their corresponding values to the <legacyBold>AddNew</legacyBold> method, rather than setting <legacyBold>Value</legacyBold> multiple times for each new field. If <legacyItalic>FieldList </legacyItalic>is an array, <legacyItalic>Values</legacyItalic> must also be an array with the same number of members; otherwise, an error occurs. The order of field names must match the order of field values in each array. The following code passes an array of fields and an array of values to the <legacyBold>AddNew</legacyBold> method.</para>
    <code>'BeginAddNew2
    Dim avarFldNames As Variant
    Dim avarFldValues As Variant
        
    avarFldNames = Array("CompanyName", "Phone")
    avarFldValues = Array("Sample Shipper 2", "(931) 555-6334")
    
    If objRs1.Supports(adAddNew) Then
        objRs1.AddNew avarFldNames, avarFldValues
    End If
    
    'Re-establish a Connection and update
    Set objRs1.ActiveConnection = GetNewConnection
    objRs1.UpdateBatch
'EndAddNew2</code>
  </introduction>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>