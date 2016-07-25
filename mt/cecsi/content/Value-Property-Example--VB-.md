---
title: "Value Property Example (VB)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - VB
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2d4fe651-ef09-461b-8884-a70b6af4362e
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
# Value Property Example (VB)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This example demonstrates the <legacyLink xlink:href="48919c74-86d4-462e-99b9-8854ceb8d683">Value</legacyLink> property with <legacyLink xlink:href="b10a72fc-3c4b-4186-a70b-993dc9f7a092">Field</legacyLink> and <legacyLink xlink:href="b2a4767c-03c7-4935-a3bc-df3e1a38a009">Property</legacyLink> objects by displaying field and property values for the <legacyBold><legacyItalic>Employees</legacyItalic></legacyBold> table.</para>
    <code>'BeginValueVB
Public Sub Main()
    On Error GoTo ErrorHandler

    'To integrate this code
    'replace the data source and initial catalog values
    'in the connection string

    ' connection and recordset variables
    Dim rstEmployees As ADODB.Recordset
    Dim Cnxn As ADODB.Connection
    Dim strCnxn As String
    Dim strSQLEmployees As String
     ' field property variables
    Dim fld As ADODB.Field
    Dim prp As ADODB.Property
    
     ' Open connection
    Set Cnxn = New ADODB.Connection
    strCnxn = "Provider='sqloledb';Data Source='MySqlServer';" &amp; _
        "Initial Catalog='Pubs';Integrated Security='SSPI';"
    Cnxn.Open strCnxn
    
    ' Open recordset with data from Employees table
    Set rstEmployees = New ADODB.Recordset
    strSQLEmployees = "employee"
    rstEmployees.Open strSQLEmployees, Cnxn, , , adCmdTable
    'rstEmployees.Open strSQLEmployees, Cnxn, adOpenStatic, adLockReadOnly, adCmdTable
    ' the above two lines of code are identical
     
    Debug.Print "Field values in rstEmployees"
    
    ' Enumerate the Fields collection of the Employees table
    For Each fld In rstEmployees.Fields
        ' Because Value is the default property of a
        ' Field object, the use of the actual keyword
        ' here is optional.
        Debug.Print "   " &amp; fld.Name &amp; " = " &amp; fld.Value
    Next fld
    
    Debug.Print "Property values in rstEmployees"
    
    ' Enumerate the Properties collection of the Recordset object
    For Each prp In rstEmployees.Properties
        Debug.Print "   " &amp; prp.Name &amp; " = " &amp; prp.Value
        ' because Value is the default property of a Property object
        ' use of the actual Value keyword is optional
    Next prp

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
'EndValueVB</code>
  </introduction>
  <relatedTopics>
<link xlink:href="b10a72fc-3c4b-4186-a70b-993dc9f7a092">Field Object</link>
<link xlink:href="b2a4767c-03c7-4935-a3bc-df3e1a38a009">Property Object</link>
<link xlink:href="48919c74-86d4-462e-99b9-8854ceb8d683">Value Property</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>