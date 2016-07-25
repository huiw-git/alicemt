---
title: "IndexNulls Property Example (VB)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - VB
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 45204669-32c0-4690-aab9-ddf0fd71ae48
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
# IndexNulls Property Example (VB)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This example demonstrates the <legacyLink xlink:href="313b0bf7-3f37-4823-8fca-bd9c80e078a7">IndexNulls</legacyLink> property of an <legacyLink xlink:href="6b9578c0-bc94-46b9-b801-c18e14b04b31">Index</legacyLink>. The code creates a new index and sets the value of <legacyBold>IndexNulls</legacyBold> based on user input (from a list box named List1). Then, the <legacyBold>Index</legacyBold> is appended to the <legacyBold>Employees</legacyBold> <legacyLink xlink:href="a6d74000-0828-49ba-850a-63da865f8802">Table</legacyLink> in the <legacyItalic>Northwind</legacyItalic> <legacyLink xlink:href="bb651639-a488-4e38-b6de-0ed99fa4dd92">Catalog</legacyLink>. The new <legacyBold>Index</legacyBold> is applied to a <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink> based on the <legacyBold>Employees</legacyBold> table, and the <legacyBold>Recordset</legacyBold> is opened. A new record is added to the <legacyBold>Employees</legacyBold> table, with a <legacyBold>Null</legacyBold> value in the indexed field. Whether this new record is displayed depends on the setting of the <legacyBold>IndexNulls</legacyBold> property.</para>
    <code>' BeginIndexNullsVB
Private Sub cmdIndexNulls_Click()
    IndexNullsX
End Sub

Sub IndexNullsX()

    Dim cnn As New ADODB.Connection
    Dim catNorthwind As New ADOX.Catalog
    Dim idxNew As New ADOX.Index
    Dim rstEmployees As New ADODB.Recordset
    Dim varBookmark As Variant
           
    ' Connect the catalog.
    cnn.Open "Provider=Microsoft.Jet.OLEDB.4.0;" &amp; _
        "data source=c:\Program Files\" &amp; _
        "Microsoft Office\Office\Samples\Northwind.mdb;"

    Set catNorthwind.ActiveConnection = cnn
    
    ' Append Country column to new index
    idxNew.Columns.Append "Country"
    idxNew.Name = "NewIndex"
        
    ' Set IndexNulls based on user selection in listbox List1
    Select Case List1.List(List1.ListIndex)
        Case "Allow"
            idxNew.IndexNulls = adIndexNullsAllow
        Case "Ignore"
            idxNew.IndexNulls = adIndexNullsIgnore
        Case Else
            End
    End Select
    
    'Append new index to Employees table
    catNorthwind.Tables("Employees").Indexes.Append idxNew
    
    rstEmployees.Index = idxNew.Name
    rstEmployees.Open "Employees", cnn, adOpenKeyset, _
        adLockOptimistic, adCmdTableDirect
        
    With rstEmployees
        ' Add a new record to the Employees table.
        .AddNew
        !FirstName = "Gary"
        !LastName = "Haarsager"
        .Update
        
        ' Bookmark the newly added record
        varBookmark = .Bookmark

        ' Use the new index to set the order of the records.
        .MoveFirst

        Debug.Print "Index = " &amp; .Index &amp; _
            ", IndexNulls = " &amp; idxNew.IndexNulls
        Debug.Print "  Country - Name"

        ' Enumerate the Recordset. The value of the
        ' IndexNulls property will determine if the newly
        ' added record appears in the output.
        Do While Not .EOF
            Debug.Print "    " &amp; _
                IIf(IsNull(!Country), "[Null]", !Country) &amp; _
                " - " &amp; !FirstName &amp; " " &amp; !LastName
            .MoveNext
        Loop

        ' Delete new record because this is a demonstration.
        .Bookmark = varBookmark
        .Delete
        
        .Close
    End With

    ' Delete new Index because this is a demonstration.
    catNorthwind.Tables("Employees").Indexes.Delete idxNew.Name
    Set catNorthwind = Nothing

End Sub
' EndIndexNullsVB</code>
  </introduction>
  <relatedTopics>
<link xlink:href="6b9578c0-bc94-46b9-b801-c18e14b04b31">Index Object</link>
<link xlink:href="313b0bf7-3f37-4823-8fca-bd9c80e078a7">IndexNulls Property</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>