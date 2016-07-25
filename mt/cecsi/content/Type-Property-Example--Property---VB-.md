---
title: "Type Property Example (Property) (VB)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - VB
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2ee8e4c5-1d66-4a77-8892-6dad7e07e611
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
# Type Property Example (Property) (VB)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This example demonstrates the <legacyLink xlink:href="8a4c079f-9f4f-4545-801d-85983b8db71e">Type</legacyLink> property. It is a model of a utility for listing the names and types of a collection, like <legacyLink xlink:href="1d539aa8-ce0d-4418-ab03-8d0a3c1e9d82">Properties</legacyLink>, <legacyLink xlink:href="7c371474-b88f-4730-afa5-44163a0488d5">Fields</legacyLink>, etc.</para>
    <para>We do not need to open the <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink> to access its <legacyBold>Properties</legacyBold> collection; they come into existence when the <legacyBold>Recordset</legacyBold> object is instantiated. However, setting the <legacyLink xlink:href="39c8d86e-7ee9-4182-be5e-aad5ce952f84">CursorLocation</legacyLink> property to <legacyBold>adUseClient</legacyBold> adds several dynamic properties to the <legacyBold>Recordset</legacyBold> object's <legacyBold>Properties</legacyBold> collection, making the example a little more interesting. For sake of illustration, we explicitly use the <legacyLink xlink:href="e11484bb-c5c7-42d8-9bb8-21572125d727">Item</legacyLink> property to access each <legacyLink xlink:href="b2a4767c-03c7-4935-a3bc-df3e1a38a009">Property</legacyLink> object.</para>
    <code>'BeginTypePropertyVB
Public Sub Main()
    On Error GoTo ErrorHandler

     ' recordset variables
    Dim rst As ADODB.Recordset
    Dim prop As ADODB.Property
     ' property variables
    Dim ix As Integer
    Dim strMsg As String
    
     ' create client-side recordset
    Set rst = New ADODB.Recordset
    rst.CursorLocation = adUseClient
     ' enumerate property types
    For ix = 0 To rst.Properties.Count - 1
        Set prop = rst.Properties.Item(ix)
        Select Case prop.Type
           Case adBigInt
              strMsg = "adBigInt"
           Case adBinary
              strMsg = "adBinary"
           Case adBoolean
              strMsg = "adBoolean"
           Case adBSTR
              strMsg = "adBSTR"
           Case adChapter
              strMsg = "adChapter"
           Case adChar
              strMsg = "adChar"
           Case adCurrency
              strMsg = "adCurrency"
           Case adDate
              strMsg = "adDate"
           Case adDBDate
              strMsg = "adDBDate"
           Case adDBTime
              strMsg = "adDBTime"
           Case adDBTimeStamp
              strMsg = "adDBTimeStamp"
           Case adDecimal
              strMsg = "adDecimal"
           Case adDouble
              strMsg = "adDouble"
           Case adEmpty
              strMsg = "adEmpty"
           Case adError
              strMsg = "adError"
           Case adFileTime
              strMsg = "adFileTime"
           Case adGUID
              strMsg = "adGUID"
           Case adIDispatch
              strMsg = "adIDispatch"
           Case adInteger
              strMsg = "adInteger"
           Case adIUnknown
              strMsg = "adIUnknown"
           Case adLongVarBinary
              strMsg = "adLongVarBinary"
           Case adLongVarChar
              strMsg = "adLongVarChar"
           Case adLongVarWChar
              strMsg = "adLongVarWChar"
           Case adNumeric
              strMsg = "adNumeric"
           Case adPropVariant
              strMsg = "adPropVariant"
           Case adSingle
              strMsg = "adSingle"
           Case adSmallInt
              strMsg = "adSmallInt"
           Case adTinyInt
              strMsg = "adTinyInt"
           Case adUnsignedBigInt
              strMsg = "adUnsignedBigInt"
           Case adUnsignedInt
              strMsg = "adUnsignedInt"
           Case adUnsignedSmallInt
              strMsg = "adUnsignedSmallInt"
           Case adUnsignedTinyInt
              strMsg = "adUnsignedTinyInt"
           Case adUserDefined
              strMsg = "adUserDefined"
           Case adVarBinary
              strMsg = "adVarBinary"
           Case adVarChar
              strMsg = "adVarChar"
           Case adVariant
              strMsg = "adVariant"
           Case adVarNumeric
              strMsg = "adVarNumeric"
           Case adVarWChar
              strMsg = "adVarWChar"
           Case adWChar
              strMsg = "adWChar"
           Case Else
              strMsg = "*UNKNOWN*"
        End Select
            'show results
        Debug.Print "Property " &amp; ix &amp; ": " &amp; prop.Name &amp; _
                    ", Type = " &amp; strMsg
    Next ix
    
    ' clean up
    Set rst = Nothing
    Exit Sub
    
ErrorHandler:
    ' clean up
    Set rst = Nothing
    
    If Err &lt;&gt; 0 Then
        MsgBox Err.Source &amp; "--&gt;" &amp; Err.Description, , "Error"
    End If
    
End Sub
'EndTypePropertyVB</code>
  </introduction>
  <relatedTopics>
<link xlink:href="b2a4767c-03c7-4935-a3bc-df3e1a38a009">Property Object</link>
<link xlink:href="8a4c079f-9f4f-4545-801d-85983b8db71e">Type Property</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>