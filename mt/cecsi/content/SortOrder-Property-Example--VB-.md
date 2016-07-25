---
title: "SortOrder Property Example (VB)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - VB
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d9502254-d89b-4bcb-94f1-6418f89e7f30
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
# SortOrder Property Example (VB)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This example demonstrates the <legacyLink xlink:href="04510b19-9cb2-4895-b23b-f7790123eb04">SortOrder</legacyLink> property of a <legacyLink xlink:href="6e772783-1bc8-4ea7-94b2-7d7a52ea5c47">Column</legacyLink> that has been appended to the <legacyLink xlink:href="23b9fea8-4f76-4a51-95ce-1a6ce4560b34">Columns</legacyLink> collection of an <legacyLink xlink:href="6b9578c0-bc94-46b9-b801-c18e14b04b31">Index</legacyLink>. The code appends an ascending index to the Country column in the <legacyBold>Employees</legacyBold> table, then displays the records. Then the code appends a descending index to the Country column in the <legacyBold>Employees</legacyBold> table and displays the records again. The difference between ascending and descending indexes is shown.</para>
  </introduction>
  <section>
    <content>
      <code>' BeginSortOrderVB
Sub Main()
    On Error GoTo SortOrderXError

    Dim cnn As New ADODB.Connection
    Dim catNorthwind As New ADOX.Catalog
    Dim idxAscending As New ADOX.Index
    Dim idxDescending As New ADOX.Index
    Dim rstEmployees As New ADODB.Recordset
        
    ' Connect to the catalog.
    cnn.Open "Provider='Microsoft.Jet.OLEDB.4.0';" &amp; _
        "Data Source='Northwind.mdb';"
    Set catNorthwind.ActiveConnection = cnn

    ' Append Country column to new index.
    idxAscending.Columns.Append "Country"
    idxAscending.Columns("Country").SortOrder = adSortAscending
    idxAscending.Name = "Ascending"
    idxAscending.IndexNulls = adIndexNullsAllow
    
    'Append new index to Employees table.
    catNorthwind.Tables("Employees").Indexes.Append idxAscending
    
    rstEmployees.Index = idxAscending.Name
    rstEmployees.Open "Employees", cnn, adOpenKeyset, _
        adLockOptimistic, adCmdTableDirect
        
    With rstEmployees
        .MoveFirst
        Debug.Print "Index = " &amp; .Index
        Debug.Print "  Country - Name"

        ' Enumerate the Recordset. The value of the
        ' IndexNulls property will determine if the newly
        ' added record appears in the output.
        Do While Not .EOF
            Debug.Print "    " &amp; !Country &amp; " - " &amp; _
                !FirstName &amp; " " &amp; !LastName
            .MoveNext
        Loop

        .Close
    End With

    ' Append Country column to new index.
    idxDescending.Columns.Append "Country"
    idxDescending.Columns("Country").SortOrder = adSortDescending
    idxDescending.Name = "Descending"
    idxDescending.IndexNulls = adIndexNullsAllow
    
    'Append descending index to Employees table.
    catNorthwind.Tables("Employees").Indexes.Append idxDescending
    
    rstEmployees.Index = idxDescending.Name
    rstEmployees.Open "Employees", cnn, adOpenKeyset, _
        adLockOptimistic, adCmdTableDirect
                
    With rstEmployees
        .MoveFirst
        Debug.Print "Index = " &amp; .Index
        Debug.Print "  Country - Name"
        
        ' Enumerate the Recordset. The value of the
        ' IndexNulls property will determine if the newly
        ' added record appears in the output.
        Do While Not .EOF
            Debug.Print "    " &amp; !Country &amp; " - " &amp; _
                !FirstName &amp; " " &amp; !LastName
            .MoveNext
        Loop
        
        .Close
    End With
       
    ' Delete new indexes because this is a demonstration.
    catNorthwind.Tables("Employees").Indexes.Delete idxAscending.Name
    catNorthwind.Tables("Employees").Indexes.Delete idxDescending.Name
    
    'Clean up
    cnn.Close
    Set catNorthwind = Nothing
    Set idxAscending = Nothing
    Set idxDescending = Nothing
    Set rstEmployees = Nothing
    Set cnn = Nothing
    Exit Sub
    
SortOrderXError:
    
    Set catNorthwind = Nothing
    Set idxAscending = Nothing
    Set idxDescending = Nothing

    If Not rstEmployees Is Nothing Then
        If rstEmployees.State = adStateOpen Then rstEmployees.Close
    End If
    Set rstEmployees = Nothing
    
    If Not cnn Is Nothing Then
        If cnn.State = adStateOpen Then cnn.Close
    End If
    Set cnn = Nothing
    
    If Err &lt;&gt; 0 Then
        MsgBox Err.Source &amp; "--&gt;" &amp; Err.Description, , "Error"
    End If
End Sub
' EndSortOrderVB</code>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="6e772783-1bc8-4ea7-94b2-7d7a52ea5c47">Column Object</link>
<link xlink:href="23b9fea8-4f76-4a51-95ce-1a6ce4560b34">Columns Collection</link>
<link xlink:href="6b9578c0-bc94-46b9-b801-c18e14b04b31">Index Object</link>
<link xlink:href="04510b19-9cb2-4895-b23b-f7790123eb04">SortOrder Property</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>