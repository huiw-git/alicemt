---
title: "ActualSize and DefinedSize Properties Example (VB)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - VB
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: bff2c273-b535-4b32-83b3-0336a406859c
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
# ActualSize and DefinedSize Properties Example (VB)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This example uses the <legacyLink xlink:href="722803d0-cef5-4d4c-b79d-3f2f58052229">ActualSize</legacyLink> and <legacyLink xlink:href="3ee27314-a305-4fbc-8433-9ee9a909afd6">DefinedSize</legacyLink> properties to display the defined size and actual size of a field.</para>
    <code>'BeginActualSizeVB

    'To integrate this code
    'replace the data source and initial catalog values
    'in the connection string

Public Sub Main()
    On Error GoTo ErrorHandler

    'recordset and connection variables
    Dim rstStores As ADODB.Recordset
    Dim SQLStores As String
    Dim strCnxn As String
     'record variables
    Dim strMessage As String

    ' Open a recordset for the Stores table
    strCnxn = "Provider='sqloledb';Data Source='MySqlServer';" &amp; _
        "Initial Catalog='Northwind';Integrated Security='SSPI';"
    Set rstStores = New ADODB.Recordset
    
    SQLStores = "Suppliers"
    rstStores.Open SQLStores, strCnxn, adOpenForwardOnly, adLockReadOnly, adCmdTable
    'the above two lines of code are identical as the default values for
    'CursorType and LockType arguments match those indicated
    
    ' Loop through the recordset displaying the contents
    ' of the store_name field, the field's defined size,
    ' and its actual size.
    rstStores.MoveFirst

    Do Until rstStores.EOF
        strMessage = "Company name: " &amp; rstStores!CompanyName &amp; _
        vbCrLf &amp; "Defined size: " &amp; _
        rstStores!CompanyName.DefinedSize &amp; _
        vbCrLf &amp; "Actual size: " &amp; _
        rstStores!CompanyName.ActualSize &amp; vbCrLf
        
        MsgBox strMessage, vbOKCancel, "ADO ActualSize Property (Visual Basic)"
        rstStores.MoveNext
    Loop

    ' clean up
    rstStores.Close
    Set rstStores = Nothing
    Exit Sub
    
ErrorHandler:
    ' clean up
    If Not rstStores Is Nothing Then
        If rstStores.State = adStateOpen Then rstStores.Close
    End If
    Set rstStores = Nothing
    
    If Err &lt;&gt; 0 Then
        MsgBox Err.Source &amp; "--&gt;" &amp; Err.Description, , "Error"
    End If
End Sub
'EndActualSizeVB</code>
  </introduction>
  <relatedTopics>
<link xlink:href="722803d0-cef5-4d4c-b79d-3f2f58052229">ActualSize Property</link>
<link xlink:href="3ee27314-a305-4fbc-8433-9ee9a909afd6">DefinedSize Property</link>
<link xlink:href="b10a72fc-3c4b-4186-a70b-993dc9f7a092">Field Object</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>