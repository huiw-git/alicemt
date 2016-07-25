---
title: "ConvertToString Method Example (VB)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - VB
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 31731e4f-3c0c-451e-8cbc-c9df28fabf6c
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
# ConvertToString Method Example (VB)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <code>'BeginConvertToStringVB

    'To integrate this code
    'replace the data source and initial catalog values
    'in the connection string
    
Public Sub Main()
    On Error GoTo ErrorHandler

     ' to integrate this code replace the server name
     ' in the CreateObject call

     ' RDS variables
    Dim rdsDS As RDS.DataSpace
    Dim rdsDC As RDS.DataControl
    Dim rdsDF As Object
     ' recordset and connection variables
    Dim rsAuthors As ADODB.Recordset
    Dim strSQLAuthors As String
    Dim strCnxn As String
    Dim varString As Variant

     ' Create a DataSpace object
    Set rdsDS = New RDS.DataSpace
     ' Create a DataFactory object
    Set rdsDF = rdsDS.CreateObject("RDSServer.DataFactory", "http://MyServer") 'MyServer

     ' Get all of the Author records
    
    strCnxn = "Provider='sqloledb';Data Source='MySqlServer';" &amp; _
        "Initial Catalog='Pubs';Integrated Security='SSPI';"
    strSQLAuthors = "SELECT * FROM Authors"
    Set rsAuthors = rdsDF.Query(strCnxn, strSQLAuthors)
     ' Show results
    Debug.Print "Old RDS recordset count:" &amp; rsAuthors.RecordCount

     ' Convert the recordset into a MIME formatted string
    varString = rdsDF.ConvertToString(rsAuthors)
    Debug.Print "Recordset as MIME format string:"
    Debug.Print varString
    
     ' Convert string value back into an ADO Recordset
    Set rdsDC = New RDS.DataControl
    rdsDC.SQL = varString
    rdsDC.ExecuteOptions = adcExecSync
    rdsDC.FetchOptions = adcFetchUpFront
    rdsDC.Refresh
     ' Show results
    Debug.Print "New ADO recordset count:" &amp; rdsDC.Recordset.RecordCount
     
     ' clean up
    rsAuthors.Close
    Set rsAuthors = Nothing
    Set rdsDC = Nothing
    Set rdsDS = Nothing
    Set rdsDC = Nothing
    
ErrorHandler:
    
    If Not rsAuthors Is Nothing Then
        If rsAuthors.State = adStateOpen Then rsAuthors.Close
    End If
    Set rsAuthors = Nothing
    Set rdsDC = Nothing
    Set rdsDS = Nothing
    Set rdsDC = Nothing
    
    If Err &lt;&gt; 0 Then
        MsgBox Err.Source &amp; "--&gt;" &amp; Err.Description, , "Error"
    End If
    
End Sub
'EndConvertToStringVB</code>
  </introduction>
  <relatedTopics>
<link xlink:href="b3f36bc8-6f69-49b0-83cd-2ccd3afebfbe">ConvertToString Method (RDS)</link>
<link xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset Object</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>