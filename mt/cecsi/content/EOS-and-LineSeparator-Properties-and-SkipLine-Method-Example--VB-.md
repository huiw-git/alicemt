---
title: "EOS and LineSeparator Properties and SkipLine Method Example (VB)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - VB
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 77ce3042-9ebc-44ba-a4ff-0f1b1fd4a9c4
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
# EOS and LineSeparator Properties and SkipLine Method Example (VB)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This example demonstrates how to manipulate text streams one line at a time. The effect of changing the line separator from the default carriage return/linefeed (<legacyBold>adCRLF</legacyBold>) to simply linefeed (<legacyBold>adLF</legacyBold>) or carriage return (<legacyBold>adCR</legacyBold>) is shown.</para>
    <code>'BeginSkipLineVB
Private Sub cmdSkipLine_Click()
    On Error GoTo ErrorHandler
    
    'Declare variables
    Dim i As Integer
    Dim objStream As Stream
    Dim strLine, strChar As String
    
    'Instantiate and open stream
    Set objStream = New Stream
    objStream.Open
    
    'Set line separator to line feed
    objStream.LineSeparator = adLF
       
    'Load text content of list box into stream
    'One line at a time
    For i = 0 To (List1.ListCount - 1)
        objStream.WriteText List1.List(i), adWriteLine
    Next
    
    'Display the entire stream
    Debug.Print "Whole Stream:"
    objStream.Position = 0
    Debug.Print objStream.ReadText
        
    'Display the first line
    Debug.Print "First Line:"
    objStream.Position = 0
    strLine = objStream.ReadText(adReadLine)
    Debug.Print strLine
    Debug.Print "Line length: " + Str(Len(strLine))
    
    'Skip a line, then display another line
    Debug.Print "Third Line:"
    objStream.SkipLine
    strLine = objStream.ReadText(adReadLine)
    Debug.Print strLine
    Debug.Print "Line length: " + Str(Len(strLine))
    
    'Switch line separator to carriage return
    'All items from list will be considered one line
    'Assuming no CRs have been loaded into stream
    Debug.Print "Whole Stream/First Line:"
    objStream.Position = 0
    objStream.LineSeparator = adCR
    strLine = objStream.ReadText(adReadLine)
    Debug.Print strLine
    Debug.Print "Line length: " + Str(Len(strLine))
    Debug.Print "Stream size: " + Str(objStream.Size)
    
    'Use EOS to Determine End of Stream
    Debug.Print "Character by character:"
    objStream.Position = 0
    Do Until objStream.EOS
        strChar = objStream.ReadText(1)
        Debug.Print strChar
    Loop
    
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

Private Sub Form_Load()
    List1.AddItem "This is the first line"
    List1.AddItem "This is the second line"
    List1.AddItem "This is the third line"
End Sub
'EndSkipLineVB</code>
  </introduction>
  <relatedTopics>
<link xlink:href="57e08c5f-f3ed-4ecd-8c66-50b83b1031d1">EOS Property</link>
<link xlink:href="0b20fbb8-6b83-48ec-b442-f96c8a4bafbb">LineSeparator Property</link>
<link xlink:href="0abc00fe-ee09-4c8e-b1f2-48ee9c5f3329">SkipLine Method</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>