---
title: "Command Object Parameters"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 10e7ef4a-78bf-4e91-931e-cbc6c065dd4c
caps.latest.revision: 13
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
# Command Object Parameters
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The previous topic discussed <legacyLink xlink:href="0b81af6f-b9ae-4f7c-b59b-b5bdd775036f">Creating and Executing a Simple Command</legacyLink>. A more interesting use for the <legacyLink xlink:href="a02c22fb-542d-465e-a629-30fd59dcbebf">Command</legacyLink> object is shown in the next example, in which the SQL command has been parameterized. This modification makes it possible to reuse the command, passing in a different value for the parameter each time. Because the <legacyLink xlink:href="11ca8825-765e-4bb4-a6ce-3f6564ad8755">Prepared Property</legacyLink> property on the <unmanagedCodeEntityReference>Command</unmanagedCodeEntityReference> object is set to <languageKeyword>true</languageKeyword>, ADO will require the provider to compile the command specified in <legacyLink xlink:href="4dd7e82a-8da5-4a4e-b439-11a29286fa0e">CommandText</legacyLink> before executing it for the first time. It also will retain the compiled command in memory. This slows the execution of the command slightly the first time it is executed because of the overhead required to prepare it, but results in a performance gain each time the command is called thereafter. Therefore, commands should be prepared only if they will be used more than one time.</para>
    <code>'BeginManualParamCmd
    On Error GoTo ErrHandler:

    Dim objConn As New ADODB.Connection
    Dim objCmd As New ADODB.Command
    Dim objParm1 As New ADODB.Parameter
    Dim objRs As New ADODB.Recordset
    
    ' Set the CommandText as a parameterized SQL query.
    objCmd.CommandText = "SELECT OrderID, OrderDate, " &amp; _
                         "RequiredDate, ShippedDate " &amp; _
                         "FROM Orders " &amp; _
                         "WHERE CustomerID = ? " &amp; _
                         "ORDER BY OrderID"
    objCmd.CommandType = adCmdText
        
    ' Prepare command because we will be executing it more than once.
    objCmd.Prepared = True
        
    ' Create new parameter for CustomerID. Initial value is ALFKI.
    Set objParm1 = objCmd.CreateParameter("CustId", adChar, _
                    adParamInput, 5, "ALFKI")
    objCmd.Parameters.Append objParm1
        
    ' Connect to the data source.
    Set objConn = GetNewConnection
    objCmd.ActiveConnection = objConn
        
    ' Execute once and display.
    Set objRs = objCmd.Execute
        
    Debug.Print objParm1.Value
    Do While Not objRs.EOF
        Debug.Print vbTab &amp; objRs(0) &amp; vbTab &amp; objRs(1) &amp; vbTab &amp; _
                    objRs(2) &amp; vbTab &amp; objRs(3)
        objRs.MoveNext
    Loop
        
    ' .Set new param value, re-execute command, and display.
    objCmd("CustId") = "CACTU"
    Set objRs = objCmd.Execute
        
    Debug.Print objParm1.Value
    Do While Not objRs.EOF
        Debug.Print vbTab &amp; objRs(0) &amp; vbTab &amp; objRs(1) &amp; vbTab &amp; _
                    objRs(2) &amp; vbTab &amp; objRs(3)
        objRs.MoveNext
    Loop
        
    'clean up
    objRs.Close
    objConn.Close
    Set objRs = Nothing
    Set objConn = Nothing
    Set objCmd = Nothing
    Set objParm1 = Nothing
    Exit Sub
    
ErrHandler:
    'clean up
    If objRs.State = adStateOpen Then
        objRs.Close
    End If
    
    If objConn.State = adStateOpen Then
        objConn.Close
    End If
    
    Set objRs = Nothing
    Set objConn = Nothing
    Set objCmd = Nothing
    Set objParm1 = Nothing
    
    If Err &lt;&gt; 0 Then
        MsgBox Err.Source &amp; "--&gt;" &amp; Err.Description, , "Error"
    End If
'EndManualParamCmd


'BeginNewConnection
Private Function GetNewConnection() As ADODB.Connection
    Dim oCn As New ADODB.Connection
    Dim sCnStr As String
    
    sCnStr = "Provider='SQLOLEDB';Data Source='MySqlServer';" &amp; _
             "Integrated Security='SSPI';Initial Catalog='Northwind';"
    oCn.Open sCnStr
    
    If oCn.State = adStateOpen Then
        Set GetNewConnection = oCn
    End If
    
End Function
'EndNewConnection</code>
    <para>Not all providers support prepared commands. If the provider does not support command preparation, it might return an error as soon as this property is set to <languageKeyword>True</languageKeyword>. If it does not return an error, it ignores the request to prepare the command and sets the <unmanagedCodeEntityReference>Prepared</unmanagedCodeEntityReference> property to <languageKeyword>false</languageKeyword>.</para>
  </introduction>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>