---
title: "PrimaryKey and Unique Properties Example (VB)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - VB
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f536acac-06ea-4b39-bfba-ee9902b01615
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
# PrimaryKey and Unique Properties Example (VB)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This example demonstrates the <legacyLink xlink:href="30185312-5e09-4804-852d-e505d660113a">PrimaryKey</legacyLink> and <legacyLink xlink:href="85fd4bd0-393b-4dc1-9d73-80dced4f2fbe">Unique</legacyLink> properties of an <legacyLink xlink:href="6b9578c0-bc94-46b9-b801-c18e14b04b31">Index</legacyLink>. The code creates a new table with two columns. The <legacyBold>PrimaryKey</legacyBold> and <legacyBold>Unique</legacyBold> properties are used to make one column the primary key for which duplicate values are not allowed.</para>
  </introduction>
  <section>
    <content>
      <code>' BeginPrimaryKeyVB
Sub Main()
    On Error GoTo PrimaryKeyXError

    Dim catNorthwind As New ADOX.Catalog
    Dim tblNew As New ADOX.Table
    Dim idxNew As New ADOX.Index
    Dim idxLoop As New ADOX.Index
    Dim colLoop As New ADOX.Column
    
    ' Connect the catalog
    catNorthwind.ActiveConnection = "Provider='Microsoft.Jet.OLEDB.4.0';" &amp; _
        "Data Source='Northwind.mdb';"
    
    ' Name new table
    tblNew.Name = "NewTable"
    
    ' Append a numeric and a text field to new table.
    tblNew.Columns.Append "NumField", adInteger, 20
    tblNew.Columns.Append "TextField", adVarWChar, 20
    
    ' Append new Primary Key index on NumField column
    ' to new table
    idxNew.Name = "NumIndex"
    idxNew.Columns.Append "NumField"
    idxNew.PrimaryKey = True
    idxNew.Unique = True
    tblNew.Indexes.Append idxNew
    
    ' Append an index on Textfield to new table.
    ' Note the different technique: Specifying index and
    ' column name as parameters of the Append method
    tblNew.Indexes.Append "TextIndex", "TextField"
    
    ' Append the new table
    catNorthwind.Tables.Append tblNew
    
    With tblNew
        Debug.Print tblNew.Indexes.Count &amp; " Indexes in " &amp; _
            tblNew.Name &amp; " Table"

        ' Enumerate Indexes collection.
        For Each idxLoop In .Indexes
            With idxLoop
                Debug.Print "Index " &amp; .Name
                Debug.Print "   Primary key = " &amp; .PrimaryKey
                Debug.Print "   Unique = " &amp; .Unique

                ' Enumerate Columns collection of each Index
                ' object.
                Debug.Print "    Columns"
                For Each colLoop In .Columns
                    Debug.Print "       " &amp; colLoop.Name
                Next colLoop
            End With
        Next idxLoop

    End With

    ' Delete new table as this is a demonstration.
    catNorthwind.Tables.Delete tblNew.Name
    
    'Clean up
    Set catNorthwind.ActiveConnection = Nothing
    Set catNorthwind = Nothing
    Set tblNew = Nothing
    Set idxNew = Nothing
    Set idxLoop = Nothing
    Set colLoop = Nothing
    Exit Sub
    
PrimaryKeyXError:
    
    Set catNorthwind = Nothing
    Set tblNew = Nothing
    Set idxNew = Nothing
    Set idxLoop = Nothing
    Set colLoop = Nothing
    
    If Err &lt;&gt; 0 Then
        MsgBox Err.Source &amp; "--&gt;" &amp; Err.Description, , "Error"
    End If
End Sub
' EndPrimaryKeyVB</code>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="6b9578c0-bc94-46b9-b801-c18e14b04b31">Index Object</link>
<link xlink:href="30185312-5e09-4804-852d-e505d660113a">PrimaryKey Property</link>
<link xlink:href="85fd4bd0-393b-4dc1-9d73-80dced4f2fbe">Unique Property</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>