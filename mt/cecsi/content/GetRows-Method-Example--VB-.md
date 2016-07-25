---
title: "GetRows Method Example (VB)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - VB
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9f7c78bb-7bb8-4c4f-8e5a-4d3bfc8a208f
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
# GetRows Method Example (VB)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This example uses the <legacyLink xlink:href="14b92860-4171-47d9-a413-dd60dd6a8880">GetRows</legacyLink> method to retrieve a specified number of rows from a <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink> and to fill an array with the resulting data. The <legacyBold>GetRows</legacyBold> method will return fewer than the desired number of rows in two cases: either if <legacyLink xlink:href="36c31ab2-f3b6-4281-89b6-db7e04e38fd2">EOF</legacyLink> has been reached, or if <legacyBold>GetRows</legacyBold> tried to retrieve a record that was deleted by another user. The function returns <legacyBold>False</legacyBold> only if the second case occurs. The GetRowsOK function is required for this procedure to run.</para>
    <code>'BeginGetRowsVB

    'To integrate this code
    'replace the data source and initial catalog values
    'in the connection string
    
Public Sub Main()
    On Error GoTo ErrorHandler

     ' connection and recordset variables
    Dim rstEmployees As ADODB.Recordset
    Dim Cnxn As ADODB.Connection
    Dim strSQLEmployees As String
    Dim strCnxn As String
    ' array variable
    Dim arrEmployees As Variant
    ' detail variables
    Dim strMessage As String
    Dim intRows As Integer
    Dim intRecord As Integer
    
    ' open connection
    Set Cnxn = New ADODB.Connection
    strCnxn = "Provider='sqloledb';Data Source='MySqlServer';" &amp; _
        "Initial Catalog='Pubs';Integrated Security='SSPI';"
    Cnxn.Open strCnxn
    
    ' open recordset client-side to enable RecordCount
    Set rstEmployees = New ADODB.Recordset
    strSQLEmployees = "SELECT fName, lName, hire_date FROM Employee ORDER BY lName"
    rstEmployees.Open strSQLEmployees, Cnxn, adOpenStatic, adLockReadOnly, adCmdText
    
    ' get user input for number of rows
    Do
        strMessage = "Enter number of rows to retrieve:"
        intRows = Val(InputBox(strMessage))
        
          ' if bad user input exit the loop
        If intRows &lt;= 0 Then
            MsgBox "Please enter a positive number", vbOKOnly, "Not less than zero!"
        ' if number of requested records is over the total
        ElseIf intRows &gt; rstEmployees.RecordCount Then
            MsgBox "Not enough records in Recordset to retrieve " &amp; intRows &amp; " rows.", _
            vbOKOnly, "Over the available total"
        Else
            Exit Do
        End If
    Loop
    
      ' else put the data in an array and print
    arrEmployees = rstEmployees.GetRows(intRows)
    
    Dim x As Integer, y As Integer
    
    For x = 0 To intRows - 1
        For y = 0 To 2
            Debug.Print arrEmployees(y, x) &amp; " ";
        Next y
        Debug.Print vbCrLf
    Next x
    
    ' clean up
    rstEmployees.Close
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
'EndGetRowsVB</code>
  </introduction>
  <relatedTopics>
<link xlink:href="14b92860-4171-47d9-a413-dd60dd6a8880">GetRows Method</link>
<link xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset Object</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>