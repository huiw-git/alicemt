---
title: "Catalog ActiveConnection Property Example (VB)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - VB
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: bb3274b1-764d-43a7-a49f-ef55680ecd26
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
# Catalog ActiveConnection Property Example (VB)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Setting the <legacyLink xlink:href="25fff69b-7556-4a28-b6f5-600a4bb0f607">ActiveConnection</legacyLink> property to a valid, open connection "opens" the catalog. From an open catalog, you can access the schema objects contained within that catalog.</para>
  </introduction>
  <section>
    <content>
      <code>' BeginOpenConnectionVB
Sub Main()
    On Error GoTo OpenConnectionError
    
    Dim cnn As New ADODB.Connection
    Dim cat As New ADOX.Catalog
    
    cnn.Open "Provider='Microsoft.Jet.OLEDB.4.0';" &amp; _
        "Data Source= 'Northwind.mdb';"
    Set cat.ActiveConnection = cnn
    Debug.Print cat.Tables(0).Type
    
    'Clean up
    cnn.Close
    Set cat = Nothing
    Set cnn = Nothing
    Exit Sub
    
OpenConnectionError:
    
    Set cat = Nothing

    If Not cnn Is Nothing Then
        If cnn.State = adStateOpen Then cnn.Close
    End If
    Set cnn = Nothing

    If Err &lt;&gt; 0 Then
        MsgBox Err.Source &amp; "--&gt;" &amp; Err.Description, , "Error"
    End If
End Sub
' EndOpenConnectionVB</code>
      <para>Setting the <legacyBold>ActiveConnection</legacyBold> property to a valid connection string also "opens" the catalog.</para>
      <code>Attribute VB_Name = "Catalog"</code>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="25fff69b-7556-4a28-b6f5-600a4bb0f607">ActiveConnection Property</link>
<link xlink:href="bb651639-a488-4e38-b6de-0ed99fa4dd92">Catalog Object</link>
<link xlink:href="a6d74000-0828-49ba-850a-63da865f8802">Table Object</link>
<link xlink:href="38d750e7-f3fb-426e-b4b4-55eea4f1a654">Tables Collection</link>
<link xlink:href="7b6e14bb-fb69-4d74-aaca-f5d380f4d887">Type Property (Table)</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>