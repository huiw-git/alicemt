---
title: "Handler Property Example (VB)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - VB
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9664f9a6-65fc-4e7f-be3d-3e4b501b558a
caps.latest.revision: 12
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
# Handler Property Example (VB)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <alert class="important">
      <para>Beginning with Windows 8 and Windows Server 2012, RDS server components are no longer included in the Windows operating system (see Windows 8 and <externalLink><linkText>Windows Server 2012 Compatibility Cookbook</linkText><linkUri>http://download.microsoft.com/download/2/C/9/2C9C7B01-A1FC-47B6-9166-2151FB6E007C/Windows 8 and Windows Server 2012 Compatibility Cookbook.docx</linkUri></externalLink> for more detail). RDS client components will be removed in a future version of Windows. Avoid using this feature in new development work, and plan to modify applications that currently use this feature. Applications that use RDS should migrate to <externalLink><linkText>WCF Data Service</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=199565</linkUri></externalLink>.</para>
    </alert>
    <para>This example demonstrates the <legacyLink xlink:href="d85ea4fc-451c-436e-97b8-58f92b149dd0">RDS DataControl</legacyLink> object <legacyLink xlink:href="fdc34362-6d47-4727-b171-8d033159408e">Handler</legacyLink> property. (See <legacyLink xlink:href="86d77985-a0d0-405a-8587-c85a20540a0e">DataFactory Customization</legacyLink> for more details.)</para>
    <para>Assume that the following sections in the parameter file, Msdfmap.ini, are located on the server:</para>
    <code>[connect AuthorDataBase]
Access=ReadWrite
Connect="DSN=Pubs"
[sql AuthorById]
SQL="SELECT * FROM Authors WHERE au_id = ?"</code>
    <para>Your code looks like the following. The command assigned to the <legacyLink xlink:href="e0dabf23-a159-4fe5-a962-3df544a21f5c">SQL</legacyLink> property will match the <legacyBold><legacyItalic>AuthorById</legacyItalic></legacyBold> identifier and will retrieve a row for author Michael O'Leary. The <legacyBold>DataControl</legacyBold> object <legacyBold>Recordset</legacyBold> property is assigned to a disconnected <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink> object purely as a coding convenience.</para>
    <code>'BeginHandlerVB
Public Sub Main()
    On Error GoTo ErrorHandler
    
    Dim dc As New DataControl
    Dim rst As ADODB.Recordset
    
    dc.Handler = "MSDFMAP.Handler"
    dc.ExecuteOptions = 1
    dc.FetchOptions = 1
    dc.Server = "http://MyServer"
    dc.Connect = "Data Source=AuthorDataBase"
    dc.SQL = "AuthorById('267-41-2394')"
    dc.Refresh                  'Retrieve the record
    Set rst = dc.Recordset      'Use another Recordset as a convenience
    Debug.Print "Author is '" &amp; rst!au_fname &amp; " " &amp; rst!au_lname &amp; "'"

    ' clean up
    If rst.State = adStateOpen Then rst.Close
    Set rst = Nothing
    Set dc = Nothing
    Exit Sub
    
ErrorHandler:
    ' clean up
    If Not rst Is Nothing Then
        If rst.State = adStateOpen Then rst.Close
    End If
    Set rst = Nothing
    Set dc = Nothing
    
    If Err &lt;&gt; 0 Then
        MsgBox Err.Source &amp; "--&gt;" &amp; Err.Description, , "Error"
    End If
End Sub
'EndHandlerVB</code>
  </introduction>
  <relatedTopics>
<link xlink:href="d85ea4fc-451c-436e-97b8-58f92b149dd0">DataControl Object (RDS)</link>
<link xlink:href="fdc34362-6d47-4727-b171-8d033159408e">Handler Property (RDS)</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>