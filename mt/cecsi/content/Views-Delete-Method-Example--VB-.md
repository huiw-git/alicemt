---
title: "Views Delete Method Example (VB)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - VB
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 17df2a83-4166-4df8-8c17-0a33aaac8582
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
# Views Delete Method Example (VB)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The following code shows how to use the <legacyLink xlink:href="e6b6e3a4-8952-4d79-81f4-51019c338374">Delete</legacyLink> method to delete a view from the catalog.</para>
  </introduction>
  <section>
    <content>
      <code>' BeginDeleteViewVB
Sub Main()
    On Error GoTo DeleteViewError

    Dim cat As New ADOX.Catalog
    
    ' Open the catalog
    cat.ActiveConnection = "Provider='Microsoft.Jet.OLEDB.4.0';" &amp; _
        "Data Source='Northwind.mdb';"
    
    'Delete the View
    cat.Views.Delete "AllCustomers"

    'Clean up
    Set cat.ActiveConnection = Nothing
    Set cat = Nothing
    Exit Sub
    
DeleteViewError:
    Set cat = Nothing
    
    If Err &lt;&gt; 0 Then
        MsgBox Err.Source &amp; "--&gt;" &amp; Err.Description, , "Error"
    End If
End Sub
' EndDeleteViewVB</code>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="e6b6e3a4-8952-4d79-81f4-51019c338374">Delete Method (Collections)</link>
<link xlink:href="a55d380c-2b7b-4b57-af74-8ba0b3de0db9">Views Collection</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>