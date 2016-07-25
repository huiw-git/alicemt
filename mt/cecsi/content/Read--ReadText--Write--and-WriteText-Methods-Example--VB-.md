---
title: "Read, ReadText, Write, and WriteText Methods Example (VB)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - VB
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 699b73f7-04f9-4d46-94b2-6cb12be6de56
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
# Read, ReadText, Write, and WriteText Methods Example (VB)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This example demonstrates how to read the contents of a text box into both a text <legacyLink xlink:href="0514531f-009d-4519-abc3-d727014a39f1">Stream</legacyLink> and a binary <legacyBold>Stream</legacyBold>. Other properties and methods shown include <legacyLink xlink:href="daa8319a-49aa-4c1c-9af6-0b01e9ab2f9d">Position</legacyLink>, <legacyLink xlink:href="e6bad449-ebdb-4dd3-886a-9e6f1e7ee5d2">Size</legacyLink>, <legacyLink xlink:href="e42507cb-9b46-4ce4-8191-2948eaf14ca2">Charset</legacyLink>, and <legacyLink xlink:href="707c18ca-6a56-4970-bbd6-ae1fb86a0b8a">SetEOS</legacyLink>.</para>
    <code>'BeginReadVB
Private Sub cmdRead_Click()
    On Error GoTo ErrorHandler
    
    'Declare variables
    Dim objStream As Stream
    Dim varA As Variant
    Dim bytA() As Byte
    Dim i As Integer
    Dim strBytes As String
    
    'Instantiate and Open Stream
    Set objStream = New Stream
    objStream.Open
    
    'Write the text content of a textbox to the stream
    If Text1.Text = "" Then
        Err.Raise 1, , "The text field is blank."
    End If
    objStream.WriteText Text1.Text
    
    'Display the text contents and size of the stream
    objStream.Position = 0
    Debug.Print "Default text:"
    Debug.Print objStream.ReadText
    Debug.Print objStream.Size
    
    'Switch character set and display
    objStream.Position = 0
    objStream.Charset = "Windows-1252"
    Debug.Print "New Charset text:"
    Debug.Print objStream.ReadText
    Debug.Print objStream.Size
    
    'Switch to a binary stream and display
    objStream.Position = 0
    objStream.Type = adTypeBinary
    Debug.Print "Binary:"
    Debug.Print objStream.Read
    Debug.Print objStream.Size
    
    'Load an array of bytes with the text box text
    ReDim bytA(Len(Text1.Text))
    For i = 1 To Len(Text1.Text)
        bytA(i - 1) = CByte(Asc(Mid(Text1.Text, i, 1)))
    Next
    
    'Write the buffer to the binary stream and display
    objStream.Position = 0
    objStream.Write bytA()
    objStream.SetEOS
    objStream.Position = 0
    Debug.Print "Binary after Write:"
    Debug.Print objStream.Read
    Debug.Print objStream.Size
    
    'Switch back to a text stream and display
    Debug.Print "Translated back:"
    objStream.Position = 0
    objStream.Type = adTypeText
    Debug.Print objStream.ReadText
    Debug.Print objStream.Size
    
    ' clean up
    objStream.Close
    Set objStream = Nothing
    Exit Sub
    
ErrorHandler:
    ' clean up
    If Not objStream Is Nothing Then
        If objStream.State = adStateOpen Then objStream.Close
    End If
    Set objStream = Nothing
    
    If Err &lt;&gt; 0 Then
        MsgBox Err.Source &amp; "--&gt;" &amp; Err.Description, , "Error"
    End If
End Sub
'EndReadVB</code>
  </introduction>
  <relatedTopics>
<link xlink:href="e42507cb-9b46-4ce4-8191-2948eaf14ca2">Charset Property</link>
<link xlink:href="daa8319a-49aa-4c1c-9af6-0b01e9ab2f9d">Position Property</link>
<link xlink:href="838502de-80f1-4eeb-8838-dd3d9403e567">Read Method</link>
<link xlink:href="be5a409e-cf87-4859-9ea5-713401755a77">ReadText Method</link>
<link xlink:href="707c18ca-6a56-4970-bbd6-ae1fb86a0b8a">SetEOS Method</link>
<link xlink:href="a487c241-d953-4c31-ae7e-6358d5cf6733">Size Property (ADO Stream)</link>
<link xlink:href="0514531f-009d-4519-abc3-d727014a39f1">Stream Object</link>
<link xlink:href="02982e6a-ac5f-4af2-b82e-ce12534b84b2">Write Method</link>
<link xlink:href="7a669048-13f4-4574-a2b1-985e089729d5">WriteText Method</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>