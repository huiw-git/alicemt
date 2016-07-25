---
title: "Type Property Example (Field) (VB)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - VB
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: accb72f5-a3bd-4a7e-92b6-6da0783b4b75
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
# Type Property Example (Field) (VB)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This example demonstrates the <legacyLink xlink:href="8a4c079f-9f4f-4545-801d-85983b8db71e">Type</legacyLink> property by displaying the name of the constant that corresponds to the value of the <legacyLink xlink:href="8a4c079f-9f4f-4545-801d-85983b8db71e">Type</legacyLink> property of all the <legacyLink xlink:href="b10a72fc-3c4b-4186-a70b-993dc9f7a092">Field</legacyLink> objects in the <legacyBold><legacyItalic>Employees</legacyItalic></legacyBold> table. The FieldType function is required for this procedure to run.</para>
    <code>'BeginTypeFieldVB
Public Sub Main()
    On Error GoTo ErrorHandler

    'To integrate this code
    'replace the data source and initial catalog values
    'in the connection string
   
    Dim Cnxn As ADODB.Connection
    Dim rstEmployees As ADODB.Recordset
    Dim fld As ADODB.Field
    Dim strCnxn As String
    Dim strSQLEmployee As String
    Dim FieldType As String
    
    ' Open connection
    Set Cnxn = New ADODB.Connection
    strCnxn = "Provider='sqloledb';Data Source='MySqlServer';" &amp; _
        "Initial Catalog='Pubs';Integrated Security='SSPI';"
    Cnxn.Open strCnxn
     
    ' Open recordset with data from Employees table
    Set rstEmployees = New ADODB.Recordset
    strSQLEmployee = "employee"
    rstEmployees.Open strSQLEmployee, Cnxn, , , adCmdTable
    'rstEmployees.Open strSQLEmployee, Cnxn, adOpenStatic, adLockReadOnly, adCmdTable
     ' the above two lines of code are identical
    
    Debug.Print "Fields in Employees Table:" &amp; vbCr
    
    ' Enumerate Fields collection of Employees table
    For Each fld In rstEmployees.Fields
        ' translate field-type code to text
        Select Case fld.Type
            Case adChar
               FieldType = "adChar"
            Case adVarChar
               FieldType = "adVarChar"
            Case adSmallInt
               FieldType = "adSmallInt"
            Case adUnsignedTinyInt
               FieldType = "adUnsignedTinyInt"
            Case adDBTimeStamp
               FieldType = "adDBTimeStamp"
        End Select
        ' show results
        Debug.Print "  Name: " &amp; fld.Name &amp; vbCr &amp; _
          "  Type: " &amp; FieldType &amp; vbCr
    Next fld
    
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
    
    Set fld = Nothing
    
    If Err &lt;&gt; 0 Then
        MsgBox Err.Source &amp; "--&gt;" &amp; Err.Description, , "Error"
    End If
End Sub
'EndTypeFieldVB


Attribute VB_Name = "TypeField"</code>
  </introduction>
  <relatedTopics>
<link xlink:href="b10a72fc-3c4b-4186-a70b-993dc9f7a092">Field Object</link>
<link xlink:href="8a4c079f-9f4f-4545-801d-85983b8db71e">Type Property</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>