---
title: "CursorType, LockType, and EditMode Properties Example (VB)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - VB
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2cb4a304-f40a-4897-8b93-82c2d8e93500
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
# CursorType, LockType, and EditMode Properties Example (VB)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This example demonstrates setting the <legacyLink xlink:href="b62c66ca-58d5-430e-9257-eb38c65e48c2">CursorType</legacyLink> and <legacyLink xlink:href="9920c14e-033a-4de1-8149-0ce9737a3246">LockType</legacyLink> properties before opening a <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink>. It also shows the value of the <legacyLink xlink:href="a1b04bb2-8c8b-47f9-8477-bfd0368b6f68">EditMode</legacyLink> property under various conditions. The EditModeOutput function is required for this procedure to run.</para>
    <code>'BeginEditModeVB

    'To integrate this code
    'replace the data source and initial catalog values
    'in the connection string

Public Sub Main()
    On Error GoTo ErrorHandler

    ' recordset variables
    Dim rstEmployees As ADODB.Recordset
    Dim Cnxn As ADODB.Connection
    Dim strCnxn As String
    Dim SQLEmployees As String
    
     ' open connection
    Set Cnxn = New ADODB.Connection
    strCnxn = "Provider='sqloledb';Data Source='MySqlServer';" &amp; _
        "Initial Catalog='Pubs';Integrated Security='SSPI';"
    Cnxn.Open strCnxn
       
      ' set recordset properties through object refs
      ' instead of through arguments to Open method
    Set rstEmployees = New ADODB.Recordset
    Set rstEmployees.ActiveConnection = Cnxn
    rstEmployees.CursorLocation = adUseClient
    rstEmployees.CursorType = adOpenStatic
    rstEmployees.LockType = adLockBatchOptimistic
    
     ' open recordset with data from Employee table
    SQLEmployees = "employee"
    rstEmployees.Open SQLEmployees, , , , adCmdTable
    
    ' Show the EditMode property under different editing states
    rstEmployees.AddNew
        rstEmployees!emp_id = "T-T55555M"
        rstEmployees!fname = "temp_fname"
        rstEmployees!lname = "temp_lname"
            'call function below
            'to output results to debug window
        EditModeOutput "After AddNew:", rstEmployees.EditMode
        rstEmployees.UpdateBatch
        EditModeOutput "After UpdateBatch:", rstEmployees.EditMode
        rstEmployees!fname = "test"
        EditModeOutput "After Edit:", rstEmployees.EditMode
    rstEmployees.Close
    
    ' Delete new record because this is a demonstration
    Cnxn.Execute "DELETE FROM employee WHERE emp_id = 'T-T55555M'"

    ' clean up
    Cnxn.Close
    Set rstEmployees = Nothing
    Set Cnxn = Nothing
    Exit Sub
    
ErrorHandler:
    ' clean up
    If Not rstEmployees Is Nothing Then
        If rstEmployees.State = adStateOpen Then rstEmployees.Close
    End If
    Set rstEmployees = Nothing
    
    If Not Cnxn Is Nothing Then
        If Cnxn.State = adStateOpen Then Cnxn.Close
    End If
    Set Cnxn = Nothing
    
    If Err &lt;&gt; 0 Then
        MsgBox Err.Source &amp; "--&gt;" &amp; Err.Description, , "Error"
    End If

End Sub

Public Function EditModeOutput(strTemp As String, _
   intEditMode As Integer)

   ' Print report based on the value of the EditMode
   ' property
   Debug.Print strTemp
   Debug.Print "  EditMode = ";

   Select Case intEditMode
      Case adEditNone
         Debug.Print "adEditNone"
      Case adEditInProgress
         Debug.Print "adEditInProgress"
      Case adEditAdd
         Debug.Print "adEditAdd"
   End Select

End Function
'EndEditModeVB</code>
  </introduction>
  <relatedTopics>
<link xlink:href="b62c66ca-58d5-430e-9257-eb38c65e48c2">CursorType Property</link>
<link xlink:href="ffc6e245-4471-42ae-84dd-e85bddfce983">CursorTypeEnum</link>
<link xlink:href="a1b04bb2-8c8b-47f9-8477-bfd0368b6f68">EditMode Property</link>
<link xlink:href="45d54b6e-db2c-4553-9fd0-528147d6da2f">EditModeEnum</link>
<link xlink:href="9920c14e-033a-4de1-8149-0ce9737a3246">LockType Property</link>
<link xlink:href="d2894eaf-4450-4ace-aa51-c8b875fd3010">LockTypeEnum</link>
<link xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset Object</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>