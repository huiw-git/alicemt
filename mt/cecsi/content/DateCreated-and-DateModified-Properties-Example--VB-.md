---
title: "DateCreated and DateModified Properties Example (VB)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - VB
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d608ea35-6e68-402f-8184-a5041e408678
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
# DateCreated and DateModified Properties Example (VB)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This example demonstrates the <legacyLink xlink:href="2bf4b00d-045c-444e-8af7-8af6297ed418">DateCreated</legacyLink> and <legacyLink xlink:href="fed09266-1547-4bda-9088-c254d81cc738">DateModified</legacyLink> properties by adding a new <legacyLink xlink:href="6e772783-1bc8-4ea7-94b2-7d7a52ea5c47">Column</legacyLink> to an existing <legacyLink xlink:href="a6d74000-0828-49ba-850a-63da865f8802">Table</legacyLink> and by creating a new <legacyBold>Table</legacyBold>. The DateOutput procedure is required for this example to run.</para>
  </introduction>
  <section>
    <content>
      <code>' BeginDateCreatedVB
Sub Main()
    On Error GoTo DateCreatedXError
    
    Dim cat As New ADOX.Catalog
    Dim tblEmployees As ADOX.Table
    Dim tblNewTable As ADOX.Table

    ' Connect to the catalog.
    cat.ActiveConnection = "Provider='Microsoft.Jet.OLEDB.4.0';" &amp; _
        "Data Source='Northwind.mdb';"
    
    With cat
        Set tblEmployees = .Tables("Employees")
        
        ' Print current information about the Employees table.
        DateOutput "Current properties", tblEmployees
        
        ' Create and append column to the Employees table.
        tblEmployees.Columns.Append "NewColumn", adInteger
        .Tables.Refresh
        
        ' Print new information about the Employees table.
        DateOutput "After creating a new column", tblEmployees
        
        ' Delete new column because this is a demonstration.
        tblEmployees.Columns.Delete "NewColumn"
     
        ' Create and append new Table object to the Northwind database.
        Set tblNewTable = New ADOX.Table
        tblNewTable.Name = "NewTable"
        tblNewTable.Columns.Append "NewColumn", adInteger
        .Tables.Append tblNewTable
        .Tables.Refresh
        
        ' Print information about the new Table object.
        DateOutput "After creating a new table", .Tables("NewTable")
        
        ' Delete new Table object because this is a demonstration.
        .Tables.Delete tblNewTable.Name
    End With

    'Clean up.
    Set cat.ActiveConnection = Nothing
    Set cat = Nothing
    Exit Sub
    
DateCreatedXError:
    Set cat = Nothing
    
    If Err &lt;&gt; 0 Then
        MsgBox Err.Source &amp; "--&gt;" &amp; Err.Description, , "Error"
    End If

End Sub

Sub DateOutput(strTemp As String, tblTemp As ADOX.Table)
    ' Print DateCreated and DateModified information about
    ' specified Table object.
    Debug.Print strTemp
    Debug.Print "    Table: " &amp; tblTemp.Name
    Debug.Print "        DateCreated = " &amp; tblTemp.DateCreated
    Debug.Print "        DateModified = " &amp; tblTemp.DateModified
    Debug.Print
End Sub
' EndDateCreatedVB</code>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="2bf4b00d-045c-444e-8af7-8af6297ed418">DateCreated Property</link>
<link xlink:href="fed09266-1547-4bda-9088-c254d81cc738">DateModified Property</link>
<link xlink:href="927bcf3e-32f5-4a80-98d3-600779f0732e">Procedure Object</link>
<link xlink:href="dc7a38e1-93b9-4034-9af2-ff419e8fb2a3">Procedures Collection</link>
<link xlink:href="653421ce-7b94-43d0-9bc6-4900f8f2af45">View Object</link>
<link xlink:href="a55d380c-2b7b-4b57-af74-8ba0b3de0db9">Views Collection</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>