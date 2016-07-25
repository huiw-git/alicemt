---
title: "Cancel Method Example (VB)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - VB
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 5c0530ad-68d0-4cba-b1af-9386d566c7c5
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
# Cancel Method Example (VB)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This example uses the <legacyLink xlink:href="e0db4e15-6787-41e2-8f13-9e9b524d620a">Cancel</legacyLink> method to cancel a command executing on a <legacyLink xlink:href="ef6b1824-5b12-43db-89d7-8f3d13896d4d">Connection</legacyLink> object if the connection is busy.</para>
    <code>'BeginCancelVB

    'To integrate this code
    'replace the data source and initial catalog values
    'in the connection string
    
Public Sub Main()
    On Error GoTo ErrorHandler

    'recordset and connection variables
    Dim Cnxn As ADODB.Connection
    Dim strCnxn As String
    Dim strCmdChange As String
    Dim strCmdRestore As String
     'record variables
    Dim blnChanged As Boolean
    
    ' Open a connection
    Set Cnxn = New ADODB.Connection
    strCnxn = "Provider='sqloledb';Data Source='MySqlServer';" &amp; _
        "Initial Catalog='Pubs';Integrated Security='SSPI';"
    Cnxn.Open strCnxn
    
    ' Define command strings
    strCmdChange = "UPDATE titles SET type = 'self_help' WHERE type = 'psychology'"
    strCmdRestore = "UPDATE titles SET type = 'psychology' " &amp; _
                     "WHERE type = 'self_help'"
   
    ' Begin a transaction, then execute a command asynchronously
    Cnxn.BeginTrans
    Cnxn.Execute strCmdChange, , adAsyncExecute
    ' do something else for a little while –
    ' use i = 1 to 32000 to allow completion
    Dim i As Integer
    For i = 1 To 1000
        i = i + i
        Debug.Print i
    Next i
    
    ' If the command has NOT completed, cancel the execute and
    ' roll back the transaction; otherwise, commit the transaction
    If CBool(Cnxn.State And adStateExecuting) Then
        Cnxn.Cancel
        Cnxn.RollbackTrans
        blnChanged = False
        MsgBox "Update canceled."
    Else
        Cnxn.CommitTrans
        blnChanged = True
        MsgBox "Update complete."
    End If
   
    ' If the change was made, restore the data
    ' because this is only a demo
    If blnChanged Then
        Cnxn.Execute strCmdRestore
        MsgBox "Data restored."
    End If
      
    ' clean up
    Cnxn.Close
    Set Cnxn = Nothing
    Exit Sub
    
ErrorHandler:
    If Not Cnxn Is Nothing Then
        If Cnxn.State = adStateOpen Then Cnxn.Close
    End If
    Set Cnxn = Nothing
    
    If Err &lt;&gt; 0 Then
        MsgBox Err.Source &amp; "--&gt;" &amp; Err.Description, , "Error"
    End If
End Sub
'EndCancelVB</code>
  </introduction>
  <relatedTopics>
<link xlink:href="e0db4e15-6787-41e2-8f13-9e9b524d620a">Cancel Method</link>
<link xlink:href="ef6b1824-5b12-43db-89d7-8f3d13896d4d">Connection Object</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>