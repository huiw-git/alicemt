---
title: "Attributes and Name Properties Example (VB)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - VB
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 258bdce3-1819-44a2-9217-105879c789ef
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
# Attributes and Name Properties Example (VB)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This example displays the value of the <legacyLink xlink:href="acc15d40-68a6-4ba9-85bd-12d331aecaa6">Attributes</legacyLink> property for <legacyLink xlink:href="ef6b1824-5b12-43db-89d7-8f3d13896d4d">Connection</legacyLink>, <legacyLink xlink:href="b10a72fc-3c4b-4186-a70b-993dc9f7a092">Field</legacyLink>, and <legacyLink xlink:href="b2a4767c-03c7-4935-a3bc-df3e1a38a009">Property</legacyLink> objects. It uses the <legacyLink xlink:href="cfd0e29c-8310-44ab-85c3-5761184b865d">Name</legacyLink> property to display the name of each <legacyBold>Field</legacyBold> and <legacyBold>Property</legacyBold> object.</para>
    <code>' BeginAttributesVB
Sub Main()
    On Error GoTo AttributesXError
    
    Dim cnn As New ADODB.Connection
    Dim cat As New ADOX.Catalog
    Dim colTemp As New ADOX.Column
    Dim rstEmployees As New Recordset
    Dim strMessage As String
    Dim strInput As String
    Dim tblEmp As ADOX.Table
    
    ' Connect the catalog.
    cnn.Open "Provider='Microsoft.Jet.OLEDB.4.0';data source=" &amp; _
        "'Northwind.mdb';"
    Set cat.ActiveConnection = cnn

    Set tblEmp = cat.Tables("Employees")
    
    ' Create a new Field object and append it to the Fields
    ' collection of the Employees table.
    colTemp.Name = "FaxPhone"
    colTemp.Type = adVarWChar
    colTemp.DefinedSize = 24
    colTemp.Attributes = adColNullable
    cat.Tables("Employees").Columns.Append colTemp.Name, adWChar, 24
    
    ' Open the Employees table for updating as a Recordset
    rstEmployees.Open "Employees", cnn, adOpenKeyset, adLockOptimistic, adCmdTable
    
    With rstEmployees
        ' Get user input.
        strMessage = "Enter fax number for " &amp; _
            !FirstName &amp; " " &amp; !LastName &amp; "." &amp; vbCr &amp; _
            "[? - unknown, X - has no fax]"
        strInput = UCase(InputBox(strMessage))
        If strInput &lt;&gt; "" Then
            Select Case strInput
                Case "?"
                    !FaxPhone = Null
                Case "X"
                    !FaxPhone = ""
                Case Else
                    !FaxPhone = strInput
            End Select
            .Update
            
            ' Print report.
            Debug.Print "Name - Fax number"
            Debug.Print !FirstName &amp; " " &amp; !LastName &amp; " - ";

            If IsNull(!FaxPhone) Then
                Debug.Print "[Unknown]"
            Else
                If !FaxPhone = "" Then
                    Debug.Print "[Has no fax]"
                Else
                    Debug.Print !FaxPhone
                End If
            End If

        End If

        .Close
    End With
    
    'Clean up
    tblEmp.Columns.Delete colTemp.Name
    cnn.Close
    Set rstEmployees = Nothing
    Set cat = Nothing
    Set colTemp = Nothing
    Set cnn = Nothing
    Exit Sub
    
AttributesXError:
    
    If Not rstEmployees Is Nothing Then
        If rstEmployees.State = adStateOpen Then rstEmployees.Close
    End If
    Set rstEmployees = Nothing
    
    If Not tblEmp Is Nothing Then tblEmp.Columns.Delete colTemp.Name
     
    Set cat = Nothing
    Set colTemp = Nothing
   
    If Not cnn Is Nothing Then
        If cnn.State = adStateOpen Then cnn.Close
    End If
    Set cnn = Nothing
    
    If Err &lt;&gt; 0 Then
        MsgBox Err.Source &amp; "--&gt;" &amp; Err.Description, , "Error"
    End If
    
End Sub
' EndAttributesVB</code>
  </introduction>
  <relatedTopics>
<link xlink:href="acc15d40-68a6-4ba9-85bd-12d331aecaa6">Attributes Property</link>
<link xlink:href="ef6b1824-5b12-43db-89d7-8f3d13896d4d">Connection Object</link>
<link xlink:href="b10a72fc-3c4b-4186-a70b-993dc9f7a092">Field Object</link>
<link xlink:href="cfd0e29c-8310-44ab-85c3-5761184b865d">Name Property</link>
<link xlink:href="b2a4767c-03c7-4935-a3bc-df3e1a38a009">Property Object</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>