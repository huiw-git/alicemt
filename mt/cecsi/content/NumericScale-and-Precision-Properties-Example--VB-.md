---
title: "NumericScale and Precision Properties Example (VB)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - VB
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9c1e2322-c225-49d1-a120-a343f23cea73
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
# NumericScale and Precision Properties Example (VB)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This example uses the <legacyLink xlink:href="29a02992-64be-4fcd-be13-445cba205893">NumericScale</legacyLink> and <legacyLink xlink:href="1fa38e78-6b5b-414d-ba0a-3dd26b29b766">Precision</legacyLink> properties to display the numeric scale and precision of fields in the <legacyBold><legacyItalic>Discounts</legacyItalic></legacyBold> table of the <legacyBold><legacyItalic>Pubs</legacyItalic></legacyBold> database.</para>
    <code>'BeginNumericScaleVB

    'To integrate this code
    'replace the data source and initial catalog values
    'in the connection string

Public Sub NumericScaleX()

    ' connection and recordset variables
   Dim rstDiscounts As ADODB.Recordset
   Dim Cnxn As ADODB.Connection
   Dim fldTemp As ADODB.Field
   Dim strCnxn As String
   Dim strSQLDiscounts As String

   ' Open connection
   Set Cnxn = New ADODB.Connection
   strCnxn = "Provider='sqloledb';Data Source='MySqlServer';Initial Catalog='Pubs';Integrated Security='SSPI';"

   Cnxn.Open strCnxn
   
   ' Open recordset
   Set rstDiscounts = New ADODB.Recordset
   strSQLDiscounts = "Discounts"
   rstDiscounts.Open strSQLDiscounts, Cnxn, adOpenStatic, adLockReadOnly, adCmdTable

   ' Display numeric scale and precision of
   ' numeric and small integer fields
   For Each fldTemp In rstDiscounts.Fields
      If fldTemp.Type = adNumeric Or fldTemp.Type = adSmallInt Then
         MsgBox "Field: " &amp; fldTemp.Name &amp; vbCr &amp; _
            "Numeric scale: " &amp; _
               fldTemp.NumericScale &amp; vbCr &amp; _
            "Precision: " &amp; fldTemp.Precision
      End If
   Next fldTemp

    ' clean up
   rstDiscounts.Close
   Cnxn.Close
   Set rstDiscounts = Nothing
   Set Cnxn = Nothing

End Sub
'EndNumericScaleVB</code>
  </introduction>
  <relatedTopics>
<link xlink:href="b10a72fc-3c4b-4186-a70b-993dc9f7a092">Field Object</link>
<link xlink:href="29a02992-64be-4fcd-be13-445cba205893">NumericScale Property</link>
<link xlink:href="e010e794-7f0f-4026-8b5b-37328e437d63">Parameter Object</link>
<link xlink:href="1fa38e78-6b5b-414d-ba0a-3dd26b29b766">Precision Property</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>