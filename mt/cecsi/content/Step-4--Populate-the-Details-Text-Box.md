---
title: "Step 4: Populate the Details Text Box"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: cb4273e2-c907-4a86-a621-3bf110088228
caps.latest.revision: 4
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
# Step 4: Populate the Details Text Box
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>To populate the Details text box, create a new subroutine named <userInput>recFields</userInput> and insert the following code:</para>
    <code>Sub recFields(r As Record, l As ListBox, t As TextBox)
    Dim f As Field
    Dim s As Stream
    Set s = New Stream
    Dim str As String
    
    For Each f In r.Fields
        l.AddItem f.Name &amp; ": " &amp; f.Value
    Next
    t.Text = ""
    If r!RESOURCE_CONTENTCLASS = "text/plain" Then
        s.Open r, adModeRead, adOpenStreamFromRecord
        str = s.ReadText(1)
        s.Position = 0
        If Asc(Mid(str, 1, 1)) = 63 Then '//63 = "?"
            s.Charset = "ascii"
            s.Type = adTypeText
        End If
        t.Text = s.ReadText(adReadAll)
    End If
End Sub</code>
    <para>This code populates <codeInline>lstDetails</codeInline> with the fields and values of the simple record passed to <codeInline>recFields</codeInline>. If the resource is a text file, a text Stream is opened from the resource record. The code determines whether the character set is ASCII and copies the Stream contents into <codeInline>txtDetails</codeInline>.</para>
  </introduction>
  <relatedTopics>
<link xlink:href="2f551969-0fd9-41ee-b81d-100975a4bdc2">Internet Publishing Scenario</link>
<link xlink:href="315c32dc-aeb1-4629-b30e-87b44e8f84d1">Step 3: Populate the Fields List Box</link>
</relatedTopics>
</developerConceptualDocument>