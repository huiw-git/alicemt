---
title: "Procedures Append Method Example (VB)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - VB
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ce83b966-474b-4f57-8eb9-370996dfc5c0
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
# Procedures Append Method Example (VB)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The following code demonstrates how to use a <legacyLink xlink:href="a02c22fb-542d-465e-a629-30fd59dcbebf">Command</legacyLink> object and the <legacyLink xlink:href="dc7a38e1-93b9-4034-9af2-ff419e8fb2a3">Procedures</legacyLink> collection <legacyLink xlink:href="38e3492c-c1e1-42e3-a71a-befdc90204db">Append</legacyLink> method to create a new procedure in the underlying data source.</para>
  </introduction>
  <section>
    <content>
      <code>' BeginCreateProcedureVB
Sub Main()
    On Error GoTo CreateProcedureError

    Dim cnn As New ADODB.Connection
    Dim cmd As New ADODB.Command
    Dim prm As ADODB.Parameter
    Dim cat As New ADOX.Catalog
    
    ' Open the Connection
    cnn.Open _
        "Provider='Microsoft.Jet.OLEDB.4.0';" &amp; _
        "Data Source='Northwind.mdb';"
    
    ' Create the parameterized command (Microsoft Jet specific)
    Set cmd.ActiveConnection = cnn
    cmd.CommandText = "PARAMETERS [CustId] Text;" &amp; _
    "Select * From Customers Where CustomerId = [CustId]"
    
    ' Open the Catalog
    Set cat.ActiveConnection = cnn
    
    ' Create the new Procedure
    cat.Procedures.Append "CustomerById", cmd
    
    'Clean
    cnn.Close
    Set cat = Nothing
    Set cmd = Nothing
    Set cnn = Nothing
    Exit Sub
    
CreateProcedureError:
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
' EndCreateProcedureVB</code>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="25fff69b-7556-4a28-b6f5-600a4bb0f607">ActiveConnection Property</link>
<link xlink:href="38e3492c-c1e1-42e3-a71a-befdc90204db">Append Method (Procedures)</link>
<link xlink:href="bb651639-a488-4e38-b6de-0ed99fa4dd92">Catalog Object</link>
<link xlink:href="927bcf3e-32f5-4a80-98d3-600779f0732e">Procedure Object</link>
<link xlink:href="dc7a38e1-93b9-4034-9af2-ff419e8fb2a3">Procedures Collection</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>