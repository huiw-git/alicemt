---
title: "Connection Close Method, Table Type Property Example (VB)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - VB
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f88e7a3b-19ed-46e2-b2ce-3b611d9b8166
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
# Connection Close Method, Table Type Property Example (VB)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Setting the <legacyLink xlink:href="25fff69b-7556-4a28-b6f5-600a4bb0f607">ActiveConnection</legacyLink> property to <legacyBold>Nothing</legacyBold> should close the connection to the catalog. Associated collections will be empty. Any objects that were created from schema objects in the catalog will be orphaned. Any properties on those objects that have been cached will still be available, but an attempt to read properties that requires a call to the provider will fail.</para>
  </introduction>
  <section>
    <content>
      <code>' BeginCloseConnectionVB
Sub Main()
    On Error GoTo CloseConnectionByNothingError
    
    Dim cnn As New ADODB.Connection
    Dim cat As New ADOX.Catalog
    Dim tbl As ADOX.Table

    cnn.Open "Provider='Microsoft.Jet.OLEDB.4.0';" &amp; _
        "Data Source= 'Northwind.mdb';"
    Set cat.ActiveConnection = cnn
    Set tbl = cat.Tables(0)
    Debug.Print tbl.Type    ' Cache tbl.Type info
    Set cat.ActiveConnection = Nothing
    Debug.Print tbl.Type    ' tbl is orphaned
    ' Previous line will succeed if this info was cached.
    Debug.Print tbl.Columns(0).DefinedSize
    ' Previous line will fail if this info has not been cached.

    'Clean up.
    cnn.Close
    Set cat = Nothing
    Set cnn = Nothing
    Exit Sub
    
CloseConnectionByNothingError:
    Set cat = Nothing
    
    If Not cnn Is Nothing Then
        If cnn.State = adStateOpen Then cnn.Close
    End If
    Set cnn = Nothing
    
    If Err &lt;&gt; 0 Then
        MsgBox Err.Source &amp; "--&gt;" &amp; Err.Description, , "Error"
    End If
End Sub
' EndCloseConnectionVB</code>
      <para>Closing a <legacyLink xlink:href="ef6b1824-5b12-43db-89d7-8f3d13896d4d">Connection</legacyLink> object that was used to open the catalog should have the same effect as setting the <unmanagedCodeEntityReference>ActiveConnection</unmanagedCodeEntityReference> property to <languageKeyword>Nothing</languageKeyword>.</para>
      <code>Attribute VB_Name = "Connection"</code>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="25fff69b-7556-4a28-b6f5-600a4bb0f607">ActiveConnection Property</link>
<link xlink:href="bb651639-a488-4e38-b6de-0ed99fa4dd92">Catalog Object</link>
<link xlink:href="6e772783-1bc8-4ea7-94b2-7d7a52ea5c47">Column Object</link>
<link xlink:href="23b9fea8-4f76-4a51-95ce-1a6ce4560b34">Columns Collection</link>
<link xlink:href="a6d74000-0828-49ba-850a-63da865f8802">Table Object</link>
<link xlink:href="38d750e7-f3fb-426e-b4b4-55eea4f1a654">Tables Collection</link>
<link xlink:href="7b6e14bb-fb69-4d74-aaca-f5d380f4d887">Type Property (Table)</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>