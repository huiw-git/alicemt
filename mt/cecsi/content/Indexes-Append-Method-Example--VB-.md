---
title: "Indexes Append Method Example (VB)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - VB
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 50f87e27-1bf9-427c-9b1d-704a672434d2
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
# Indexes Append Method Example (VB)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The following code demonstrates how to create a new index. The index is on two columns in the table.</para>
  </introduction>
  <section>
    <content>
      <code>Attribute VB_Name = "IndexesAppend"
Option Explicit

' BeginCreateIndexVB
Sub Main()
    On Error GoTo CreateIndexError

    Dim tbl As New Table
    Dim idx As New ADOX.Index
    Dim cat As New ADOX.Catalog
    
    'Open the catalog.
    cat.ActiveConnection = "Provider='Microsoft.Jet.OLEDB.4.0';" &amp; _
        "Data Source='Northwind.mdb';"
    
    ' Define the table and append it to the catalog.
    tbl.Name = "MyTable"
    tbl.Columns.Append "Column1", adInteger
    tbl.Columns.Append "Column2", adInteger
    tbl.Columns.Append "Column3", adVarWChar, 50
    cat.Tables.Append tbl
    Debug.Print "Table 'MyTable' is added."
    
    ' Define a multi-column index.
    idx.Name = "multicolidx"
    idx.Columns.Append "Column1"
    idx.Columns.Append "Column2"
    
    ' Append the index to the table.
    tbl.Indexes.Append idx
    Debug.Print "The index is appended to table 'MyTable'."
    
    'Delete the table as this is a demonstration.
    cat.Tables.Delete tbl.Name
    Debug.Print "Table 'MyTable' is deleted."
    
    'Clean up.
    Set cat.ActiveConnection = Nothing
    Set cat = Nothing
    Set tbl = Nothing
    Set idx = Nothing
    Exit Sub
    
CreateIndexError:
    Set cat = Nothing
    Set tbl = Nothing
    Set idx = Nothing
    
    If Err &lt;&gt; 0 Then
        MsgBox Err.Source &amp; "--&gt;" &amp; Err.Description, , "Error"
    End If
End Sub
' EndCreateIndexVB</code>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="6695769f-275b-4b70-81bd-1a5f7d74926c">Append Method (Indexes)</link>
<link xlink:href="6b9578c0-bc94-46b9-b801-c18e14b04b31">Index Object</link>
<link xlink:href="184cf536-455c-42be-bf1c-a5c25bade961">Indexes Collection</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>