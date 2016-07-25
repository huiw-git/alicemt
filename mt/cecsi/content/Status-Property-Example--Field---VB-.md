---
title: "Status Property Example (Field) (VB)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - VB
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: fdd09b60-39c7-44be-8008-e891a031f80e
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
# Status Property Example (Field) (VB)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The following example opens a document from a read/write folder using the <legacyLink xlink:href="66a208d9-b580-4655-a41e-1d36e5b5bfca">Internet Publishing Provider</legacyLink>. The <legacyLink xlink:href="8cd1f7f4-0a3a-4f07-b8ba-6582e70140ad">Status</legacyLink> property of a <legacyLink xlink:href="b10a72fc-3c4b-4186-a70b-993dc9f7a092">Field</legacyLink> object of the <legacyLink xlink:href="db83ed2c-a8e3-460c-8682-64667e4d5d01">Record</legacyLink> will first be set to <legacyBold>adFieldPendingInsert</legacyBold>, then be updated to <legacyBold>adFieldOk</legacyBold>.</para>
    <code>'BeginStatusFieldVB
    
 ' to integrate this code replace the values in the source string

Sub Main()
    
   Dim File As ADODB.Record
   Dim strFile As String
   Dim Cnxn As ADODB.Connection
   Dim strCnxn As String
   
   Set Cnxn = New ADODB.Connection
   strCnxn = "url=http://MyServer/"
   Cnxn.Open strCnxn
   
   Set File = New ADODB.Record
   strFile = "Folder/FileName"
   ' Open a read/write document
   File.Source = strFile
   File.ActiveConnection = Cnxn
   File.Mode = adModeReadWrite
   File.Open

   Debug.Print "Append a couple of fields"
   
   File.Fields.Append "chektest:fld1", adWChar, 42, adFldUpdatable, "fld1"
   File.Fields.Append "chektest:fld2", adWChar, 42, adFldUpdatable, "fld2"
   
   Debug.Print "status for the fields"
   Debug.Print File.Fields("chektest:fld1").Status 'adfldpendinginsert
   Debug.Print File.Fields("chektest:fld2").Status 'adfldpendinginsert
   
    'turn off error-handling to verify field status
   On Error Resume Next
   
   File.Fields.Update
   
   Debug.Print "Update succeeds"
   Debug.Print File.Fields("chektest:fld1").Status 'adfldpendinginsert + adFieldUnavailable
   Debug.Print File.Fields("chektest:fld2").Status 'adfldpendinginsert + adFieldUnavailable
    
    ' resume default error-handling
   On Error GoTo 0
     
     ' clean up
    File.Close
    Cnxn.Close
    Set File = Nothing
    Set Cnxn = Nothing
      
End Sub
'EndStatusFieldVB</code>
    <para>The following example deletes a known <legacyBold>Field</legacyBold> from a <legacyBold>Record</legacyBold> opened from a document. The <legacyBold>Status</legacyBold> property will first be set to <legacyBold>adFieldOK</legacyBold>, then <legacyBold>adFieldPendingUnknown</legacyBold>.</para>
    <code>Attribute VB_Name = "StatusField"</code>
    <para>The following code deletes a <legacyBold>Field</legacyBold> from a <legacyBold>Record</legacyBold> opened on a read-only document. <legacyBold>Status</legacyBold> will be set to <legacyBold>adFieldPendingDelete</legacyBold>. At <legacyLink xlink:href="6b2a9c31-1a7e-40db-8a53-30720d0f6cc1">Update</legacyLink>, the delete will fail and <legacyBold>Status</legacyBold> will be <legacyBold>adFieldPendingDelete</legacyBold> plus <legacyBold>adFieldPermissionDenied</legacyBold>. <legacyLink xlink:href="eaa856cc-c786-462e-890c-c896261b1741">CancelUpdate</legacyLink> clears the pending <legacyBold>Status</legacyBold> setting.</para>
    <code>Attribute VB_Name = "StatusField"</code>
  </introduction>
  <relatedTopics>
<link xlink:href="b10a72fc-3c4b-4186-a70b-993dc9f7a092">Field Object</link>
<link xlink:href="db83ed2c-a8e3-460c-8682-64667e4d5d01">Record Object</link>
<link xlink:href="8cd1f7f4-0a3a-4f07-b8ba-6582e70140ad">Status Property (ADO Field)</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>