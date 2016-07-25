---
title: "Create Method Example (VB)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - VB
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d7ea0244-596a-404e-8f30-71cadab8d8fc
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
# Create Method Example (VB)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The following code shows how to create a new Microsoft Jet database with the <legacyLink xlink:href="64f5c21c-b581-42d8-bdc7-c4f1bebaf105">Create</legacyLink> method.</para>
  </introduction>
  <section>
    <content>
      <code>Attribute VB_Name = "Create"
Option Explicit

' BeginCreateDatabseVB
Sub CreateDatabase()
    On Error GoTo CreateDatabaseError
    
    Dim cat As New ADOX.Catalog
    cat.Create "Provider='Microsoft.Jet.OLEDB.4.0';Data Source='new.mdb'"

    'Clean up
    Set cat = Nothing
    Exit Sub
    
CreateDatabaseError:
    Set cat = Nothing

    If Err &lt;&gt; 0 Then
        MsgBox Err.Source &amp; "--&gt;" &amp; Err.Description, , "Error"
    End If
End Sub
' EndCreateDatabaseVB</code>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="bb651639-a488-4e38-b6de-0ed99fa4dd92">Catalog Object</link>
<link xlink:href="64f5c21c-b581-42d8-bdc7-c4f1bebaf105">Create Method</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>