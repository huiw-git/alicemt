---
title: "Count Property Example (VB)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - VB
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 35033910-623b-449a-a57d-baff3ed5ab8f
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
# Count Property Example (VB)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This example demonstrates the <legacyLink xlink:href="da9ccd1f-d402-41a2-940c-45556fc5340d">Count</legacyLink> property with two collections in the <legacyBold><legacyItalic>Employee</legacyItalic></legacyBold> database. The property obtains the number of objects in each collection, and sets the upper limit for loops that enumerate these collections. Another way to enumerate these collections without using the <legacyBold>Count</legacyBold> property would be to use <codeInline>For Each...Next</codeInline> statements.</para>
    <code>'BeginCountVB

    'To integrate this code
    'replace the data source and initial catalog values
    'in the connection string
    
Public Sub Main()
    On Error GoTo ErrorHandler

    ' recordset and connection variables
    Dim rstEmployees As ADODB.Recordset
    Dim Cnxn As ADODB.Connection
    Dim strSQLEmployees As String
    Dim strCnxn As String
    
    Dim intLoop As Integer
    
    ' Open a connection
    Set Cnxn = New ADODB.Connection
    strCnxn = "Provider='sqloledb';Data Source='MySqlServer';" &amp; _
        "Initial Catalog='Northwind';Integrated Security='SSPI';"
    Cnxn.Open strCnxn
    
    ' Open recordset with data from Employee table
    Set rstEmployees = New ADODB.Recordset
    strSQLEmployees = "Employee"
    'rstEmployees.Open strSQLEmployee, Cnxn, , , adCmdTable
    rstEmployees.Open strSQLEmployees, Cnxn, adOpenForwardOnly, adLockReadOnly, adCmdTable
    'the above two lines opening the recordset are identical as
    'the default values for CursorType and LockType arguments match those specified
    
    ' Print information about Fields collection
    Debug.Print rstEmployees.Fields.Count &amp; " Fields in Employee"
    
    For intLoop = 0 To rstEmployees.Fields.Count - 1
        Debug.Print "   " &amp; rstEmployees.Fields(intLoop).Name
    Next intLoop

    ' Print information about Properties collection
    Debug.Print rstEmployees.Properties.Count &amp; " Properties in Employee"
    
    For intLoop = 0 To rstEmployees.Properties.Count - 1
        Debug.Print "   " &amp; rstEmployees.Properties(intLoop).Name
    Next intLoop

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
'EndCountVB</code>
  </introduction>
  <relatedTopics>
<link xlink:href="da9ccd1f-d402-41a2-940c-45556fc5340d">Count Property</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>