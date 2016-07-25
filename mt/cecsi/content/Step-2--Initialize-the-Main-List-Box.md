---
title: "Step 2: Initialize the Main List Box"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a1454493-1c86-46c2-ada8-d3c6fcdaf3c1
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
# Step 2: Initialize the Main List Box
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>To declare global Record and Recordset objects, insert the following code into the (General) (Declarations) for Form1: </para>
    <code>Option Explicit
Dim grec As Record
Dim grs As Recordset</code>
    <para>This code declares global object references for Record and Recordset objects that will be used later in this scenario.</para>
  </introduction>
  <section>
    <title>To connect to a URL and populate lstMain</title>
    <content>
      <para>Insert the following code into the Form Load event handler for Form1: </para>
      <code>Private Sub Form_Load()
    Set grec = New Record
    Set grs = New Recordset
    grec.Open "", "URL=http://servername/foldername/", , _
        adOpenIfExists Or adCreateCollection
    Set grs = grec.GetChildren
    While Not grs.EOF
        lstMain.AddItem grs(0)
        grs.MoveNext
    Wend
End Sub</code>
      <para>This code instantiates the global Record and Recordset objects. The Record object, <codeInline>grec</codeInline>, is opened with a URL specified as the ActiveConnection. If the URL exists, it is opened; if it does not already exist, it is created. Note that you should replace "http://servername/foldername/" with a valid URL from your environment. </para>
      <para>The Recordset object, <codeInline>grs</codeInline>, is opened on the children of the Record, <codeInline>grec</codeInline>. Then <codeInline>lstMain</codeInline> is populated with the file names of the resources published to the URL. </para>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="2f551969-0fd9-41ee-b81d-100975a4bdc2">Internet Publishing Scenario</link>
<link xlink:href="77d3bfa5-fc9f-4a72-93b4-790c7d227988">Step 1: Set Up the Visual Basic Project</link>
<link xlink:href="315c32dc-aeb1-4629-b30e-87b44e8f84d1">Step 3: Populate the Fields List Box</link>
</relatedTopics>
</developerConceptualDocument>