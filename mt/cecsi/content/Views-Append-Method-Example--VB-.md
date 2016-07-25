---
title: "Views Append Method Example (VB)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - VB
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b5b4c082-ac29-4f49-a8b8-e21b554c9b0d
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
# Views Append Method Example (VB)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The following code demonstrates how to use a <legacyLink xlink:href="a02c22fb-542d-465e-a629-30fd59dcbebf">Command</legacyLink> object and the <legacyLink xlink:href="a55d380c-2b7b-4b57-af74-8ba0b3de0db9">Views</legacyLink> collection <legacyLink xlink:href="6070fd58-3237-4c77-a966-5b39ce5d57e4">Append</legacyLink> method to create a new view in the underlying data source.</para>
  </introduction>
  <section>
    <content>
      <code>' BeginCreateViewVB
Sub Main()
    On Error GoTo CreateViewError

    Dim cmd As New ADODB.Command
    Dim cat As New ADOX.Catalog
    
    ' Open the Catalog
    cat.ActiveConnection = _
        "Provider='Microsoft.Jet.OLEDB.4.0';" &amp; _
        "Data Source='Northwind.mdb';"
    
    ' Create the command representing the view.
    cmd.CommandText = "Select * From Customers"
    
    ' Create the new View
    cat.Views.Append "AllCustomers", cmd

    'Clean up
    Set cat.ActiveConnection = Nothing
    Set cat = Nothing
    Set cmd = Nothing
    Exit Sub
    
CreateViewError:

    Set cat = Nothing
    Set cmd = Nothing
    
    If Err &lt;&gt; 0 Then
        MsgBox Err.Source &amp; "--&gt;" &amp; Err.Description, , "Error"
    End If
End Sub
' EndCreateViewVB</code>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="25fff69b-7556-4a28-b6f5-600a4bb0f607">ActiveConnection Property</link>
<link xlink:href="6070fd58-3237-4c77-a966-5b39ce5d57e4">Append Method (Views)</link>
<link xlink:href="bb651639-a488-4e38-b6de-0ed99fa4dd92">Catalog Object</link>
<link xlink:href="653421ce-7b94-43d0-9bc6-4900f8f2af45">View Object</link>
<link xlink:href="a55d380c-2b7b-4b57-af74-8ba0b3de0db9">Views Collection</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>