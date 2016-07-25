---
title: "Command and CommandText Properties Example (VB)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - VB
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 413263a8-05c0-4404-929d-69f82b987ba3
caps.latest.revision: 10
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
# Command and CommandText Properties Example (VB)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The following code demonstrates how to use the <legacyLink xlink:href="bcc9146f-586f-4e69-9c10-863440c9cffa">Command</legacyLink> property to update the text of a procedure.</para>
  </introduction>
  <section>
    <content>
      <code>' BeginProcedureTextVB
Sub Main()
    On Error GoTo ProcedureTextError
    
    Dim cnn As New ADODB.Connection
    Dim cat As New ADOX.Catalog
    Dim cmd As New ADODB.Command
    
    ' Open the connection.
    cnn.Open "Provider='Microsoft.Jet.OLEDB.4.0';" &amp; _
        "Data Source='Northwind.mdb';"
    
    ' Open the catalog.
    Set cat.ActiveConnection = cnn
    
    ' Get the command.
    Set cmd = cat.Procedures("CustomerById").Command

    ' Update the CommandText.
    cmd.CommandText = "Select CustomerId, CompanyName, ContactName " &amp; _
        "From Customers " &amp; _
        "Where CustomerId = [CustId]"
    
    ' Update the procedure.
    Set cat.Procedures("CustomerById").Command = cmd
    
    'Clean up.
    cnn.Close
    Set cat = Nothing
    Set cmd = Nothing
    Set cnn = Nothing
    Exit Sub
    
ProcedureTextError:
    Set cat = Nothing
    Set cmd = Nothing
    
    If Not cnn Is Nothing Then
        If cnn.State = adStateOpen Then cnn.Close
    End If
    Set cnn = Nothing
    
    If Err &lt;&gt; 0 Then
        MsgBox Err.Source &amp; "--&gt;" &amp; Err.Description, , "Error"
    End If
End Sub
' EndProcedureTextVB</code>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="25fff69b-7556-4a28-b6f5-600a4bb0f607">ActiveConnection Property</link>
<link xlink:href="bb651639-a488-4e38-b6de-0ed99fa4dd92">Catalog Object</link>
<link xlink:href="bcc9146f-586f-4e69-9c10-863440c9cffa">Command Property</link>
<link xlink:href="927bcf3e-32f5-4a80-98d3-600779f0732e">Procedure Object</link>
<link xlink:href="dc7a38e1-93b9-4034-9af2-ff419e8fb2a3">Procedures Collection</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>