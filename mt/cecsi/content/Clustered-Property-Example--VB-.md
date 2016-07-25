---
title: "Clustered Property Example (VB)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - VB
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1cd30769-c8af-43e7-be27-12ed0434daa1
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
# Clustered Property Example (VB)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This example demonstrates the <legacyLink xlink:href="9b62fb35-de43-425a-83ca-77af4e33fea9">Clustered</legacyLink> property of an <legacyLink xlink:href="6b9578c0-bc94-46b9-b801-c18e14b04b31">Index</legacyLink>. Note that Microsoft Jet databases do not support clustered indexes, so this example will return <languageKeyword>False</languageKeyword> for the <unmanagedCodeEntityReference>Clustered</unmanagedCodeEntityReference> property of all indexes in the <legacyBold>Northwind</legacyBold> database.</para>
  </introduction>
  <section>
    <content>
      <code>' BeginClusteredVB
Sub Main()
    On Error GoTo ClusteredXError
    
    Dim cnn As New ADODB.Connection
    Dim cat As New ADOX.Catalog
    Dim tblLoop As ADOX.Table
    Dim idxLoop As ADOX.Index
    Dim strCnn As String

    strCnn = "Provider='SQLOLEDB';Data Source='MySqlServer';Initial Catalog='pubs';" &amp; _
        "Integrated Security='SSPI';"
    ' Connect to the catalog.
    cnn.Open strCnn
    cat.ActiveConnection = cnn
    
    ' Enumerate the tables.
    For Each tblLoop In cat.Tables
        'Enumerate the indexes.
        For Each idxLoop In tblLoop.Indexes
            Debug.Print tblLoop.Name &amp; " " &amp; _
                idxLoop.Name &amp; " " &amp; idxLoop.Clustered
        Next idxLoop
    Next tblLoop

    'Clean up.
    cnn.Close
    Set cat = Nothing
    Set cnn = Nothing
    Exit Sub
    
ClusteredXError:

    Set cat = Nothing
    
    If Not cnn Is Nothing Then
        If cnn.State = adStateOpen Then cnn.Close
    End If
    Set cnn = Nothing

    If Err &lt;&gt; 0 Then
        MsgBox Err.Source &amp; "--&gt;" &amp; Err.Description, , "Error"
    End If
End Sub
' EndClusteredVB</code>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="bb651639-a488-4e38-b6de-0ed99fa4dd92">Catalog Object</link>
<link xlink:href="9b62fb35-de43-425a-83ca-77af4e33fea9">Clustered Property</link>
<link xlink:href="6b9578c0-bc94-46b9-b801-c18e14b04b31">Index Object</link>
<link xlink:href="a6d74000-0828-49ba-850a-63da865f8802">Table Object</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>