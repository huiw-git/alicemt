---
title: "ParentCatalog Property Example (VB)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - VB
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 448bc850-7584-4c5f-89f3-5f4fee88b259
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
# ParentCatalog Property Example (VB)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The following code demonstrates how to use the <legacyLink xlink:href="a0bb2ed8-d4cb-4f92-8de7-769bbe0e6273">ParentCatalog</legacyLink> property to access a provider-specific property prior to appending a table to a catalog. The property is <unmanagedCodeEntityReference>AutoIncrement</unmanagedCodeEntityReference>, which creates an AutoIncrement field in a Microsoft Jet database.</para>
  </introduction>
  <section>
    <content>
      <code>' BeginCreateAutoIncrColumnVB
Sub Main()
    On Error GoTo CreateAutoIncrColumnError

    Dim cnn As New ADODB.Connection
    Dim cat As New ADOX.Catalog
    Dim tbl As New ADOX.Table
    
    cnn.Open "Provider='Microsoft.Jet.OLEDB.4.0';" &amp; _
        "Data Source='Northwind.mdb';"
    Set cat.ActiveConnection = cnn
    
    With tbl
        .Name = "MyContacts"
        Set .ParentCatalog = cat
        ' Create fields and append them to the new Table object.
        .Columns.Append "ContactId", adInteger
        ' Make the ContactId column and auto incrementing column
        .Columns("ContactId").Properties("AutoIncrement") = True
        .Columns.Append "CustomerID", adVarWChar
        .Columns.Append "FirstName", adVarWChar
        .Columns.Append "LastName", adVarWChar
        .Columns.Append "Phone", adVarWChar, 20
        .Columns.Append "Notes", adLongVarWChar
    End With
    
    cat.Tables.Append tbl
    Debug.Print "Table 'MyContacts' is added."
    
    ' Delete the table as this is a demonstration.
    cat.Tables.Delete tbl.Name
    Debug.Print "Table 'MyContacts' is delete."
    
    'Clean up
    cnn.Close
    Set cat = Nothing
    Set tbl = Nothing
    Set cnn = Nothing
    Exit Sub
    
CreateAutoIncrColumnError:
    
    Set cat = Nothing
    Set tbl = Nothing

    If Not cnn Is Nothing Then
        If cnn.State = adStateOpen Then cnn.Close
    End If
    Set cnn = Nothing
    
    If Err &lt;&gt; 0 Then
        MsgBox Err.Source &amp; "--&gt;" &amp; Err.Description, , "Error"
    End If
    
End Sub
' EndCreateAutoIncrColumnVB</code>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="7a46d23c-efef-4ec7-815d-cd3ac86787dd">Append Method (Columns)</link>
<link xlink:href="a362ed51-314c-4783-9598-538dbf755f3d">Append Method (Tables)</link>
<link xlink:href="bb651639-a488-4e38-b6de-0ed99fa4dd92">Catalog Object</link>
<link xlink:href="6e772783-1bc8-4ea7-94b2-7d7a52ea5c47">Column Object</link>
<link xlink:href="23b9fea8-4f76-4a51-95ce-1a6ce4560b34">Columns Collection</link>
<link xlink:href="81b92baf-b6b9-4f4e-9f33-4503795518cd">Name Property</link>
<link xlink:href="a0bb2ed8-d4cb-4f92-8de7-769bbe0e6273">ParentCatalog Property</link>
<link xlink:href="a6d74000-0828-49ba-850a-63da865f8802">Table Object</link>
<link xlink:href="5c6718b6-f728-478a-8afb-5d17b0a91d1f">Type Property (Column)</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>