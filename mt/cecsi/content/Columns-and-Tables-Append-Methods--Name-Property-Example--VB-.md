---
title: "Columns and Tables Append Methods, Name Property Example (VB)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - VB
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 678e5546-df5d-4cd0-bfe9-6cf13cb385c0
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
# Columns and Tables Append Methods, Name Property Example (VB)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The following code demonstrates how to create a new table.</para>
  </introduction>
  <section>
    <content>
      <code>' BeginCreateTableVB
Sub Main()
    On Error GoTo CreateTableError
    
    Dim tbl As New Table
    Dim cat As New ADOX.Catalog
    
    ' Open the Catalog.
    cat.ActiveConnection = "Provider='Microsoft.Jet.OLEDB.4.0';" &amp; _
        "Data Source='Northwind.mdb';"
    
    tbl.Name = "MyTable"
    tbl.Columns.Append "Column1", adInteger
    tbl.Columns.Append "Column2", adInteger
    tbl.Columns.Append "Column3", adVarWChar, 50
    cat.Tables.Append tbl
    Debug.Print "Table 'MyTable' is added."
    
    'Delete the table as this is a demonstration.
    cat.Tables.Delete tbl.Name
    Debug.Print "Table 'MyTable' is deleted."
    
    'Clean up
    Set cat.ActiveConnection = Nothing
    Set cat = Nothing
    Set tbl = Nothing
    Exit Sub
    
CreateTableError:

    Set cat = Nothing
    Set tbl = Nothing

    If Err &lt;&gt; 0 Then
        MsgBox Err.Source &amp; "--&gt;" &amp; Err.Description, , "Error"
    End If
End Sub
' EndCreateTableVB</code>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="7a46d23c-efef-4ec7-815d-cd3ac86787dd">Append Method (Columns)</link>
<link xlink:href="a362ed51-314c-4783-9598-538dbf755f3d">Append Method (Tables)</link>
<link xlink:href="6e772783-1bc8-4ea7-94b2-7d7a52ea5c47">Column Object</link>
<link xlink:href="23b9fea8-4f76-4a51-95ce-1a6ce4560b34">Columns Collection</link>
<link xlink:href="81b92baf-b6b9-4f4e-9f33-4503795518cd">Name Property</link>
<link xlink:href="a6d74000-0828-49ba-850a-63da865f8802">Table Object</link>
<link xlink:href="38d750e7-f3fb-426e-b4b4-55eea4f1a654">Tables Collection</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>