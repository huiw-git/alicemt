---
title: "Views and Fields Collections Example (VB)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - VB
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d8304849-3f80-4cf3-9425-529d2a8ebedd
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
# Views and Fields Collections Example (VB)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The following code demonstrates how to use the <legacyLink xlink:href="bcc9146f-586f-4e69-9c10-863440c9cffa">Command</legacyLink> property and the <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink> object to retrieve field information for the view.</para>
  </introduction>
  <section>
    <content>
      <code>' BeginViewFieldsVB
Sub ViewFields()
    On Error GoTo ViewFieldsError
    
    Dim cnn As New ADODB.Connection
    Dim rst As New ADODB.Recordset
    Dim fld As ADODB.Field
    Dim cat As New ADOX.Catalog
    
    ' Open the Connection
    cnn.Open _
        "Provider='Microsoft.Jet.OLEDB.4.0';" &amp; _
        "Data Source='Northwind.mdb';"
    
    ' Open the catalog
    Set cat.ActiveConnection = cnn
    
    ' Set the Source for the Recordset
    Set rst.Source = cat.Views("AllCustomers").Command
    
    ' Retrieve Field information
    rst.Fields.Refresh
    For Each fld In rst.Fields
        Debug.Print fld.Name &amp; ":" &amp; fld.Type
    Next

    'Clean up
    cnn.Close
    Set cat = Nothing
    Set rst = Nothing
    Set cnn = Nothing
    Exit Sub
    
ViewFieldsError:

    If Not cnn Is Nothing Then
        If cnn.State = adStateOpen Then cnn.Close
    End If
    
    Set cat = Nothing
    Set rst = Nothing
    Set cnn = Nothing
    
    If Err &lt;&gt; 0 Then
        MsgBox Err.Source &amp; "--&gt;" &amp; Err.Description, , "Error"
    End If
    
End Sub
' EndViewFieldsVB</code>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="25fff69b-7556-4a28-b6f5-600a4bb0f607">ActiveConnection Property</link>
<link xlink:href="bb651639-a488-4e38-b6de-0ed99fa4dd92">Catalog Object</link>
<link xlink:href="bcc9146f-586f-4e69-9c10-863440c9cffa">Command Property</link>
<link xlink:href="653421ce-7b94-43d0-9bc6-4900f8f2af45">View Object</link>
<link xlink:href="a55d380c-2b7b-4b57-af74-8ba0b3de0db9">Views Collection</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>