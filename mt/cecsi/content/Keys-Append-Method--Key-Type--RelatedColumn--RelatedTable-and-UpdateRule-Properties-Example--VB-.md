---
title: "Keys Append Method, Key Type, RelatedColumn, RelatedTable and UpdateRule Properties Example (VB)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - VB
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 13b5b1c3-6af6-439e-bb65-976578ba6bc2
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
# Keys Append Method, Key Type, RelatedColumn, RelatedTable and UpdateRule Properties Example (VB)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The following code demonstrates how to create a new foreign key relationship between two existing tables named <legacyBold>Customers</legacyBold> and <legacyBold>Orders</legacyBold>.</para>
  </introduction>
  <section>
    <content>
      <code>' BeginCreateKeyVB
Sub Main()
    On Error GoTo CreateKeyError

    Dim kyForeign As New ADOX.Key
    Dim cat As New ADOX.Catalog

    ' Connect to the catalog.
    cat.ActiveConnection = "Provider='Microsoft.Jet.OLEDB.4.0';" &amp; _
        "Data Source='Northwind.mdb';"
    
    ' Define the foreign key.
    kyForeign.Name = "CustOrder"
    kyForeign.Type = adKeyForeign
    kyForeign.RelatedTable = "Customers"
    kyForeign.Columns.Append "CustomerId"
    kyForeign.Columns("CustomerId").RelatedColumn = "CustomerId"
    kyForeign.UpdateRule = adRICascade
    
    ' Append the foreign key to the keys collection.
    cat.Tables("Orders").Keys.Append kyForeign
    
    'Delete the key t demonstrate the Delete method.
    cat.Tables("Orders").Keys.Delete kyForeign.Name
    
    'Clean up.
    Set cat.ActiveConnection = Nothing
    Set cat = Nothing
    Set kyForeign = Nothing
    Exit Sub
    
CreateKeyError:
    Set cat = Nothing
    Set kyForeign = Nothing
    
    If Err &lt;&gt; 0 Then
        MsgBox Err.Source &amp; "--&gt;" &amp; Err.Description, , "Error"
    End If
    
End Sub
' EndCreateKeyVB</code>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="7a46d23c-efef-4ec7-815d-cd3ac86787dd">Append Method (Columns)</link>
<link xlink:href="215a5391-f422-42ec-99ea-4e6fbb5d3d64">Append Method (Keys)</link>
<link xlink:href="bb651639-a488-4e38-b6de-0ed99fa4dd92">Catalog Object</link>
<link xlink:href="6e772783-1bc8-4ea7-94b2-7d7a52ea5c47">Column Object</link>
<link xlink:href="23b9fea8-4f76-4a51-95ce-1a6ce4560b34">Columns Collection</link>
<link xlink:href="55f116fe-4d56-4892-bffe-0cdd6fc727c9">Key Object</link>
<link xlink:href="cdb31c76-e559-475c-b33a-aac24f73e70e">Keys Collection</link>
<link xlink:href="81b92baf-b6b9-4f4e-9f33-4503795518cd">Name Property</link>
<link xlink:href="2f2ca019-c785-4c08-beb1-3a2d3b47823e">RelatedColumn Property</link>
<link xlink:href="cb54c6bc-2be2-40b1-bc11-90c10651b878">RelatedTable Property</link>
<link xlink:href="a6d74000-0828-49ba-850a-63da865f8802">Table Object</link>
<link xlink:href="38d750e7-f3fb-426e-b4b4-55eea4f1a654">Tables Collection</link>
<link xlink:href="8ca2f1fd-eb1e-490c-a28b-67eda92e0fc7">Type Property (Key)</link>
<link xlink:href="f4e21060-40cb-4790-8611-4086a092dda2">UpdateRule Property</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>