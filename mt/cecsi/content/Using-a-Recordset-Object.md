---
title: "Using a Recordset Object"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 01c630d8-eb35-4bd0-a99f-7c0f85316cc1
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
# Using a Recordset Object
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Alternatively, you can use <legacyBold>Recordset.Open</legacyBold> to implicitly establish a connection and issue a command over that connection in a single operation. For example, in Visual Basic:</para>
    <code>Dim oRs As ADODB.Recordset
Dim sConn As String
Dim sSQL as String

<codeFeaturedElement>sConn = "Provider='SQLOLEDB';Data Source='MySqlServer';" &amp; _</codeFeaturedElement>
<codeFeaturedElement>             "Initial Catalog='Northwind';Integrated Security='SSPI';"</codeFeaturedElement>

sSQL = "SELECT ProductID, ProductName, CategoryID, UnitPrice " &amp; _
             "FROM Products"

' Create and Open the Recordset object.
Set oRs = New ADODB.Recordset
oRs.CursorLocation = adUseClient
oRs.Open sSQL, <codeFeaturedElement>sConn</codeFeaturedElement>, adOpenStatic, _
               adLockBatchOptimistic, adCmdText
                      
MsgBox oRs.RecordCount
        
oRs.MarshalOptions = adMarshalModifiedOnly
' Disconnect the Recordset.
Set oRs.ActiveConnection = Nothing
oRs.Close        
Set oRs = Nothing</code>
    <para>Notice that <legacyBold>oRs.Open</legacyBold> takes a connection string (<legacyItalic>sConn</legacyItalic>), in place of a <legacyBold>Connection</legacyBold> object (<legacyItalic>oConn</legacyItalic>), as the value of its <legacyBold>ActiveConnection</legacyBold> parameter. Also the client-side cursor type is enforced by setting the <legacyBold>CursorLocation</legacyBold> property on the <legacyBold>Recordset</legacyBold> object. Again, contrast this with the <legacyBold>HelloData</legacyBold> example.</para>
  </introduction>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>