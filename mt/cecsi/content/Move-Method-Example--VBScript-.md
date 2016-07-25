---
title: "Move Method Example (VBScript)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - VB
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 29ec4b95-8986-4970-943f-3da3ecb207a2
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
# Move Method Example (VBScript)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This example uses the <legacyLink xlink:href="13fe9381-d00b-4f4a-9162-83c3f21b3837">Move</legacyLink> method to position the record pointer, based on user input.</para>
    <para>Use the following example in an Active Server Page (ASP). To view this fully functional example, you must either have the data source AdvWorks.mdb (installed with the SDK) located at C:\Program Files\Microsoft Platform SDK\Samples\DataAccess\Rds\RDSTest\advworks.mdb or edit the path in the example code to reflect the actual location of this file. This is a Microsoft Access database file.</para>
    <para>Use <legacyBold>Find</legacyBold> to locate the file Adovbs.inc and place it in the directory you plan to use. Cut and paste the following code to Notepad or another text editor, and save it as <legacyBold>MoveVBS.asp</legacyBold>. You can view the result in any browser.</para>
    <para>Try entering a letter or noninteger to see the error handling work. </para>
    <code>&lt;!-- BeginMoveVBS --&gt;
&lt;%@ Language=VBScript %&gt;
&lt;%' use this meta tag instead of adovbs.inc%&gt;
&lt;!--METADATA TYPE="typelib" uuid="00000205-0000-0010-8000-00AA006D2EA4" --&gt;
&lt;HTML&gt;
&lt;HEAD&gt;
&lt;TITLE&gt;ADO Move Methods&lt;/TITLE&gt;
&lt;STYLE&gt;
&lt;!--
BODY {
   font-family: "MS SANS SERIF",sans-serif;
    }
.thead1 {
   background-color: #008080; 
   font-family: 'Arial Narrow','Arial',sans-serif; 
   font-size: x-small;
   color: white;
   }
.tbody { 
   text-align: center;
   background-color: #f7efde;
   font-family: 'Arial Narrow','Arial',sans-serif; 
   font-size: x-small;
    }
--&gt;
&lt;/STYLE&gt;
&lt;/HEAD&gt;
&lt;BODY&gt; 
&lt;H3&gt;ADO Move Methods&lt;/H3&gt;
&lt;% ' to integrate/test this code replace the 
   ' Data Source value in the Connection string%&gt;
&lt;% 
    ' connection and recordset variables
    Dim Cnxn, strCnxn
    Dim rsCustomers, strSQLCustomers

    ' open connection
    Set Cnxn = Server.CreateObject("ADODB.Connection")
    strCnxn = "Provider='sqloledb';Data Source=" &amp; _
            Request.ServerVariables("SERVER_NAME") &amp; ";" &amp; _
            "Integrated Security='SSPI';Initial Catalog='Northwind';"

    Cnxn.Open strCnxn
        
     ' create and open Recordset using object refs
    Set rsCustomers = Server.CreateObject("ADODB.Recordset")
    strSQLCustomers = "Customers"
    
    rsCustomers.ActiveConnection = Cnxn
    rsCustomers.CursorLocation = adUseClient
    rsCustomers.CursorType = adOpenKeyset
    rsCustomers.LockType = adLockOptimistic
    rsCustomers.Source = strSQLCustomers
    rsCustomers.Open

    'Check number of user moves this session and increment by entry
    Session("Clicks") = Session("Clicks") + Request.Form("MoveAmount")
    Clicks = Session("Clicks")
    ' Move to last known recordset position plus amount passed 
    rsCustomers.Move CInt(Clicks)

    'Error Handling
    If rsCustomers.EOF Then
        Session("Clicks") = rsCustomers.RecordCount
        Response.Write "This is the Last Record"
        rsCustomers.MoveLast
    ElseIf rsCustomers.BOF Then
        Session("Clicks") = 1
        rsCustomers.MoveFirst
        Response.Write "This is the First Record"
    End If
    %&gt;

    &lt;H3&gt;Current Record Number is &lt;BR&gt;
    &lt;% 
    If Session("Clicks") = 0 Then Session("Clicks") = 1
    Response.Write(Session("Clicks") )%&gt; of &lt;%=rsCustomers.RecordCount%&gt;&lt;/H3&gt;
    &lt;HR&gt;


    &lt;TABLE COLSPAN=8 CELLPADDING=5 BORDER=0&gt;

    &lt;!-- BEGIN column header row for Customer Table--&gt;

    &lt;TR CLASS=thead1&gt;
       &lt;TD&gt;Company Name&lt;/TD&gt;
       &lt;TD&gt;Contact Name&lt;/TD&gt;
       &lt;TD&gt;City&lt;/TD&gt;
    &lt;/TR&gt;
        &lt;% 'display%&gt;
        &lt;TR CLASS=tbody&gt;
          &lt;TD&gt; &lt;%= rsCustomers("CompanyName")%&gt; &lt;/TD&gt;
          &lt;TD&gt; &lt;%= rsCustomers("ContactName")%&gt;&lt;/TD&gt;
          &lt;TD&gt; &lt;%= rsCustomers("City")%&gt; &lt;/TD&gt;
        &lt;/TR&gt; 
    &lt;/TABLE&gt;

    &lt;HR&gt;
    &lt;Input Type=Button Name=cmdDown  Value="&amp;lt;  "&gt;
    &lt;Input Type=Button Name=cmdUp Value=" &amp;gt;"&gt;
    &lt;H5&gt;Click Direction Arrows for Previous or Next Record
    &lt;BR&gt; &lt;BR&gt;

    &lt;FORM Method = Post Action="MoveVbs.asp" Name=Form&gt;
    &lt;TABLE&gt;
        &lt;TR&gt;
           &lt;TD&gt;&lt;Input Type="Button" Name=Move Value="Move Amount "&gt;&lt;/TD&gt;
           &lt;TD&gt;&lt;/TD&gt;
           &lt;TD&gt;&lt;Input Type="Text" Size="4" Name="MoveAmount" Value=0&gt;&lt;/TD&gt;
        &lt;TR&gt;
    &lt;/TABLE&gt;
    Click Move Amount to use Move Method&lt;br&gt;
    Enter Number of Records to Move + or - &lt;/H5&gt;    &lt;/FORM&gt;
&lt;/BODY&gt;

&lt;Script Language = "VBScript"&gt;

Sub Move_OnClick
   ' Make sure move value entered is an integer
   If IsNumeric(Document.Form.MoveAmount.Value)Then
      Document.Form.MoveAmount.Value = CInt(Document.Form.MoveAmount.Value)
      Document.Form.Submit
   Else
      MsgBox "You Must Enter a Number", ,"ADO-ASP Example"
      Document.Form.MoveAmount.Value = 0
   End If
End Sub

Sub cmdDown_OnClick
   Document.Form.MoveAmount.Value = -1
   Document.Form.Submit
End Sub

Sub cmdUp_OnClick
   Document.Form.MoveAmount.Value = 1
   Document.Form.Submit
End Sub
&lt;/Script&gt;

&lt;%
    ' clean up
    If rsCustomers.State = adStateOpen then
        rsCustomers.Close
    End If
    If Cnxn.State = adStateOpen then
        Cnxn.Close
    End If
%&gt;
&lt;/HTML&gt;
&lt;!-- EndMoveVBS --&gt;</code>
  </introduction>
  <relatedTopics>
<link xlink:href="13fe9381-d00b-4f4a-9162-83c3f21b3837">Move Method</link>
<link xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset Object</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>