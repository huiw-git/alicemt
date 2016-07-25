---
title: "Seek Method and Index Property Example (VB)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - VB
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 337c9eda-9ddf-49ac-94d3-b33114ba6224
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
# Seek Method and Index Property Example (VB)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This example uses the <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink> object's <legacyLink xlink:href="129293d2-19d3-4940-bf64-483ee72fb4a1">Seek</legacyLink> method and <legacyLink xlink:href="1c79e271-21ec-41a8-8163-c5e89f0001a7">Index</legacyLink> property in conjunction with a given <legacyBold><legacyItalic>Employee ID</legacyItalic></legacyBold>, to locate the employee's name in the <legacyBold><legacyItalic>Employees</legacyItalic></legacyBold> table of the Nwind.mdb database.</para>
    <code>'BeginSeekVB
Public Sub SeekX()
    On Error GoTo ErrorHandler

    ' To integrate this code replace the data source
    ' in the connection string
 
     'recordset and connection variables
    Dim rstEmployees As ADODB.Recordset
    Dim Cnxn As ADODB.Connection
    Dim strCnxn As String
    Dim strSQLEmployees As String
    
    Dim strID As String
    Dim strPrompt As String
    strPrompt = "Enter an EmployeeID (e.g., 1 to 9)"
    
    ' Open connection
    Set Cnxn = New ADODB.Connection
    strCnxn = "Provider='Microsoft.Jet.OLEDB.4.0';" &amp; _
                "Data Source='C:\Program Files\Microsoft Office XP\Office10\Samples\northwind.mdb';"
    Cnxn.Open strCnxn
     
     ' open recordset server-side for indexing
    Set rstEmployees = New ADODB.Recordset
    rstEmployees.CursorLocation = adUseServer
    strSQLEmployees = "employees"
    rstEmployees.Open strSQLEmployees, strCnxn, adOpenKeyset, adLockReadOnly, adCmdTableDirect
    
    ' Does this provider support Seek and Index?
    If rstEmployees.Supports(adIndex) And rstEmployees.Supports(adSeek) Then
        rstEmployees.Index = "PrimaryKey"
        ' Display all the employees
            rstEmployees.MoveFirst
            Do While rstEmployees.EOF = False
                Debug.Print rstEmployees!EmployeeId; ": "; rstEmployees!FirstName; " "; _
                    rstEmployees!LastName
                rstEmployees.MoveNext
            Loop
        
    ' Prompt the user for an EmployeeID between 1 and 9
          rstEmployees.MoveFirst
          Do
             strID = LCase(Trim(InputBox(strPrompt, "Seek Example")))
             ' Quit if strID is a zero-length string (CANCEL, null, etc.)
             If Len(strID) = 0 Then Exit Do
             If Len(strID) = 1 And strID &gt;= "1" And strID &lt;= "9" Then
                rstEmployees.Seek Array(strID), adSeekFirstEQ
                If rstEmployees.EOF Then
                   Debug.Print "Employee not found.", , "Seek Example"
                   MsgBox "Employee not found."
                Else
                   Debug.Print strID; ": Employee='"; rstEmployees!FirstName; " "; _
                      rstEmployees!LastName; "'"
                   MsgBox "EmployeeID is: " + strID + "; Employee Name is: '" + rstEmployees!FirstName + " " + _
                      rstEmployees!LastName + "'", , "Seek Example"
                End If
             Else
                MsgBox "You entered a wrong EmployeeID, please enter a new ID."
             End If
          Loop
    End If
    
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
'EndSeekVB</code>
  </introduction>
  <relatedTopics>
<link xlink:href="1c79e271-21ec-41a8-8163-c5e89f0001a7">Index Property</link>
<link xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset Object</link>
<link xlink:href="129293d2-19d3-4940-bf64-483ee72fb4a1">Seek Method</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>