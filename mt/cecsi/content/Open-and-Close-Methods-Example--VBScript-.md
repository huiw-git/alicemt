---
title: "Open and Close Methods Example (VBScript)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - VB
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 66eca011-e258-4d8f-bd67-e017bcf0871b
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
# Open and Close Methods Example (VBScript)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This example uses the <legacyLink xlink:href="3236749c-4b71-4235-89e2-ccdfaaa9319d">Open</legacyLink> and <legacyLink xlink:href="3cdf27d1-a180-4cff-8e42-95dec5fb1b55">Close</legacyLink> methods on both <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink> and <legacyLink xlink:href="ef6b1824-5b12-43db-89d7-8f3d13896d4d">Connection</legacyLink> objects that have been opened.</para>
    <para>Use the following example in an Active Server Page (ASP). Use <legacyBold>Find</legacyBold> to locate the file Adovbs.inc and place it in the directory you plan to use. Cut and paste the following code into Notepad or another text editor, and save it as <legacyBold>OpenVBS.asp</legacyBold>. You can view the result in any browser.</para>
    <code>&lt;!-- BeginOpenVBS --&gt;
&lt;%@ Language=VBScript %&gt;
&lt;%' use this meta tag instead of adovbs.inc%&gt;
&lt;!--METADATA TYPE="typelib" uuid="00000205-0000-0010-8000-00AA006D2EA4" --&gt;
&lt;HTML&gt;
&lt;HEAD&gt;
&lt;META name="VI60_DefaultClientScript"  content=VBScript&gt;
&lt;META NAME="GENERATOR" Content="Microsoft Visual Studio 6.0"&gt;
&lt;title&gt;ADO Open Method&lt;/title&gt;
&lt;STYLE&gt;
&lt;!--
BODY {
   font-family: 'Verdana','Arial','Helvetica',sans-serif;
   BACKGROUND-COLOR:white;
   COLOR:black;
    }
.thead {
   background-color: #008080; 
   font-family: 'Verdana','Arial','Helvetica',sans-serif; 
   font-size: x-small;
   color: white;
   }
.thead2 {
   background-color: #800000; 
   font-family: 'Verdana','Arial','Helvetica',sans-serif; 
   font-size: x-small;
   color: white;
   }
.tbody { 
   text-align: center;
   background-color: #f7efde;
   font-family: 'Verdana','Arial','Helvetica',sans-serif; 
   font-size: x-small;
    }
--&gt;
&lt;/STYLE&gt;
&lt;/HEAD&gt;

&lt;BODY&gt;
&lt;H3&gt;ADO Open Method&lt;/H3&gt;

&lt;TABLE WIDTH=600 BORDER=0&gt;
&lt;TR&gt;
&lt;TD VALIGN=TOP COLSPAN=3&gt;
&lt;FONT SIZE=2&gt;
&lt;% ' to integrate/test this code replace the 
   ' Data Source value in the Connection string%&gt;
&lt;% 
    ' connection and recordset variables
    Dim Cnxn, strCnxn
    Dim rsCustomers, strSQLCustomers
    Dim rsProducts, strSQLProducts

    ' open connection
    Set Cnxn = Server.CreateObject("ADODB.Connection")
    strCnxn = "Provider='sqloledb';Data Source=" &amp; _
            Request.ServerVariables("SERVER_NAME") &amp; ";" &amp; _
            "Integrated Security='SSPI';Initial Catalog='Northwind';"

    Cnxn.Open strCnxn
        
    ' create and open first Recordset using Connection - execute
    Set rsCustomers = Server.CreateObject("ADODB.Recordset")
    strSQLCustomers = "SELECT CompanyName, ContactName, City FROM Customers"
    Set rsCustomers = Cnxn.Execute(strSQLCustomers) 

    ' create and open second Recordset using recordset - open
    Set rsProducts = Server.CreateObject("ADODB.Recordset")
    strSQLProducts = "SELECT ProductName, UnitPrice FROM Products"
    rsProducts.Open strSQLProducts, Cnxn, adOpenDynamic, adLockPessimistic, adCmdText
    %&gt;

    &lt;TABLE COLSPAN=8 CELLPADDING=5 BORDER=0&gt;
    &lt;!-- BEGIN column header row for Customer Table--&gt;
    &lt;TR CLASS=thead&gt;
       &lt;TD&gt;Company Name&lt;/TD&gt;
       &lt;TD&gt;Contact Name&lt;/TD&gt;
       &lt;TD&gt;City&lt;/TD&gt;
    &lt;/TR&gt;

    &lt;!--Display ADO Data from Customer Table--&gt;
    &lt;% Do Until rsCustomers.EOF %&gt;
    &lt;TR CLASS=tbody&gt;
      &lt;TD&gt; &lt;%=rsCustomers("CompanyName")%&gt; &lt;/TD&gt;
      &lt;TD&gt; &lt;%=rsCustomers("ContactName")%&gt;&lt;/TD&gt;
      &lt;TD&gt; &lt;%=rsCustomers("City")%&gt; &lt;/TD&gt;
    &lt;/TR&gt; 
    &lt;%rsCustomers.MoveNext 
    Loop 
    %&gt;
    &lt;/TABLE&gt;

    &lt;HR&gt;

    &lt;TABLE COLSPAN=8 CELLPADDING=5 BORDER=0&gt;
    &lt;!-- BEGIN column header row for Product List Table--&gt;

    &lt;TR CLASS=thead2&gt;
       &lt;TD&gt;Product Name&lt;/TD&gt;
       &lt;TD&gt;Unit Price&lt;/TD&gt;
    &lt;/TR&gt;
    &lt;!-- Display ADO Data Product List--&gt;
    &lt;% Do Until rsProducts.EOF %&gt;
      &lt;TR CLASS=tbody&gt;  
      &lt;TD&gt; &lt;%=rsProducts("ProductName")%&gt; &lt;/TD&gt;
      &lt;TD&gt; &lt;%=rsProducts("UnitPrice")%&gt; &lt;/TD&gt;
      &lt;/TR&gt;
      &lt;!--  Next Row = Record --&gt;
    &lt;%rsProducts.MoveNext 
    Loop 

    ' clean up
    If rsProducts.State = adStateOpen then
        rsProducts.Close
    End If
    If rsCustomers.State = adStateOpen then
        rsCustomers.Close
    End If
    If Cnxn.State = adStateOpen then
        Cnxn.Close
    End If
    Set rsProducts = Nothing
    Set rsCustomers = Nothing
    Set Cnxn = Nothing

    %&gt;
    &lt;/TABLE&gt;

&lt;/BODY&gt;
&lt;/HTML&gt;
&lt;!-- EndOpenVBS --&gt;</code>
  </introduction>
  <relatedTopics>
<link xlink:href="3cdf27d1-a180-4cff-8e42-95dec5fb1b55">Close Method</link>
<link xlink:href="ef6b1824-5b12-43db-89d7-8f3d13896d4d">Connection Object</link>
<link xlink:href="663defab-5545-4973-9036-24d5882c9737">Open Method (ADO Connection)</link>
<link xlink:href="3236749c-4b71-4235-89e2-ccdfaaa9319d">Open Method (ADO Recordset)</link>
<link xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset Object</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>