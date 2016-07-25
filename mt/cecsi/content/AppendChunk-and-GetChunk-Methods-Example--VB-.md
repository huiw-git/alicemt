---
title: "AppendChunk and GetChunk Methods Example (VB)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - VB
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c07862b5-e466-46bd-910b-59ac96709cb9
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
# AppendChunk and GetChunk Methods Example (VB)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This example uses the <legacyLink xlink:href="c648b5a8-d4f1-4d16-836e-3957feb03617">AppendChunk</legacyLink> and <legacyLink xlink:href="fc268e22-205b-44a3-9038-ffed51e23e10">GetChunk</legacyLink> methods to fill an image field with data from another record.</para>
    <code>'BeginAppendChunkVB

    'To integrate this code
    'replace the data source and initial catalog values
    'in the connection string
    
Public Sub Main()
    On Error GoTo ErrorHandler

    'recordset and connection variables
    Dim Cnxn As ADODB.Connection
    Dim strCnxn As String
    Dim rstPubInfo As ADODB.Recordset
    Dim strSQLPubInfo As String
     'record variables
    Dim strPubID As String
    Dim strPRInfo As String
    Dim lngOffset As Long
    Dim lngLogoSize As Long
    Dim varLogo As Variant
    Dim varChunk As Variant
    Dim strMsg As String
    
    Const conChunkSize = 100
    
    ' Open a connection
    Set Cnxn = New ADODB.Connection
    strCnxn = "Provider='sqloledb';Data Source='MySqlServer';" &amp; _
        "Initial Catalog='Pubs';Integrated Security='SSPI';"
    Cnxn.Open strCnxn
    
    ' Open the pub_info table with a cursor that allows updates
    Set rstPubInfo = New ADODB.Recordset
    strSQLPubInfo = "pub_info"
    rstPubInfo.Open strSQLPubInfo, Cnxn, adOpenKeyset, adLockOptimistic, adCmdTable
    
    ' Prompt for a logo to copy
    strMsg = "Available logos are : " &amp; vbCr &amp; vbCr
    Do While Not rstPubInfo.EOF
        strMsg = strMsg &amp; rstPubInfo!pub_id &amp; vbCr &amp; _
            Left(rstPubInfo!pr_info, InStr(rstPubInfo!pr_info, ",") - 1) &amp; _
            vbCr &amp; vbCr
        rstPubInfo.MoveNext
    Loop
   
    strMsg = strMsg &amp; "Enter the ID of a logo to copy:"
    strPubID = InputBox(strMsg)
    
    ' Copy the logo to a variable in chunks
    rstPubInfo.Filter = "pub_id = '" &amp; strPubID &amp; "'"
    lngLogoSize = rstPubInfo!logo.ActualSize
    Do While lngOffset &lt; lngLogoSize
        varChunk = rstPubInfo!logo.GetChunk(conChunkSize)
        varLogo = varLogo &amp; varChunk
        lngOffset = lngOffset + conChunkSize
    Loop
   
    ' Get data from the user
    strPubID = Trim(InputBox("Enter a new pub ID" &amp; _
                             " [must be &gt; 9899 &amp; &lt; 9999]:"))
                             
    strPRInfo = Trim(InputBox("Enter descriptive text:"))
    
    ' Add the new publisher to the publishers table to avoid
    ' getting an error due to foreign key constraint
    Cnxn.Execute "INSERT publishers(pub_id, pub_name) VALUES('" &amp; _
                   strPubID &amp; "','Your Test Publisher')"
    
    ' Add a new record, copying the logo in chunks
    rstPubInfo.AddNew
    rstPubInfo!pub_id = strPubID
    rstPubInfo!pr_info = strPRInfo

    lngOffset = 0 ' Reset offset
    Do While lngOffset &lt; lngLogoSize
        varChunk = LeftB(RightB(varLogo, lngLogoSize - lngOffset), _
            conChunkSize)
        rstPubInfo!logo.AppendChunk varChunk
        lngOffset = lngOffset + conChunkSize
    Loop
    rstPubInfo.Update
   
    ' Show the newly added data
    MsgBox "New record: " &amp; rstPubInfo!pub_id &amp; vbCr &amp; _
        "Description: " &amp; rstPubInfo!pr_info &amp; vbCr &amp; _
        "Logo size: " &amp; rstPubInfo!logo.ActualSize

    ' Delete new records because this is a demo
    rstPubInfo.Requery
    Cnxn.Execute "DELETE FROM pub_info " &amp; _
        "WHERE pub_id = '" &amp; strPubID &amp; "'"

    Cnxn.Execute "DELETE FROM publishers " &amp; _
        "WHERE pub_id = '" &amp; strPubID &amp; "'"

    ' clean up
    rstPubInfo.Close
    Cnxn.Close
    Set rstPubInfo = Nothing
    Set Cnxn = Nothing
    Exit Sub
    
ErrorHandler:
   ' clean up
    If Not rstPubInfo Is Nothing Then
        If rstPubInfo.State = adStateOpen Then rstPubInfo.Close
    End If
    Set rstPubInfo = Nothing
    
    If Not Cnxn Is Nothing Then
        If Cnxn.State = adStateOpen Then Cnxn.Close
    End If
    Set Cnxn = Nothing
    
    If Err &lt;&gt; 0 Then
        MsgBox Err.Source &amp; "--&gt;" &amp; Err.Description, , "Error"
    End If
End Sub
'EndAppendChunkVB</code>
  </introduction>
  <relatedTopics>
<link xlink:href="c648b5a8-d4f1-4d16-836e-3957feb03617">AppendChunk Method</link>
<link xlink:href="b10a72fc-3c4b-4186-a70b-993dc9f7a092">Field Object</link>
<link xlink:href="fc268e22-205b-44a3-9038-ffed51e23e10">GetChunk Method</link>
<link xlink:href="e010e794-7f0f-4026-8b5b-37328e437d63">Parameter Object</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>