---
title: "Visual Basic Example of Data Shaping"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - VB
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d95dd499-19e2-4ce7-b16e-f56a04a9519c
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
# Visual Basic Example of Data Shaping
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <code>' This application makes use of Microsoft Hierarchical FlexGrid
' Control, which is named as MSHFLexGrid.
Const SHAPER = "MSDataShape"
Const DP = "SQLOLEDB"
Const DS = "MySQLServer"
Const DB = "Northwind"

Private Sub Form_Load()
    FirstExample
End Sub

Private Sub Form_Resize()
    MSHFlexGrid.Top = 0
    MSHFlexGrid.Left = 0
    MSHFlexGrid.Width = Me.ScaleWidth
    MSHFlexGrid.Height = Me.ScaleHeight
End Sub

Private Sub FirstExample()
    Dim con As ADODB.Connection
    Dim rst As ADODB.Recordset
    Dim sCmd As String
    
    Set con = New ADODB.Connection
    Set rst = New ADODB.Recordset
    
    con.ConnectionString = ConnectionString(SHAPER, DP, DS, DB)
    con.Open
    
    sCmd = "SHAPE {SELECT CustomerID, ContactName FROM Customers} " _
        &amp; "APPEND ({SELECT OrderID, OrderDate, CustomerID FROM Orders} " _
        &amp; "AS chapOrders " _
        &amp; "RELATE customerID TO customerID)"

    rst.Open sCmd, con, adOpenStatic, 2
    Set MSHFlexGrid.Recordset = rst
    
    rst.Close
    Set rst = Nothing
    
    con.Close
    Set con = Nothing
    
End Sub

Private Function ConnectionString(pr As String, _
                                  dpr As String, _
                                  dsr As String, _
                                  dbs As String)
    Dim s As String
    If pr = "" Then
        s = "Provider=" &amp; dpr &amp; _
          ";Data Source=" &amp; dsr &amp; _
          ";Initial Catalog=" &amp; dbs &amp; _
          ";Integrated Security=SSPI;"
    Else
        s = "Provider=" &amp; pr &amp; _
          ";Data Provider=" &amp; dpr &amp; _
          ";Data Source=" &amp; dsr &amp; _
          ";Initial Catalog=" &amp; dbs &amp; _
          ";Integrated Security=SSPI;"
    End If
    ConnectionString = s
End Function
                                  </code>
  </introduction>
  <section>
    <content>
      <procedure>
        <title>Try It!</title>
        <steps class="ordered">
          <step>
            <content>
              <para>Create a Visual Basic Standard EXE application project</para>
            </content>
          </step>
          <step>
            <content>
              <para>Select <legacyBold>Components</legacyBold> from the <legacyBold>Project</legacyBold> menu in Visual Studio</para>
            </content>
          </step>
          <step>
            <content>
              <para>Select "Microsoft Hierarchical FlexGrid Control 6.0 (OLEDB)" from the <legacyBold>Components</legacyBold> popup window and then click <legacyBold>Save</legacyBold>.</para>
            </content>
          </step>
          <step>
            <content>
              <para>Double-click the FlexGrid Control from the ToolBox pane in the Visual Basic workspace. Change the name of this instance to MSHFLEXGRID.</para>
            </content>
          </step>
          <step>
            <content>
              <para>Copy the preceding code and paste it into the <legacyBold>Code</legacyBold> page to replace any existing code.</para>
            </content>
          </step>
          <step>
            <content>
              <para>Select <legacyBold>Start</legacyBold> from the <legacyBold>Run</legacyBold> menu to execute the application.</para>
            </content>
          </step>
        </steps>
      </procedure>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>