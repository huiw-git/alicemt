---
title: "ADOX Code Example: NumericScale and Precision Properties Example (VB)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - VB
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ea2ec614-34c8-41b7-8ebd-063798bd56b4
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
# ADOX Code Example: NumericScale and Precision Properties Example (VB)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This example demonstrates the <legacyLink xlink:href="573ee5d1-57c7-4a27-be79-a0e12944ad9b">NumericScale</legacyLink> and <legacyLink xlink:href="0e0ecbbf-d7de-49d4-a128-5a519ecd54ba">Precision</legacyLink> properties of the <legacyLink xlink:href="6e772783-1bc8-4ea7-94b2-7d7a52ea5c47">Column</legacyLink> object. This code displays their value for the <legacyBold>Order Details</legacyBold> table of the <legacyItalic>Northwind</legacyItalic> database.</para>
  </introduction>
  <section>
    <content>
      <code>' BeginNumericScalePrecVB
Sub Main()
    On Error GoTo NumericScalePrecXError

    Dim cnn As New ADODB.Connection
    Dim cat As New ADOX.Catalog
    Dim tblOD As ADOX.Table
    Dim colLoop As ADOX.Column
        
    ' Connect the catalog.
    cnn.Open "Provider='Microsoft.Jet.OLEDB.4.0';" &amp; _
        "data source='Northwind.mdb';"
    Set cat.ActiveConnection = cnn
    
    ' Retrieve the Order Details table
    Set tblOD = cat.Tables("Order Details")
    
    ' Display numeric scale and precision of
    ' small integer fields.
    For Each colLoop In tblOD.Columns
        If colLoop.Type = adSmallInt Then
            MsgBox "Column: " &amp; colLoop.Name &amp; vbCr &amp; _
                "Numeric scale: " &amp; _
                colLoop.NumericScale &amp; vbCr &amp; _
                "Precision: " &amp; colLoop.Precision
        End If
    Next colLoop
    
    'Clean up
    cnn.Close
    Set cat = Nothing
    Set cnn = Nothing
    Exit Sub
    
NumericScalePrecXError:
    Set cat = Nothing
    
    If Not cnn Is Nothing Then
        If cnn.State = adStateOpen Then cnn.Close
    End If
    Set cnn = Nothing
    
    If Err &lt;&gt; 0 Then
        MsgBox Err.Source &amp; "--&gt;" &amp; Err.Description, , "Error"
    End If
End Sub
' EndNumericScalePrecVB</code>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="6e772783-1bc8-4ea7-94b2-7d7a52ea5c47">Column Object</link>
<link xlink:href="573ee5d1-57c7-4a27-be79-a0e12944ad9b">NumericScale Property</link>
<link xlink:href="0e0ecbbf-d7de-49d4-a128-5a519ecd54ba">Precision Property</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>