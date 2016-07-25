---
title: "AddNew Method Example (VB)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - VB
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d439e097-65f3-471d-8799-5a1263beb3c1
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
# AddNew Method Example (VB)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This example uses the <legacyLink xlink:href="a9f54be9-5763-45d0-a6eb-09981b03bc08">AddNew</legacyLink> method to create a new record with the specified name.</para>
    <code>'BeginAddNewVB

    'To integrate this code
    'replace the data source and initial catalog values
    'in the connection string

Public Sub Main()
    On Error GoTo ErrorHandler

    'recordset and connection variables
    Dim Cnxn As ADODB.Connection
    Dim rstEmployees As ADODB.Recordset
    Dim strCnxn As String
    Dim strSQL As String
     'record variables
    Dim strID As String
    Dim strFirstName As String
    Dim strLastName As String
    Dim blnRecordAdded As Boolean

    ' Open a connection
    Set Cnxn = New ADODB.Connection
    strCnxn = "Provider='sqloledb';Data Source='MySqlServer';" &amp; _
        "Initial Catalog='Northwind';Integrated Security='SSPI';"
    Cnxn.Open strCnxn
       
    ' Open Employees Table with a cursor that allows updates
    Set rstEmployees = New ADODB.Recordset
    strSQL = "Employees"
    rstEmployees.Open strSQL, strCnxn, adOpenKeyset, adLockOptimistic, adCmdTable
    
    ' Get data from the user
    strFirstName = Trim(InputBox("Enter first name:"))
    strLastName = Trim(InputBox("Enter last name:"))
    
    ' Proceed only if the user actually entered something
    ' for both the first and last names
    If strFirstName &lt;&gt; "" And strLastName &lt;&gt; "" Then
    
        rstEmployees.AddNew
        rstEmployees!firstname = strFirstName
        rstEmployees!LastName = strLastName
        rstEmployees.Update
        blnRecordAdded = True
        
        ' Show the newly added data
        MsgBox "New record: " &amp; rstEmployees!EmployeeId &amp; " " &amp; _
        rstEmployees!firstname &amp; " " &amp; rstEmployees!LastName
        
    Else
        MsgBox "Please enter a first name and last name."
    End If
          
    ' Delete the new record because this is a demonstration
    Cnxn.Execute "DELETE FROM Employees WHERE EmployeeID = '" &amp; strID &amp; "'"
     
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
'EndAddNewVB</code>
  </introduction>
  <relatedTopics>
<link xlink:href="a9f54be9-5763-45d0-a6eb-09981b03bc08">AddNew Method</link>
<link xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset Object</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>