---
title: "DeleteRecord and MoveRecord Methods Example (VB)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - VB
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c3937d1e-9872-47e5-a22e-b147637f2388
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
# DeleteRecord and MoveRecord Methods Example (VB)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This example demonstrates how to copy, move, edit, and delete the contents of a text file published to a Web folder. Other properties and methods used include <legacyLink xlink:href="b3f09bac-4f66-49f6-aa5a-6fbb4fb28338">GetChildren</legacyLink>, <legacyLink xlink:href="65120ce6-3900-4cd4-b322-3b9816d74737">ParentURL</legacyLink>, <legacyLink xlink:href="2c18279e-6f35-4af0-b12e-8f1543d9ed20">Source</legacyLink>, and <legacyLink xlink:href="938522b4-f836-4c80-8d27-a598a000f0ee">Flush</legacyLink>.</para>
    <code>'BeginDeleteRecordVB

'Note:
' IIS must be running for this sample to work. To
' use this sample you must:
'
' 1. create folders named "test" and "test2"
'    in the root web folder of http://MyServer
'
' 2. Create a text file named "test2.txt" in the
'    "test" folder.
' 3. Replace "MyServer" with the appropriate web
'    server name.
    
Public Sub Main()
    On Error GoTo ErrorHandler

     ' connection and recordset variables
    Dim rsDestFolder As ADODB.Recordset
    Dim Cnxn As ADODB.Connection
    Dim strCnxn As String
 
     ' file as record variables
    Dim rcFile As ADODB.Record
    Dim rcDestFile As ADODB.Record
    Dim rcDestFolder As ADODB.Record
    Dim objStream As Stream
    
     ' file variables
    Dim strFile As String
    Dim strDestFile As String
    Dim strDestFolder As String
            
     ' instantiate variables
    Set rsDestFolder = New ADODB.Recordset
    Set rcDestFolder = New ADODB.Record
    Set rcFile = New ADODB.Record
    Set rcDestFile = New ADODB.Record
    Set objStream = New ADODB.Stream
     
     ' open a record on a text file
    Set Cnxn = New ADODB.Connection
    strCnxn = "url=http://MyServer/"
    Cnxn.Open strCnxn
    strFile = "test/test2.txt"
    rcFile.Open strFile, Cnxn, adModeReadWrite, adOpenIfExists Or adCreateNonCollection
    Debug.Print Cnxn
    
     ' edit the contents of the text file
    objStream.Open rcFile, , adOpenStreamFromRecord
    
    Debug.Print "Source: " &amp; strCnxn &amp; rcFile.Source
    Debug.Print "Original text: " &amp; objStream.ReadText
    
    objStream.Position = 0
    objStream.WriteText "Newer Text. "
    objStream.Position = 0
    
    Debug.Print "New text: " &amp; objStream.ReadText
    
     ' reset the stream object
    objStream.Flush
    objStream.Close
    rcFile.Close
    
     ' reopen record to see new contents of text file
    rcFile.Open strFile, Cnxn, adModeReadWrite, adOpenIfExists Or adCreateNonCollection
    objStream.Open rcFile, adModeReadWrite, adOpenStreamFromRecord
    
    Debug.Print "Source: " &amp; strCnxn &amp; rcFile.Source
    Debug.Print "Edited text: " &amp; objStream.ReadText
    
     ' copy the file to another folder
    strDestFile = "test2/test1.txt"
    rcFile.CopyRecord "", "http://MyServer/" &amp; strDestFile, "", "", adCopyOverWrite
    
     ' delete the original file
    rcFile.DeleteRecord
    
     ' move the file from the subfolder back to original location
    strDestFolder = "test2/"
    rcDestFolder.Open strDestFolder, Cnxn ', adOpenIfExists  'Or adCreateCollection
    Set rsDestFolder = rcDestFolder.GetChildren
    rsDestFolder.MoveFirst
    
     ' position current record at on the correct file
    Do While Not (rsDestFolder.EOF Or rsDestFolder(0) = "test1.txt")
        rsDestFolder.MoveNext
    Loop
    
     ' open a record on the correct row of the recordset
    rcDestFile.Open rsDestFolder, Cnxn
    
     ' do the move
    rcDestFile.MoveRecord "", "http://MyServer/" &amp; strFile, "", "", adMoveOverWrite
    
    ' clean up
    rsDestFolder.Close
    Cnxn.Close
    Set rsDestFolder = Nothing
    Set Cnxn = Nothing
    Exit Sub
    
ErrorHandler:
    ' clean up
    If Not rsDestFolder Is Nothing Then
        If rsDestFolder.State = adStateOpen Then rsDestFolder.Close
    End If
    Set rsDestFolder = Nothing
    
    If Not Cnxn Is Nothing Then
        If Cnxn.State = adStateOpen Then Cnxn.Close
    End If
    Set Cnxn = Nothing
    
    If Err &lt;&gt; 0 Then
        MsgBox Err.Source &amp; "--&gt;" &amp; Err.Description, , "Error"
    End If
End Sub
'EndDeleteRecordVB</code>
  </introduction>
  <relatedTopics>
<link xlink:href="2726498c-dbd8-4266-983b-ae7d62c39142">DeleteRecord Method</link>
<link xlink:href="938522b4-f836-4c80-8d27-a598a000f0ee">Flush Method</link>
<link xlink:href="b3f09bac-4f66-49f6-aa5a-6fbb4fb28338">GetChildren Method</link>
<link xlink:href="6d2807b0-b861-4583-bcaf-fb0b82e0f2d0">MoveRecord Method</link>
<link xlink:href="65120ce6-3900-4cd4-b322-3b9816d74737">ParentURL Property</link>
<link xlink:href="2c18279e-6f35-4af0-b12e-8f1543d9ed20">Source Property (ADO Record)</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>