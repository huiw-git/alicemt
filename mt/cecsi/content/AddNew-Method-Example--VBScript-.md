---
title: "AddNew Method Example (VBScript)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - VB
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: dcdcaf0a-b9b0-4d81-8728-43c38c4c853b
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
# AddNew Method Example (VBScript)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This example uses the <legacyLink xlink:href="a9f54be9-5763-45d0-a6eb-09981b03bc08">AddNew</legacyLink> method to create a new record with the specified name.</para>
    <para>Use the following example in an Active Server Page (ASP). Use <legacyBold>Find</legacyBold> to locate the file Adovbs.inc and place it in the directory you plan to use. Cut and paste the following code to Notepad or another text editor, and save it as <legacyBold>AddNewVBS.asp</legacyBold>. You can view the result in any client browser.</para>
    <para>To exercise the example, add a new record in the HTML form. Click <legacyBold>Add New</legacyBold>. See the <legacyLink xlink:href="78935d6d-1c1a-4306-a83a-1763210c69f9">Delete Method Example</legacyLink> to remove unwanted records.</para>
    <code>&lt;!-- BeginAddNewVBS --&gt;
&lt;%@Language = VBScript %&gt;
&lt;%' use this meta tag instead of adovbs.inc%&gt;
&lt;!--METADATA TYPE="typelib" uuid="00000205-0000-0010-8000-00AA006D2EA4" --&gt;
&lt;HTML&gt;
&lt;HEAD&gt;
    &lt;TITLE&gt;ADO AddNew Method (VBScript)&lt;/TITLE&gt;
    &lt;STYLE&gt;
    &lt;!--
    body {
       font-family: 'Verdana','Arial','Helvetica',sans-serif;
       BACKGROUND-COLOR:white;
       COLOR:black;
        }
    TH {
       background-color: #008080; 
       font-family: 'Arial Narrow','Arial',sans-serif; 
       font-size: xx-small;
       color: white;
       }
    TD { 
       text-align: center;
       background-color: #f7efde;
       font-family: 'Arial Narrow','Arial',sans-serif; 
       font-size: xx-small;
        }
    --&gt;
    &lt;/STYLE&gt;
&lt;/HEAD&gt;
&lt;BODY&gt; 

&lt;H1&gt;ADO AddNew Method (VBScript)&lt;/H1&gt;

&lt;% ' to integrate/test this code replace the 
   ' Data Source value in the Connection string%&gt;
&lt;% 
    ' connection and recordset variables
    Dim Cnxn, strCnxn
    Dim rsCustomers, strSQLCustomers
    Dim fld, Err

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

    'If this is first time page is open, Form collection
    'will be empty when data is entered. run AddNew method
    If Not IsEmpty(Request.Form) Then
        If Not Request.Form("CompanyName") = "" Then
            rsCustomers.AddNew
                rsCustomers("CustomerID") = Request.Form("CompanyID")
                rsCustomers("CompanyName") = Request.Form("CompanyName")
                rsCustomers("ContactName") = Request.Form("FirstName") &amp; _
                    " " &amp; Request.Form("LastName")
                rsCustomers("Phone") = Request.Form("PhoneNumber")
                rsCustomers("City") = Request.Form("City")
                rsCustomers("Region") = Request.Form("State")
            rsCustomers.Update
             ' check for errors
            If Cnxn.Errors.Count &gt; 0 Then
                For Each Err In Cnxn.Errors
                    Response.Write("Error " &amp; Err.SQLState &amp; ": " &amp; _
                        Err.Description &amp; " | " &amp; Err.NativeError)
                Next
            Cnxn.Errors.Clear
            rsCustomers.CancelUpdate
            End If
            'On Error GoTo 0
        rsCustomers.MoveFirst
        End If
    End If
%&gt;

