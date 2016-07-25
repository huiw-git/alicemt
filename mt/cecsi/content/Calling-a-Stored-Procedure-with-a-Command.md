---
title: "Calling a Stored Procedure with a Command"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 685f7652-2271-4ede-b552-2eeb8c756b4c
caps.latest.revision: 14
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
# Calling a Stored Procedure with a Command
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>You can use a command to call a stored procedure. The code sample at the end of this topic refers to a stored procedure in the Northwind sample database, called CustOrdersOrders, which is defined as follows.</para>
    <code>CREATE PROCEDURE CustOrdersOrders @CustomerID nchar(5) AS
SELECT OrderID, OrderDate, RequiredDate, ShippedDate
FROM Orders
WHERE CustomerID = @CustomerID
ORDER BY OrderID</code>
    <para>See your SQL Server documentation for more information about how to define and call stored procedures.</para>
    <para>This stored procedure is similar to the command used in <legacyLink xlink:href="10e7ef4a-78bf-4e91-931e-cbc6c065dd4c">Command Object Parameters</legacyLink>. It takes a customer ID parameter and returns information about that customer's orders. The following code sample uses this stored procedure as the source for an ADO <legacyBold>Recordset</legacyBold>.</para>
    <para>Using the stored procedure allows you to access another capability of ADO: the <legacyBold>Parameters</legacyBold> collection <legacyBold>Refresh</legacyBold> method. By using this method, ADO can automatically fill in all information about the parameters required by the command at run time. There is a performance penalty in using this technique, because ADO must query the data source for the information about the parameters.</para>
    <para>Other important differences exist between the following code sample and the code in <legacyLink xlink:href="10e7ef4a-78bf-4e91-931e-cbc6c065dd4c">Command Object Parameters</legacyLink>, where the parameters were entered manually. First, this code does not set the <legacyBold>Prepared</legacyBold> property to <legacyBold>True</legacyBold> because it is a SQL Server stored procedure and is precompiled by definition. Second, the <legacyBold>CommandType</legacyBold> property of the <legacyBold>Command</legacyBold> object changed to <legacyBold>adCmdStoredProc</legacyBold> in the second example to inform ADO that the command was a stored procedure.</para>
    <para>Finally, in the second example the parameter must be referred to by index when setting the value, because you might not know the name of the parameter at design time. If you do know the name of the parameter, you can set the new <legacyLink xlink:href="42409387-026c-435f-a9b1-bf4167095875">NamedParameters</legacyLink> property of the <legacyBold>Command</legacyBold> object to True and refer to the property's name. You might wonder why the position of the first parameter mentioned in the stored procedure (@CustomerID) is 1 instead of 0 (<codeInline>objCmd(1) = "ALFKI"</codeInline>). This is because parameter 0 contains a return value from the SQL Server stored procedure.</para>
    <code>'BeginAutoParamCmd
    On Error GoTo ErrHandler:
    
    Dim objConn As New ADODB.Connection
    Dim objCmd As New ADODB.Command
    Dim objParm1 As New ADODB.Parameter
    Dim objRs As New ADODB.Recordset
    
    ' Set CommandText equal to the stored procedure name.
    objCmd.CommandText = "CustOrdersOrders"
    objCmd.CommandType = adCmdStoredProc
            
    ' Connect to the data source.
    Set objConn = GetNewConnection
    objCmd.ActiveConnection = objConn
        
    ' Automatically fill in parameter info from stored procedure.
    objCmd.Parameters.Refresh
    
    ' Set the param value.
    objCmd(1) = "ALFKI"
    
    ' Execute once and display...
    Set objRs = objCmd.Execute
        
    Debug.Print objParm1.Value
    Do While Not objRs.EOF
        Debug.Print vbTab &amp; objRs(0) &amp; vbTab &amp; objRs(1) &amp; vbTab &amp; _
                    objRs(2) &amp; vbTab &amp; objRs(3)
        objRs.MoveNext
    Loop
        
    ' ...then set new param value, re-execute command, and display.
    objCmd(1) = "CACTU"
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
'EndAutoParamCmd


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
  </introduction>
  <relatedTopics>
<externalLink><linkText>Knowledge Base article 117500</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=117500</linkUri></externalLink>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>