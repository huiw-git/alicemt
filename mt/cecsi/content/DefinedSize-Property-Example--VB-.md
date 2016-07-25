---
title: "DefinedSize Property Example (VB)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - VB
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4dda2239-7ab5-4729-9c63-eb530803f7d9
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
# DefinedSize Property Example (VB)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This example demonstrates the <legacyLink xlink:href="762b8937-c31c-4e90-bb85-506d991e8280">DefinedSize</legacyLink> property of a <legacyLink xlink:href="6e772783-1bc8-4ea7-94b2-7d7a52ea5c47">Column</legacyLink>. The code will redefine the size of the FirstName column of the <legacyBold>Employees</legacyBold> table of the <legacyItalic>Northwind</legacyItalic> database. Then, the change in the values of the FirstName <legacyLink xlink:href="b10a72fc-3c4b-4186-a70b-993dc9f7a092">Field</legacyLink> of a <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink> based on the <legacyBold>Employees</legacyBold> table is displayed. Note that by default, the FirstName field becomes padded with spaces after you redefine the <legacyBold>DefinedSize</legacyBold> property.</para>
  </introduction>
  <section>
    <content>
      <code>' BeginDefinedSizeVB
Public Sub Main()
    On Error GoTo DefinedSizeXError

    Dim rstEmployees As ADODB.Recordset
    Dim catNorthwind As New ADOX.Catalog
    Dim colFirstName As ADOX.Column
    Dim colNewFirstName As New ADOX.Column
    Dim aryFirstName() As String
    Dim i As Integer
    Dim strCnn As String

    strCnn = "Provider='Microsoft.Jet.OLEDB.4.0';" &amp; _
             "Data Source='Northwind.mdb';"

    ' Open a Recordset for the Employees table.
    Set rstEmployees = New ADODB.Recordset
    rstEmployees.Open "Employees", strCnn, adOpenKeyset, , adCmdTable
    ReDim aryFirstName(rstEmployees.RecordCount)
    
    ' Open a Catalog for the Northwind database,
    ' using same connection as rstEmployees
    Set catNorthwind.ActiveConnection = rstEmployees.ActiveConnection
    
    ' Loop through the recordset displaying the contents
    ' of the FirstName field, the field's defined size,
    ' and its actual size.
    ' Also store FirstName values in aryFirstName array.
    rstEmployees.MoveFirst
    Debug.Print " "
    Debug.Print "Original Defined Size and Actual Size"
    i = 0
    Do Until rstEmployees.EOF
        Debug.Print "Employee name: " &amp; rstEmployees!FirstName &amp; _
            " " &amp; rstEmployees!LastName
        Debug.Print "    FirstName Defined size: " _
            &amp; rstEmployees!FirstName.DefinedSize
        Debug.Print "    FirstName Actual size: " &amp; _
            rstEmployees!FirstName.ActualSize
            If Not rstEmployees!FirstName = Null Then
                aryFirstName(i) = rstEmployees!FirstName
            End If
        rstEmployees.MoveNext
        i = i + 1
    Loop
    rstEmployees.Close
 
    ' Redefine the DefinedSize of FirstName in the catalog
    Set colFirstName = catNorthwind.Tables("Employees").Columns("FirstName")
    colNewFirstName.Name = colFirstName.Name
    colNewFirstName.Type = colFirstName.Type
    colNewFirstName.DefinedSize = colFirstName.DefinedSize + 1
    
    ' Append new FirstName column to catalog
    catNorthwind.Tables("Employees").Columns.Delete colFirstName.Name
    catNorthwind.Tables("Employees").Columns.Append colNewFirstName

    ' Open Employee table in Recordset for updating
    rstEmployees.Open "Employees", catNorthwind.ActiveConnection, _
        adOpenKeyset, adLockOptimistic, adCmdTable
    
    ' Loop through the recordset displaying the contents
    ' of the FirstName field, the field's defined size,
    ' and its actual size.
    ' Also restore FirstName values from aryFirstName.
    rstEmployees.MoveFirst
    Debug.Print " "
    Debug.Print "New Defined Size and Actual Size"
    i = 0
    Do Until rstEmployees.EOF
        rstEmployees!FirstName = aryFirstName(i)
        Debug.Print "Employee name: " &amp; rstEmployees!FirstName &amp; _
            " " &amp; rstEmployees!LastName
        Debug.Print "    FirstName Defined size: " _
            &amp; rstEmployees!FirstName.DefinedSize
        Debug.Print "    FirstName Actual size: " &amp; _
            rstEmployees!FirstName.ActualSize
        rstEmployees.MoveNext
        i = i + 1
    Loop
    rstEmployees.Close
    
    ' Restore original FirstName column to catalog
    catNorthwind.Tables("Employees").Columns.Delete colNewFirstName.Name
    catNorthwind.Tables("Employees").Columns.Append colFirstName
    
    ' Restore original FirstName values to Employees table
    rstEmployees.Open "Employees", catNorthwind.ActiveConnection, _
        adOpenKeyset, adLockOptimistic, adCmdTable
    
    rstEmployees.MoveFirst
    i = 0
    Do Until rstEmployees.EOF
        rstEmployees!FirstName = aryFirstName(i)
        rstEmployees.MoveNext
        i = i + 1
    Loop
    rstEmployees.Close
        
    'Clean up
    Set catNorthwind = Nothing
    Set colNewFirstName = Nothing
    Set colFirstName = Nothing
    Set rstEmployees = Nothing
    Exit Sub
    
DefinedSizeXError:
    Set catNorthwind = Nothing
    Set colNewFirstName = Nothing
    Set colFirstName = Nothing
    
    If Not rstEmployees Is Nothing Then
        If rstEmployees.State = adStateOpen Then rstEmployees.Close
    End If
    Set rstEmployees = Nothing
    
    If Err &lt;&gt; 0 Then
        MsgBox Err.Source &amp; "--&gt;" &amp; Err.Description, , "Error"
    End If
    
End Sub
' EndDefinedSizeVB</code>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="6e772783-1bc8-4ea7-94b2-7d7a52ea5c47">Column Object</link>
<link xlink:href="762b8937-c31c-4e90-bb85-506d991e8280">DefinedSize Property</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>