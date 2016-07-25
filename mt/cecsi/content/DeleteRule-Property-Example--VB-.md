---
title: "DeleteRule Property Example (VB)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - VB
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9ba00118-a80d-4a6d-a7d6-4f5492fb7ded
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
# DeleteRule Property Example (VB)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This example demonstrates the <legacyLink xlink:href="87bd4c0a-cae3-4007-a939-4193acaa00ac">DeleteRule</legacyLink> property of a <legacyLink xlink:href="55f116fe-4d56-4892-bffe-0cdd6fc727c9">Key</legacyLink> object. The code appends a new <legacyLink xlink:href="a6d74000-0828-49ba-850a-63da865f8802">Table</legacyLink> and then defines a new primary key, setting <legacyBold>DeleteRule</legacyBold> to <legacyBold>adRICascade</legacyBold>.</para>
  </introduction>
  <section>
    <content>
      <code>' BeginDeleteRuleVB
Sub Main()
    On Error GoTo DeleteRuleXError
    
    Dim kyPrimary As New ADOX.Key
    Dim cat As New ADOX.Catalog
    Dim tblNew As New ADOX.Table

    ' Connect the catalog
    cat.ActiveConnection = "Provider='Microsoft.Jet.OLEDB.4.0';" &amp; _
                     "data source='Northwind.mdb';"

    ' Name new table
    tblNew.Name = "NewTable"
    
    ' Append a numeric and a text field to new table.
    tblNew.Columns.Append "NumField", adInteger, 20
    tblNew.Columns.Append "TextField", adVarWChar, 20

    ' Append the new table
    cat.Tables.Append tblNew

    ' Define the Primary key
    kyPrimary.Name = "NumField"
    kyPrimary.Type = adKeyPrimary
    kyPrimary.RelatedTable = "Customers"
    kyPrimary.Columns.Append "NumField"
    kyPrimary.Columns("NumField").RelatedColumn = "CustomerId"
    kyPrimary.DeleteRule = adRICascade
    
    ' Append the primary key
    cat.Tables("NewTable").Keys.Append kyPrimary
    Debug.Print "The primary key is appended."
    
    'Delete the table as this is a demonstration.
    cat.Tables.Delete tblNew.Name
    Debug.Print "The primary key is deleted."

    'Clean up
    Set cat.ActiveConnection = Nothing
    Set cat = Nothing
    Set kyPrimary = Nothing
    Set tblNew = Nothing
    Exit Sub
    
DeleteRuleXError:

    Set cat = Nothing
    Set kyPrimary = Nothing
    Set tblNew = Nothing
    
    If Err &lt;&gt; 0 Then
        MsgBox Err.Source &amp; "--&gt;" &amp; Err.Description, , "Error"
    End If
    
End Sub
' EndDeleteRuleVB</code>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="87bd4c0a-cae3-4007-a939-4193acaa00ac">DeleteRule Property</link>
<link xlink:href="55f116fe-4d56-4892-bffe-0cdd6fc727c9">Key Object</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>