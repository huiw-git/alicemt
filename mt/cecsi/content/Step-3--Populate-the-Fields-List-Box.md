---
title: "Step 3: Populate the Fields List Box"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 315c32dc-aeb1-4629-b30e-87b44e8f84d1
caps.latest.revision: 4
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
# Step 3: Populate the Fields List Box
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>To populate the Fields list box, insert the following code into the Click event handler of <codeInline>lstMain</codeInline>:</para>
    <code>Private Sub lstMain_Click()
    Dim rec As Record
    Dim rs As Recordset
    Set rec = New Record
    Set rs = New Recordset
    grs.MoveFirst
    grs.Move lstMain.ListIndex
    lstDetails.Clear
    rec.Open grs
    Select Case rec.RecordType
        Case adCollectionRecord:
            Set rs = rec.GetChildren
            While Not rs.EOF
                lstDetails.AddItem rs(0)
                rs.MoveNext
            Wend
        Case adSimpleRecord:
            recFields rec, lstDetails, txtDetails
            
        Case adStructDoc:
    End Select
    
End Sub</code>
    <para>This code declares and instantiates local Record and Recordset objects, <codeInline>rec</codeInline> and <codeInline>rs</codeInline>, respectively.</para>
    <para>The row corresponding to the resource selected in <codeInline>lstMain</codeInline> is made the current row of <codeInline>grs</codeInline>. Then the Details list box is cleared and <codeInline>rec</codeInline> is opened with the current row of <codeInline>grs</codeInline> as the source.</para>
    <para>If the resource is a collection record, as specified by <legacyLink xlink:href="790e46a2-13d2-451e-a8be-130bd9a206a4">RecordType</legacyLink>, the local Recordset <codeInline>rs</codeInline> is opened on the children of rec. Then <codeInline>lstDetails</codeInline> is filled with the values from the rows of <codeInline>rs</codeInline>.</para>
    <para>If the resource is a simple record, <codeInline>recFields</codeInline> is called. For more information about <codeInline>recFields</codeInline>, see the next step.</para>
    <para>No code is implemented if the resource is a structured document.</para>
  </introduction>
  <relatedTopics>
<link xlink:href="2f551969-0fd9-41ee-b81d-100975a4bdc2">Internet Publishing Scenario</link>
<link xlink:href="a1454493-1c86-46c2-ada8-d3c6fcdaf3c1">Step 2: Initialize the Main List Box</link>
<link xlink:href="cb4273e2-c907-4a86-a621-3bf110088228">Step 4: Populate the Details Text Box</link>
</relatedTopics>
</developerConceptualDocument>