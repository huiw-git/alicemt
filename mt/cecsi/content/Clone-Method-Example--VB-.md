---
title: "Clone Method Example (VB)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - VB
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 64cb1753-e074-4a2d-8b74-7c35f3f6f64d
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
# Clone Method Example (VB)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This example uses the <legacyLink xlink:href="ad49265f-1c05-4271-9bbf-7c00010ac18c">Clone</legacyLink> method to create copies of a <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink> and then lets the user position the record pointer of each copy independently.</para>
    <code>'BeginCloneVB

    'To integrate this code
    'replace the data source and initial catalog values
    'in the connection string
    
Public Sub Main()
    On Error GoTo ErrorHandler

    'recordset array and connection variables
    Dim arstStores(1 To 3) As ADODB.Recordset
    Dim Cnxn As ADODB.Connection
    Dim strSQLStore As String
    Dim strCnxn As String
     'record variables
    Dim intLoop As Integer
    Dim strMessage As String
    Dim strFind As String
    
    ' Open a connection
    Set Cnxn = New ADODB.Connection
    strCnxn = "Provider='sqloledb';Data Source='MySqlServer';" &amp; _
        "Initial Catalog='Pubs';Integrated Security='SSPI';"
    Cnxn.Open strCnxn
    
    ' Open recordset as a static cursor type recordset
    Set arstStores(1) = New ADODB.Recordset
    strSQLStore = "SELECT stor_name FROM Stores ORDER BY stor_name"
    arstStores(1).Open strSQLStore, strCnxn, adOpenStatic, adLockBatchOptimistic, adCmdText
    
    ' Create two clones of the original Recordset
    Set arstStores(2) = arstStores(1).Clone
    Set arstStores(3) = arstStores(1).Clone

    ' Loop through the array so that on each pass the user
    ' is searching a different copy of the same Recordset
    Do
        For intLoop = 1 To 3
             ' Ask for search string while showing where
             ' the current record pointer is for each Recordset
            strMessage = _
                "Recordsets from stores table:" &amp; vbCr &amp; _
                "  1 - Original - Record pointer at " &amp; arstStores(1)!stor_name &amp; vbCr &amp; _
                "  2 - Clone - Record pointer at " &amp; arstStores(2)!stor_name &amp; vbCr &amp; _
                "  3 - Clone - Record pointer at " &amp; arstStores(3)!stor_name &amp; vbCr &amp; _
                "Enter search string for #" &amp; intLoop &amp; ":"
            
            strFind = Trim(InputBox(strMessage))
             ' make sure something was entered, if not then EXIT loop
            If strFind = "" Then Exit Do
         
             ' otherwise locate the record from the entered string
            arstStores(intLoop).Filter = "stor_name = '" &amp; strFind &amp; "'"
         
             'if there's no match, jump to the last record
            If arstStores(intLoop).EOF Then
                arstStores(intLoop).Filter = adFilterNone
                arstStores(intLoop).MoveLast
            Else
                MsgBox "Found " &amp; strFind
            End If
        Next intLoop
    Loop

    ' clean up
    arstStores(1).Close
    arstStores(2).Close
    arstStores(3).Close
    Cnxn.Close
    Set arstStores(1) = Nothing
    Set arstStores(2) = Nothing
    Set arstStores(3) = Nothing
    Set Cnxn = Nothing
    Exit Sub
    
ErrorHandler:
    ' clean up
    If Not arstStores(1) Is Nothing Then
        If arstStores(1).State = adStateOpen Then arstStores(1).Close
    End If
    Set arstStores(1) = Nothing
    If Not arstStores(2) Is Nothing Then
        If arstStores(2).State = adStateOpen Then arstStores(2).Close
    End If
    Set arstStores(2) = Nothing
    If Not arstStores(3) Is Nothing Then
        If arstStores(3).State = adStateOpen Then arstStores(3).Close
    End If
    Set arstStores(3) = Nothing
    
    If Not Cnxn Is Nothing Then
        If Cnxn.State = adStateOpen Then Cnxn.Close
    End If
    Set Cnxn = Nothing
    
    If Err &lt;&gt; 0 Then
        MsgBox Err.Source &amp; "--&gt;" &amp; Err.Description, , "Error"
    End If
End Sub
'EndCloneVB</code>
  </introduction>
  <relatedTopics>
<link xlink:href="ad49265f-1c05-4271-9bbf-7c00010ac18c">Clone Method</link>
<link xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset Object</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>