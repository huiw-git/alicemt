---
title: "Supports Method Example (VB)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - VB
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 135aab26-ff5c-4fd9-910f-65cdead0b47e
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
# Supports Method Example (VB)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This example uses the <legacyLink xlink:href="298fc41c-0b55-42fc-b373-c5133b4da6a5">Supports</legacyLink> method to display the options supported by a recordset opened with different cursor types. The DisplaySupport procedure is required for this procedure to run.</para>
    <code>'BeginSupportsVB

    'To integrate this code
    'replace the data source and initial catalog values
    'in the connection string

Public Sub Main()
    On Error GoTo ErrorHandler

    ' recordset and connection variables
    Dim rstTitles As ADODB.Recordset
    Dim Cnxn As ADODB.Connection
    Dim strCnxn As String
    Dim strSQLTitles As String
     ' array variables
    Dim arrCursorType(4) As Integer
    Dim intIndex As Integer
    
    ' open connection
    Set Cnxn = New ADODB.Connection
    strCnxn = "Provider='sqloledb';Data Source='MySqlServer';" &amp; _
        "Initial Catalog='Pubs';Integrated Security='SSPI';"
    Cnxn.Open strCnxn
    
    ' Fill array with CursorType constants
    arrCursorType(0) = adOpenForwardOnly
    arrCursorType(1) = adOpenKeyset
    arrCursorType(2) = adOpenDynamic
    arrCursorType(3) = adOpenStatic
    
    ' open recordset using each CursorType and optimistic locking
    For intIndex = 0 To 3
        Set rstTitles = New ADODB.Recordset
        rstTitles.CursorType = arrCursorType(intIndex)
        rstTitles.LockType = adLockOptimistic
        
        strSQLTitles = "Titles"
        rstTitles.Open strSQLTitles, Cnxn, , , adCmdTable
        
        Select Case arrCursorType(intIndex)
           Case adOpenForwardOnly
              Debug.Print "ForwardOnly cursor supports:"
           Case adOpenKeyset
              Debug.Print "Keyset cursor supports:"
           Case adOpenDynamic
              Debug.Print "Dynamic cursor supports:"
           Case adOpenStatic
              Debug.Print "Static cursor supports:"
        End Select
        
        ' call the DisplaySupport procedure from below
        ' to display the supported options
        DisplaySupport rstTitles
       
    Next intIndex
   
    ' clean up
    rstTitles.Close
    Cnxn.Close
    Set rstTitles = Nothing
    Set Cnxn = Nothing
    Exit Sub
    
ErrorHandler:
    ' clean up
    If Not rstTitles Is Nothing Then
        If rstTitles.State = adStateOpen Then rstTitles.Close
    End If
    Set rstTitles = Nothing
    
    If Not Cnxn Is Nothing Then
        If Cnxn.State = adStateOpen Then Cnxn.Close
    End If
    Set Cnxn = Nothing
    
    If Err &lt;&gt; 0 Then
        MsgBox Err.Source &amp; "--&gt;" &amp; Err.Description, , "Error"
    End If
End Sub
'EndSupportsVB



'BeginSupports2VB
Public Sub DisplaySupport(rstTemp As ADODB.Recordset)

   Dim arrConstants(11) As Long
   Dim blnSupports As Boolean
   Dim intIndex As Integer

   ' Fill array with cursor option constants
   arrConstants(0) = adAddNew
   arrConstants(1) = adApproxPosition
   arrConstants(2) = adBookmark
   arrConstants(3) = adDelete
   arrConstants(4) = adFind
   arrConstants(5) = adHoldRecords
   arrConstants(6) = adMovePrevious
   arrConstants(7) = adNotify
   arrConstants(8) = adResync
   arrConstants(9) = adUpdate
   arrConstants(10) = adUpdateBatch
   
   For intIndex = 0 To 10
      blnSupports = _
         rstTemp.Supports(arrConstants(intIndex))
      If blnSupports Then
         Select Case arrConstants(intIndex)
            Case adAddNew
               Debug.Print "   AddNew"
            Case adApproxPosition
               Debug.Print "   AbsolutePosition and AbsolutePage"
            Case adBookmark
               Debug.Print "   blnkmark"
            Case adDelete
               Debug.Print "   Delete"
            Case adFind
               Debug.Print "   Find"
            Case adHoldRecords
               Debug.Print "   Holding Records"
            Case adMovePrevious
               Debug.Print "   MovePrevious and Move"
            Case adNotify
               Debug.Print "   Notifications"
            Case adResync
               Debug.Print "   Resyncing data"
            Case adUpdate
               Debug.Print "   Update"
            Case adUpdateBatch
               Debug.Print "   batch updating"
         End Select
      End If
   Next intIndex

End Sub
'EndSupports2VB</code>
  </introduction>
  <relatedTopics>
<link xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset Object</link>
<link xlink:href="298fc41c-0b55-42fc-b373-c5133b4da6a5">Supports Method</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>