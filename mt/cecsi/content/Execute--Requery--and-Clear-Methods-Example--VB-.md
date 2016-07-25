---
title: "Execute, Requery, and Clear Methods Example (VB)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - VB
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ed5e1b60-3769-4b26-a253-1d721e37941d
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
# Execute, Requery, and Clear Methods Example (VB)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This example demonstrates the <legacyBold>Execute</legacyBold> method when run from both a <legacyLink xlink:href="a02c22fb-542d-465e-a629-30fd59dcbebf">Command</legacyLink> object and a <legacyLink xlink:href="ef6b1824-5b12-43db-89d7-8f3d13896d4d">Connection</legacyLink> object. It also uses the <legacyLink xlink:href="d81ab76f-1aa8-4ccf-92ec-b65254dc3ea1">Requery</legacyLink> method to retrieve current data in a <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink>, and the <legacyLink xlink:href="0a61ba7a-20b8-426a-91a0-9040e7c5a98a">Clear</legacyLink> method to clear the contents of the <legacyLink xlink:href="290819e1-7b39-4e1e-a93b-801257138b00">Errors</legacyLink> collection. (The <legacyBold>Errors</legacyBold> collection is accessed via the <legacyBold>Connection</legacyBold> object of the <legacyLink xlink:href="52d0a96c-14fb-4ad9-b004-4d821bc0a6db">ActiveConnection</legacyLink> property of the <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink>.) The ExecuteCommand and PrintOutput procedures are required for this procedure to run.</para>
    <code>'BeginExecuteVB
    
    'To integrate this code
    'replace the data source and initial catalog values
    'in the connection string

Public Sub Main()
    On Error GoTo Err_Execute

    ' connection, command, and recordset variables
    Dim Cnxn As ADODB.Connection
    Dim cmdChange As ADODB.Command
    Dim rstTitles As ADODB.Recordset
    Dim Err As ADODB.Error
    Dim strSQLChange As String
    Dim strSQLRestore As String
    Dim strSQLTitles
    Dim strCnxn As String
    
     ' Define two SQL statements to execute as command text
    strSQLChange = "UPDATE Titles SET Type = 'self_help' WHERE Type = 'psychology'"
    strSQLRestore = "UPDATE Titles SET Type = 'psychology' WHERE Type = 'self_help'"
    
     ' Open connection
    strCnxn = "Provider='sqloledb';Data Source='MySqlServer';" &amp; _
        "Initial Catalog='Pubs';Integrated Security='SSPI';"
    Set Cnxn = New ADODB.Connection
    Cnxn.Open strCnxn
    
     ' Create command object
    Set cmdChange = New ADODB.Command
    Set cmdChange.ActiveConnection = Cnxn
    cmdChange.CommandText = strSQLChange
    
     ' Open titles table
    Set rstTitles = New ADODB.Recordset
    strSQLTitles = "titles"
    rstTitles.Open strSQLTitles, Cnxn, , , adCmdTable
    
    ' Print report of original data
    Debug.Print _
       "Data in Titles table before executing the query"
    PrintOutput rstTitles
    
    ' Call the ExecuteCommand subroutine below to execute cmdChange command
    ExecuteCommand cmdChange, rstTitles
    
    ' Print report of new data
    Debug.Print _
       "Data in Titles table after executing the query"
    PrintOutput rstTitles
    
    ' Use the Connection object's execute method to
    ' execute SQL statement to restore data and trap for
    ' errors, checking the Errors collection if necessary
    Cnxn.Execute strSQLRestore, , adExecuteNoRecords
    
    ' Retrieve the current data by requerying the recordset
    rstTitles.Requery
    
    ' Print report of restored data using sub from below
    Debug.Print "Data after executing the query to restore the original information "
    PrintOutput rstTitles

    ' clean up
    rstTitles.Close
    Cnxn.Close
    Set rstTitles = Nothing
    Set Cnxn = Nothing
    Exit Sub
   
Err_Execute:
    ' Notify user of any errors that result from
    ' executing the query
    If rstTitles.ActiveConnection.Errors.Count &gt;= 0 Then
       For Each Err In rstTitles.ActiveConnection.Errors
          MsgBox "Error number: " &amp; Err.Number &amp; vbCr &amp; _
             Err.Description
       Next Err
    End If
   
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

Public Sub ExecuteCommand(cmdTemp As ADODB.Command, rstTemp As ADODB.Recordset)

   Dim Err As Error
   
   ' Run the specified Command object and trap for
   ' errors, checking the Errors collection
   On Error GoTo Err_Execute
   cmdTemp.Execute
   On Error GoTo 0

   ' Retrieve the current data by requerying the recordset
   rstTemp.Requery
   
   Exit Sub

Err_Execute:

   ' Notify user of any errors that result from
   ' executing the query
   If rstTemp.ActiveConnection.Errors.Count &gt; 0 Then
      For Each Err In rstTemp.ActiveConnection.Errors
         MsgBox "Error number: " &amp; Err.Number &amp; vbCr &amp; _
            Err.Description
      Next Err
   End If
   
   Resume Next

End Sub

Public Sub PrintOutput(rstTemp As ADODB.Recordset)

   ' Enumerate Recordset
   Do While Not rstTemp.EOF
      Debug.Print "  " &amp; rstTemp!Title &amp; _
         ", " &amp; rstTemp!Type
      rstTemp.MoveNext
   Loop

End Sub
'EndExecuteVB</code>
  </introduction>
  <relatedTopics>
<link xlink:href="0a61ba7a-20b8-426a-91a0-9040e7c5a98a">Clear Method</link>
<link xlink:href="a02c22fb-542d-465e-a629-30fd59dcbebf">Command Object</link>
<link xlink:href="ef6b1824-5b12-43db-89d7-8f3d13896d4d">Connection Object</link>
<link xlink:href="a175d453-fa55-4f49-9ede-a26d83177919">Error Object</link>
<link xlink:href="f84a5ff3-0528-4ad7-9bea-9a15103378dd">Execute Method (ADO Command)</link>
<link xlink:href="03c69320-96b2-4d85-8d49-a13b13e31578">Execute Method (ADO Connection)</link>
<link xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset Object</link>
<link xlink:href="d81ab76f-1aa8-4ccf-92ec-b65254dc3ea1">Requery Method</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>