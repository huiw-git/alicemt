---
title: "CopyRecord, CopyTo, and SaveToFile Methods Example (VB)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - VB
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 61a51b74-93cd-439c-877f-f3055499d39f
caps.latest.revision: 9
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
# CopyRecord, CopyTo, and SaveToFile Methods Example (VB)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This example demonstrates how to create copies of a file using <legacyLink xlink:href="0514531f-009d-4519-abc3-d727014a39f1">Stream</legacyLink> or <legacyLink xlink:href="db83ed2c-a8e3-460c-8682-64667e4d5d01">Record</legacyLink> objects. One copy is made to a Web folder for Internet publishing. Other properties and methods shown include <legacyLink xlink:href="f6a17e8c-7a28-48d0-bded-76b9e0cf7639">Stream Type</legacyLink>, <legacyBold>Open</legacyBold>, <legacyLink xlink:href="b18d8d38-7354-4a94-b637-6ac035faa433">LoadFromFile</legacyLink>, and <legacyLink xlink:href="ab79a623-88a9-40b6-a017-a658bf19b778">Record Open</legacyLink>.</para>
    <code>'BeginCopyRecordVB

'Note:
' This sample requires that "C:\checkmrk.wmf" and
' "http://MyServer/mywmf.wmf" exist.

Option Explicit

Private Sub Form_Load()
    On Error GoTo ErrorHandler
    
    ' Declare variables
    Dim strPicturePath, strStreamPath, strStream2Path, _
        strRecordPath, strStreamURL, strRecordURL As String
    Dim objStream, objStream2 As Stream
    Dim objRecord As Record
    Dim objField As Field
    
    ' Instantiate objects
    Set objStream = New Stream
    Set objStream2 = New Stream
    Set objRecord = New Record
    
    ' Initialize path and URL strings
    strPicturePath = "C:\checkmrk.wmf"
    strStreamPath = "C:\mywmf.wmf"
    strStreamURL = "URL=http://MyServer/mywmf.wmf"
    strStream2Path = "C:\checkmrk2.wmf"
    strRecordPath = "C:\mywmf.wmf"
    strRecordURL = "http://MyServer/mywmf2.wmf"
    
    ' Load the file into the stream
    objStream.Open
    objStream.Type = adTypeBinary
    objStream.LoadFromFile (strPicturePath)
    
    ' Save the stream to a new path and filename
    objStream.SaveToFile strStreamPath, adSaveCreateOverWrite
       
    ' Copy the contents of the first stream to a second stream
    objStream2.Open
    objStream2.Type = adTypeBinary
    objStream.CopyTo objStream2
    
    ' Save the second stream to a different path
    objStream2.SaveToFile strStream2Path, adSaveCreateOverWrite
    
    ' Because strStreamPath is a Web Folder, open a Record on the URL
    objRecord.Open "", strStreamURL
    
    ' Display the Fields of the record
    For Each objField In objRecord.Fields
        Debug.Print objField.Name &amp; ": " &amp; objField.Value
    Next
    
    ' Copy the record to a new URL
    objRecord.CopyRecord "", strRecordURL, , , adCopyOverWrite
    
    ' Load each copy of the graphic into Image controls for viewing
    Image1.Picture = LoadPicture(strPicturePath)
    Image2.Picture = LoadPicture(strStreamPath)
    Image3.Picture = LoadPicture(strStream2Path)
    Image4.Picture = LoadPicture(strRecordPath)
    
    ' clean up
    objStream.Close
    objStream2.Close
    objRecord.Close
    Set objStream = Nothing
    Set objStream2 = Nothing
    Set objRecord = Nothing
    Exit Sub
    
ErrorHandler:
    ' clean up
    If Not objStream Is Nothing Then
        If objStream.State = adStateOpen Then objStream.Close
    End If
    Set objStream = Nothing
    
    If Not objStream2 Is Nothing Then
        If objStream2.State = adStateOpen Then objStream2.Close
    End If
    Set objStream2 = Nothing
    
    If Not objRecord Is Nothing Then
        If objRecord.State = adStateOpen Then objRecord.Close
    End If
    Set objRecord = Nothing
    
    If Err &lt;&gt; 0 Then
        MsgBox Err.Source &amp; "--&gt;" &amp; Err.Description, , "Error"
    End If
End Sub
'EndCopyRecordVB</code>
  </introduction>
  <relatedTopics>
<link xlink:href="b9bcf272-3c74-479f-95dd-0229a32e98fc">CopyRecord Method</link>
<link xlink:href="b4aa5714-916b-48b8-8b09-cc2708379602">CopyTo Method</link>
<link xlink:href="b18d8d38-7354-4a94-b637-6ac035faa433">LoadFromFile Method</link>
<link xlink:href="ab79a623-88a9-40b6-a017-a658bf19b778">Open Method (ADO Record)</link>
<link xlink:href="d26f48fb-904e-4932-a245-3b4332ca1600">Open Method (ADO Stream)</link>
<link xlink:href="db83ed2c-a8e3-460c-8682-64667e4d5d01">Record Object</link>
<link xlink:href="8a8594f2-422b-4d2e-94f8-7fe337445900">SaveToFile Method</link>
<link xlink:href="0514531f-009d-4519-abc3-d727014a39f1">Stream Object</link>
<link xlink:href="f6a17e8c-7a28-48d0-bded-76b9e0cf7639">Type Property (ADO Stream)</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>