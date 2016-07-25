---
title: "Description, HelpContext, HelpFile, NativeError, Number, Source, and SQLState Properties Example (VB)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - VB
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 5c728458-d85c-497c-afcf-2cfa36c3342a
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
# Description, HelpContext, HelpFile, NativeError, Number, Source, and SQLState Properties Example (VB)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This example triggers an error, traps it, and displays the <legacyLink xlink:href="4b5d6790-6c29-42aa-bf78-d9cfb8ad7965">Description</legacyLink>, <legacyLink xlink:href="2b9ef441-993c-44d4-8f87-fac0979dac1d">HelpContext</legacyLink>, <legacyLink xlink:href="2b9ef441-993c-44d4-8f87-fac0979dac1d">HelpFile</legacyLink>, <legacyLink xlink:href="b9b47e57-18a4-4186-aef5-5bd18d7b1d74">NativeError</legacyLink>, <legacyLink xlink:href="f92323c5-dd11-4a63-a505-d9014a0f067f">Number</legacyLink>, <legacyLink xlink:href="4044ba15-f013-4c4c-9fe1-b4410fe9a778">Source</legacyLink>, and <legacyLink xlink:href="f9e25967-54b0-444d-af2a-0d2c75365d3e">SQLState</legacyLink> properties of the resulting <legacyLink xlink:href="a175d453-fa55-4f49-9ede-a26d83177919">Error</legacyLink> object.</para>
    <code>'BeginDescriptionVB
Public Sub Main()

    Dim Cnxn As ADODB.Connection
    Dim Err As ADODB.Error
    Dim strError As String
    
    On Error GoTo ErrorHandler
    
    ' Intentionally trigger an error
    Set Cnxn = New ADODB.Connection
    Cnxn.Open "nothing"
    
    Set Cnxn = Nothing
    Exit Sub

ErrorHandler:

    ' Enumerate Errors collection and display
    ' properties of each Error object
    For Each Err In Cnxn.Errors
        strError = "Error #" &amp; Err.Number &amp; vbCr &amp; _
            "   " &amp; Err.Description &amp; vbCr &amp; _
            "   (Source: " &amp; Err.Source &amp; ")" &amp; vbCr &amp; _
            "   (SQL State: " &amp; Err.SQLState &amp; ")" &amp; vbCr &amp; _
            "   (NativeError: " &amp; Err.NativeError &amp; ")" &amp; vbCr
        If Err.HelpFile = "" Then
            strError = strError &amp; "   No Help file available"
        Else
            strError = strError &amp; _
               "   (HelpFile: " &amp; Err.HelpFile &amp; ")" &amp; vbCr &amp; _
               "   (HelpContext: " &amp; Err.HelpContext &amp; ")" &amp; _
               vbCr &amp; vbCr
        End If
         
        Debug.Print strError
    Next

    Resume Next
End Sub
'EndDescriptionVB</code>
  </introduction>
  <relatedTopics>
<link xlink:href="4b5d6790-6c29-42aa-bf78-d9cfb8ad7965">Description Property</link>
<link xlink:href="a175d453-fa55-4f49-9ede-a26d83177919">Error Object</link>
<link xlink:href="2b9ef441-993c-44d4-8f87-fac0979dac1d">HelpContext Property</link>
<link xlink:href="2b9ef441-993c-44d4-8f87-fac0979dac1d">HelpFile Property</link>
<link xlink:href="b9b47e57-18a4-4186-aef5-5bd18d7b1d74">NativeError Property</link>
<link xlink:href="f92323c5-dd11-4a63-a505-d9014a0f067f">Number Property</link>
<link xlink:href="4044ba15-f013-4c4c-9fe1-b4410fe9a778">Source Property (ADO Error)</link>
<link xlink:href="f9e25967-54b0-444d-af2a-0d2c75365d3e">SQLState Property</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>