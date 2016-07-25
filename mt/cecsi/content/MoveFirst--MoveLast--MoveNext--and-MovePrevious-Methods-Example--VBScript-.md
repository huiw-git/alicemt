---
title: "MoveFirst, MoveLast, MoveNext, and MovePrevious Methods Example (VBScript)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - VB
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 911aa1dd-2786-4f34-992c-bb2fbdabcbdf
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
# MoveFirst, MoveLast, MoveNext, and MovePrevious Methods Example (VBScript)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This example uses the <legacyLink xlink:href="a61a01a7-5b33-4150-9126-21dfa63654cb">MoveFirst</legacyLink>, <legacyLink xlink:href="a61a01a7-5b33-4150-9126-21dfa63654cb">MoveLast</legacyLink>, <legacyLink xlink:href="a61a01a7-5b33-4150-9126-21dfa63654cb">MoveNext</legacyLink>, and <legacyLink xlink:href="a61a01a7-5b33-4150-9126-21dfa63654cb">MovePrevious</legacyLink> methods to move the record pointer of a <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink> based on the supplied command.</para>
    <para>Cut and paste the following code into Notepad or another text editor, and save it as <legacyBold>MoveFirstVBS.asp</legacyBold>. You can view the result in any browser.</para>
    <code>&lt;!-- BeginMoveFirstVBS --&gt;
&lt;%@ Language=VBScript %&gt;
&lt;%' use this meta tag instead of adovbs.inc%&gt;
&lt;!--METADATA TYPE="typelib" uuid="00000205-0000-0010-8000-00AA006D2EA4" --&gt;
&lt;HTML&gt;
&lt;HEAD&gt;
&lt;TITLE&gt;ADO MoveNext, MovePrevious, MoveLast, MoveFirst Methods&lt;/TITLE&gt;

&lt;SCRIPT LANGUAGE="VBScript"&gt;
&lt;!--
   Sub cmdDown_OnClick
      'Set Values in Form Input Boxes and Submit Form
      Document.form.MoveAction.Value = "MovePrev"
      Document.Form.Submit
   End Sub

   Sub cmdUp_OnClick
      Document.form.MoveAction.Value = "MoveNext"
      Document.Form.Submit
   End Sub

   Sub cmdFirst_OnClick
      Document.form.MoveAction.Value = "MoveFirst"
      Document.Form.Submit
   End Sub

   Sub cmdLast_OnClick
      Document.form.MoveAction.Value = "MoveLast"
      Document.Form.Submit
   End Sub
//--&gt;
&lt;/SCRIPT&gt;
&lt;/HEAD&gt;

&lt;body bgcolor="white"&gt; 
&lt;h1 align="center"&gt;ADO MoveNext, MovePrevious &lt;br&gt; MoveLast &amp; MoveFirst Methods&lt;/h1&gt;
&lt;% ' to integrate/test this code replace the 
   ' Data Source value in the Connection string%&gt;
&lt;% 
   ' connection and recordset variables
   Dim Cnxn, strCnxn
   Dim rsEmployees, strSQLEmployees

   ' open connection
    Set Cnxn = Server.CreateObject("ADODB.Connection")
    strCnxn = "Provider='sqloledb';Data Source=" &amp; _
            Request.ServerVariables("SERVER_NAME") &amp; ";" &amp; _
            "Integrated Security='SSPI';Initial Catalog='Northwind';"
    Cnxn.Open strCnxn
      
    ' create and open Recordset using object refs
   Set rsEmployees = Server.CreateObject("ADODB.Recordset")
   strSQLEmployees = "Employees"
   
   rsEmployees.ActiveConnection = Cnxn
   rsEmployees.CursorLocation = adUseClient
   rsEmployees.CursorType = adOpenKeyset
   rsEmployees.LockType = adLockOptimistic
   rsEmployees.Source = strSQLEmployees
   rsEmployees.Open

   rsEmployees.MoveFirst

   If Not IsEmpty(Request.Form("MoveAction")) Then
      strAction = Request.Form("MoveAction")
      varPosition  = Request.Form("Position")
      
      rsEmployees.AbsolutePosition = varPosition
      
      Select Case strAction
      
        Case "MoveNext"
        
         rsEmployees.MoveNext
         If rsEmployees.EOF Then
            rsEmployees.MoveLast
            strMessage = "Can't move beyond the last record."
         End If
        
        Case "MovePrev"
        
         rsEmployees.MovePrevious
         If rsEmployees.BOF Then
            rsEmployees.MoveFirst
            strMessage = "Can't move beyond the first record."
         End If

        Case "MoveLast"
      
         rsEmployees.MoveLast
      
        Case "MoveFirst"
      
         rsEmployees.MoveFirst
      
      End Select
   End If
      
%&gt;

&lt;!-- Display Current Record Number and Recordset Size --&gt;
&lt;h2&gt;Record Number &lt;%=rsEmployees.AbsolutePosition%&gt; of &lt;%=rsEmployees.RecordCount%&gt;&lt;/H2&gt;
&lt;hr&gt;
&lt;table cellpadding=5 border=0&gt;
&lt;!-- BEGIN column header row for Customer Table--&gt;
&lt;tr&gt;
   &lt;th&gt;Name&lt;/th&gt;
   &lt;th&gt;Hire Date&lt;/th&gt;
&lt;/tr&gt;

&lt;!--Display ADO Data from Customer Table--&gt;
&lt;tr&gt;
  &lt;td&gt;&lt;%= rsEmployees("LastName") &amp; ", " %&gt; 
      &lt;%= rsEmployees("FirstName") &amp; " " %&gt;&lt;/td&gt;
  &lt;td&gt;&lt;%= rsEmployees("HireDate")%&gt;&lt;/td&gt;
&lt;/tr&gt; 
&lt;tr&gt;
  &lt;td colspan=2&gt;&lt;%=strMessage%&gt;&lt;/td&gt;
&lt;/tr&gt;
&lt;/table&gt;

&lt;hr&gt;

&lt;form Name="Form" Method="Post" Action="MoveFirstVbs.asp"&gt;
&lt;Input Type=Button Name=cmdDown Value="&lt;"&gt;
&lt;Input Type=Button Name=cmdUp Value="&gt;"&gt;
&lt;BR&gt;
&lt;H3&gt;Click Direction Arrows to Use MovePrevious or MoveNext&lt;/H3&gt;
&lt;Input Type=Button Name=cmdFirst Value="First Record"&gt;
&lt;Input Type=Button Name=cmdLast Value="Last Record"&gt;


&lt;!-- Use Hidden Form Fields to record values to send to Server --&gt;

&lt;input Type="Hidden" Size="4" Name="MoveAction" Value="Move"&gt;
&lt;input Type="Hidden" Size="4" Name="Position" Value="&lt;%= rsEmployees.AbsolutePosition%&gt;"&gt;
&lt;/form&gt;

&lt;HR&gt;
&lt;/BODY&gt;

&lt;%
    ' clean up
    If rsEmployees.State = adStateOpen then
        rsEmployees.Close
    End If
    If Cnxn.State = adStateOpen then
        Cnxn.Close
    End If
%&gt;
&lt;/HTML&gt;
&lt;!-- EndMoveFirstVBS --&gt;</code>
  </introduction>
  <relatedTopics>
<link xlink:href="a61a01a7-5b33-4150-9126-21dfa63654cb">MoveFirst, MoveLast, MoveNext, and MovePrevious Methods</link>
<link xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset Object</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>