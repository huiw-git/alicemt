---
title: "CreateRecordset Method Example (VB)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - VB
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2de8fd02-0f49-4d47-8bd3-397726d1c644
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
# CreateRecordset Method Example (VB)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>You can create a <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink> object and specify the column information. You can then insert data into the <legacyBold>Recordset</legacyBold> object; the underlying rowset buffers the inserts.</para>
    <para>The following code example shows how to define a <legacyBold>Recordset</legacyBold> by using the <legacyLink xlink:href="e75240c2-b749-471e-b6ea-98cae232efbe">RDSServer.DataFactory</legacyLink> object. You can also do this with the <legacyLink xlink:href="d85ea4fc-451c-436e-97b8-58f92b149dd0">RDS.DataControl</legacyLink> object.</para>
    <code>'BeginRsDefineShapeVB
Sub Main()
    On Error GoTo ErrorHandler
    
    Dim ADF As RDSServer.DataFactory
    Dim vntRecordShape(3)
    Dim vntField1Shape(3)
    Dim vntField2Shape(3)
    Dim vntField3Shape(3)
    Dim vntField4Shape(3)
    
    Set ADF = New RDSServer.DataFactory
    
    ' For each field, specify the name,
    ' type, size, and nullability.
    
    vntField1Shape(0) = "Name"   ' Column name.
    vntField1Shape(1) = CInt(129)   ' Column type.
    vntField1Shape(2) = CInt(40)   ' Column size.
    vntField1Shape(3) = False      ' Nullable?
    
    vntField2Shape(0) = "Age"
    vntField2Shape(1) = CInt(3)
    vntField2Shape(2) = CInt(-1)
    vntField2Shape(3) = True
    
    vntField3Shape(0) = "DateOfBirth"
    vntField3Shape(1) = CInt(7)
    vntField3Shape(2) = CInt(-1)
    vntField3Shape(3) = True
    
    vntField4Shape(0) = "Balance"
    vntField4Shape(1) = CInt(6)
    vntField4Shape(2) = CInt(-1)
    vntField4Shape(3) = True
    
    ' Put all fields into an array of arrays.
    vntRecordShape(0) = vntField1Shape
    vntRecordShape(1) = vntField2Shape
    vntRecordShape(2) = vntField3Shape
    vntRecordShape(3) = vntField4Shape
    
    ' Use the RDSServer.DataFactory to create an empty
    ' recordset. It takes an array of variants where
    ' every element is itself another array of
    ' variants, one for every column required in the
    ' recordset.
    ' The elements of the inner array are the column's
    ' name, type, size, and nullability.
    '
    ' NOTE: You could just use the RDS.DataControl object
    ' instead of the RDSServer.DataFactory object. In
    ' that case, the following code would be Set NewRS
    ' = ADC1.CreateRecordset(vntRecordShape)
    Dim NewRs As ADODB.Recordset
    Set NewRs = ADF.CreateRecordSet(vntRecordShape)
    
    Dim fields(3)
    fields(0) = vntField1Shape(0)
    fields(1) = vntField2Shape(0)
    fields(2) = vntField3Shape(0)
    fields(3) = vntField4Shape(0)
    
    ' Populate the new recordset with data values.
    Dim fieldVals(3)
    
    ' Use AddNew to add the records.
    fieldVals(0) = "Joe"
    fieldVals(1) = 5
    fieldVals(2) = CDate(#1/5/1996#)
    fieldVals(3) = 123.456
    NewRs.AddNew fields, fieldVals
    
    fieldVals(0) = "Mary"
    fieldVals(1) = 6
    fieldVals(2) = CDate(#6/5/1996#)
    fieldVals(3) = 31
    NewRs.AddNew fields, fieldVals
    
    fieldVals(0) = "Alex"
    fieldVals(1) = 13
    fieldVals(2) = CDate(#1/6/1996#)
    fieldVals(3) = 34.0001
    NewRs.AddNew fields, fieldVals
    
    fieldVals(0) = "Susan"
    fieldVals(1) = 13
    fieldVals(2) = CDate(#8/6/1996#)
    fieldVals(3) = 0#
    NewRs.AddNew fields, fieldVals
    
    NewRs.MoveFirst
    
    ' Set the newly created and populated Recordset to
    ' the SourceRecordset property of the
    ' RDS.DataControl to bind to visual controls
    Dim ADC1 As RDS.DataControl
    Set ADC1 = New RDS.DataControl
    Set ADC1.SourceRecordset = NewRs

    'Clean up
    If NewRs.State = adStateOpen Then NewRs.Close
    Set NewRs = Nothing
    Set ADC1 = Nothing
    Set ADF = Nothing
    Exit Sub
    
ErrorHandler:
    ' clean up
    If Not NewRs Is Nothing Then
        If NewRs.State = adStateOpen Then NewRs.Close
    End If
    Set NewRs = Nothing
    Set ADC1 = Nothing
    Set ADF = Nothing
    
    If Err &lt;&gt; 0 Then
        MsgBox Err.Source &amp; "--&gt;" &amp; Err.Description, , "Error"
    End If
End Sub
'EndRsDefineShapeVB</code>
  </introduction>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>