&lt;TABLE COLSPAN="8" CELLPADDING=5 BORDER=1 ALIGN="center"&gt;
&lt;!-- BEGIN column header row for Customer Table--&gt;
    &lt;TR&gt;
        &lt;TH&gt;Customer ID&lt;/TH&gt;
        &lt;TH&gt;Company Name&lt;/TH&gt;
        &lt;TH&gt;Contact Name&lt;/TH&gt;
        &lt;TH&gt;Phone Number&lt;/TH&gt;
        &lt;TH&gt;City&lt;/TH&gt;
        &lt;TH&gt;State/Province&lt;/TH&gt;
        &lt;/TR&gt;
        
    &lt;% ' show the data
        Do Until rsCustomers.EOF
            Response.Write("&lt;TR&gt;")
            Response.Write("&lt;TD&gt;" &amp; rsCustomers("CustomerID") &amp; "&lt;/TD&gt;")
            Response.Write("&lt;TD&gt;" &amp; rsCustomers("CompanyName")&amp; "&lt;/TD&gt;")
            Response.Write("&lt;TD&gt;" &amp; rsCustomers("ContactName") &amp; "&lt;/TD&gt;")
            Response.Write("&lt;TD&gt;" &amp; rsCustomers("Phone") &amp; "&lt;/TD&gt;")
            Response.Write("&lt;TD&gt;" &amp; rsCustomers("City") &amp; "&lt;/TD&gt;")
            Response.Write("&lt;TD&gt;" &amp; rsCustomers("Region") &amp; "&lt;/TD&gt;")
            Response.Write("&lt;/TR&gt;")
        rsCustomers.MoveNext 
        Loop 
    %&gt;
&lt;/TABLE&gt; 

&lt;HR&gt;

&lt;!--
    Form to enter new record posts variables
    back to this page
--&gt;
&lt;FORM Method=post Action="AddNewVbs.asp" Name=Form&gt;
    &lt;TABLE&gt;
        &lt;TR&gt;
            &lt;TD&gt;Company ID:&lt;/TD&gt;
            &lt;TD&gt;&lt;INPUT Size="5" Name="CompanyID" maxLength=5  &gt;&lt;/TD&gt;
        &lt;/TR&gt;
        &lt;TR&gt;
            &lt;TD&gt;Company Name:&lt;/TD&gt;
            &lt;TD&gt;&lt;INPUT Size="50" Name="CompanyName" &gt;&lt;/TD&gt;
        &lt;/TR&gt;
        &lt;TR&gt;
            &lt;TD&gt;Contact First Name:&lt;/TD&gt;
            &lt;TD&gt;&lt;INPUT Size="50" Name="FirstName" &gt;&lt;/TD&gt;
        &lt;/TR&gt;
        &lt;TR&gt;
            &lt;TD&gt;Contact Last Name:&lt;/TD&gt;
            &lt;TD&gt;&lt;INPUT Size="50" Name="LastName" &gt;&lt;/TD&gt;
        &lt;/TR&gt;
        &lt;TR&gt;
            &lt;TD&gt;Contact Phone:&lt;/TD&gt;
            &lt;TD&gt;&lt;INPUT Size="50" Name="PhoneNumber" &gt;&lt;/TD&gt;
        &lt;/TR&gt;
        &lt;TR&gt;
            &lt;TD&gt;City:&lt;/TD&gt;
            &lt;TD&gt;&lt;INPUT Size="50" Name="City" &gt;&lt;/TD&gt;
        &lt;/TR&gt;
        &lt;TR&gt;
            &lt;TD&gt;State / Province:&lt;/TD&gt;
            &lt;TD&gt;&lt;INPUT Size="5" Name="State" &gt;&lt;/TD&gt;
        &lt;/TR&gt;
        &lt;TR&gt;
            &lt;TD Align="right"&gt;&lt;INPUT Type="submit" Value="Add New"&gt;&lt;/TD&gt;
            &lt;TD Align="left"&gt;&lt;INPUT Type="reset" Value="Reset Form"&gt;&lt;/TD&gt;
        &lt;/TR&gt;
    &lt;/TABLE&gt;
&lt;/FORM&gt;

&lt;%
    ' Show connection.
    Response.Write("Following is the connection string: &lt;br&gt;&lt;br&gt;")
    Response.Write(Cnxn)

    ' Clean up.
    If rsCustomers.State = adStateOpen then
       rsCustomers.Close
    End If
    If Cnxn.State = adStateOpen then
       Cnxn.Close
    End If
    Set rsCustomers=Nothing
    Set Cnxn=Nothing
    Set fld=Nothing
%&gt;

&lt;SCRIPT Language = "VBScript"&gt;
Sub Form_OnSubmit
   MsgBox "Sending New Record to Server",,"ADO-ASP _Example"
End Sub
&lt;/SCRIPT&gt;
&lt;/BODY&gt;
&lt;/HTML&gt;
&lt;!-- EndAddNewVBS --&gt;</code>
  </introduction>
  <relatedTopics>
<link xlink:href="a9f54be9-5763-45d0-a6eb-09981b03bc08">AddNew Method</link>
<link xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset Object</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>