---
title: "Creating and Executing a Simple Command"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0b81af6f-b9ae-4f7c-b59b-b5bdd775036f
caps.latest.revision: 8
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
# Creating and Executing a Simple Command
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>A simple command is one that is not parameterized and requires no persistence. There are three ways to create and execute a simple command.

</para>
    <list class="bullet">
      <listItem>
        <para>Using a <legacyBold>Command</legacyBold> object</para>
      </listItem>
      <listItem>
        <para>Using a <legacyBold>Connection</legacyBold> object</para>
      </listItem>
      <listItem>
        <para>Using a <legacyBold>Recordset</legacyBold> object</para>
      </listItem>
    </list>
  </introduction>
  <section>
    <title>Using a Command object</title>
    <content>
      <para>To create a simple command using a <legacyBold>Command</legacyBold> object, you must assign the instruction to the <legacyBold>CommandText</legacyBold> property of a <legacyBold>Command</legacyBold> object and set the appropriate value for the <legacyBold>CommandType</legacyBold> property. Executing the command requires that an open connection is assigned to the <legacyBold>ActiveConnection</legacyBold> property of the <legacyBold>Command</legacyBold> object, followed by a call to the <legacyBold>Execute</legacyBold> method on the <legacyBold>Command</legacyBold> object. </para>
      <para>The following code snippet shows the basic method of using the <legacyBold>Command</legacyBold> object to execute a command against a data source. This example uses a row-returning command, and returns the results of the command execution as a <legacyBold>Recordset</legacyBold> object.</para>
      <code>    'BeginBasicCmd
    On Error GoTo ErrHandler:
    
    Dim objConn As New ADODB.Connection
    Dim objCmd As New ADODB.Command
    Dim objRs As New ADODB.Recordset
    
    objCmd.CommandText = "SELECT OrderID, OrderDate, " &amp; _
                         "RequiredDate, ShippedDate " &amp; _
                         "FROM Orders " &amp; _
                         "WHERE CustomerID = 'ALFKI' " &amp; _
                         "ORDER BY OrderID"
    objCmd.CommandType = adCmdText
    
    ' Connect to the data source.
    Set objConn = GetNewConnection
    objCmd.ActiveConnection = objConn
    
    ' Execute once and display...
    Set objRs = objCmd.Execute
    
    Debug.Print "ALFKI"
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
    
    If Err &lt;&gt; 0 Then
        MsgBox Err.Source &amp; "--&gt;" &amp; Err.Description, , "Error"
    End If
'EndBasicCmd


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
    </content>
  </section>
  <section>
    <title>Using a Recordset object</title>
    <content>
      <para>You can also create a command as a text string and pas it to the <legacyBold>Open</legacyBold> method on a <legacyBold>Recordset</legacyBold> object, together with the command type (adCmdText), for execution. The following code snippet demonstrate this.</para>
      <code>    
    Const DS = "MySqlServer"
    Const DB = "Northwind"
    Const DP = "SQLOLEDB"
    
    Dim objRs As New ADODB.Recordset
    Dim CommandText As String
    Dim ConnctionString As String
    
    CommandText = "SELECT OrderID, OrderDate, " &amp; _
                         "RequiredDate, ShippedDate " &amp; _
                         "FROM Orders " &amp; _
                         "WHERE CustomerID = 'ALFKI' " &amp; _
                         "ORDER BY OrderID"
    ConnectionString = "Provider=" &amp; DP &amp; _
                       ";Data Source=" &amp; DS &amp; _
                       ";Initial Catalog=" &amp; DB &amp; _
                       ";Integrated Security=SSPI;"
    
    ' Connect to data source and execute the SQL command.
    objRs.Open <codeFeaturedElement>CommandText</codeFeaturedElement>, ConnectionString, _
                adOpenStatic, adLockReadOnly, <codeFeaturedElement>adCmdText</codeFeaturedElement>
    
    Debug.Print "ALFKI"
    Do While Not objRs.EOF
        Debug.Print vbTab &amp; objRs(0) &amp; vbTab &amp; objRs(1) &amp; vbTab &amp; _
                    objRs(2) &amp; vbTab &amp; objRs(3)
        objRs.MoveNext
    Loop
    
    'Clean up.
    objRs.Close
    Set objRs = Nothing</code>
    </content>
  </section>
  <section>
    <title>Using a Connection object</title>
    <content>
      <para>You can also execute a command on an open Connection object. The previous code example now becomes this:</para>
      <code>    Const DS = "MySqlServer"
    Const DB = "Northwind"
    Const DP = "SQLOLEDB"
    
    
    Dim objConn As New ADODB.Connection
    Dim objRs As New ADODB.Recordset
    
    CommandText = "SELECT OrderID, OrderDate, " &amp; _
                         "RequiredDate, ShippedDate " &amp; _
                         "FROM Orders " &amp; _
                         "WHERE CustomerID = 'ALFKI' " &amp; _
                         "ORDER BY OrderID"
                         
    ConnectionString = "Provider=" &amp; DP &amp; _
                       ";Data Source=" &amp; DS &amp; _
                       ";Initial Catalog=" &amp; DB &amp; _
                       ";Integrated Security=SSPI;"
    
    ' Connect to the data source.
    objConn.Open ConnectionString
    
    ' Execute command through the connection and display...
    Set objRs = objConn.Execute(<codeFeaturedElement>CommandText</codeFeaturedElement>)
    
    Debug.Print "ALFKI"
    Do While Not objRs.EOF
        Debug.Print vbTab &amp; objRs(0) &amp; vbTab &amp; objRs(1) &amp; vbTab &amp; _
                    objRs(2) &amp; vbTab &amp; objRs(3)
        objRs.MoveNext
    Loop
    
    'Clean up.
    objRs.Close
    objConn.Close
    Set objRs = Nothing
    Set objConn = Nothing</code>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>