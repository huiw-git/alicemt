---
title: "Execute, Requery, and Clear Methods Example (VBScript)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - VB
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3a7bbf07-2fca-4892-95f4-eec93f2d5e91
caps.latest.revision: 11
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
# Execute, Requery, and Clear Methods Example (VBScript)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This example demonstrates the <legacyBold>Execute</legacyBold> method when run from both a <legacyLink xlink:href="a02c22fb-542d-465e-a629-30fd59dcbebf">Command</legacyLink> object and a <legacyLink xlink:href="ef6b1824-5b12-43db-89d7-8f3d13896d4d">Connection</legacyLink> object. It also uses the <legacyLink xlink:href="d81ab76f-1aa8-4ccf-92ec-b65254dc3ea1">Requery</legacyLink> method to retrieve current data in a <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">recordset</legacyLink>, and the <legacyLink xlink:href="0a61ba7a-20b8-426a-91a0-9040e7c5a98a">Clear</legacyLink> method to clear the contents of the <legacyLink xlink:href="290819e1-7b39-4e1e-a93b-801257138b00">Errors</legacyLink> collection. The ExecuteCommand and PrintOutput procedures are required for this procedure to run.</para>
    <para>Use the following example in an Active Server Page (ASP). To view this fully functional example, you must either have the data source AdvWorks.mdb (installed with the SDK samples) located at C:\Program Files\Microsoft Platform SDK\Samples\DataAccess\Rds\RDSTest\advworks.mdb or edit the path in the example code to reflect the actual location of this file. This is a Microsoft Access database file.</para>
    <para>Use <legacyBold>Find</legacyBold> to locate the file Adovbs.inc and place it in the directory you plan to use. Cut and paste the following code into Notepad or another text editor, and save it as <legacyBold>ExecuteVBS.asp</legacyBold>. You can view the result in any client browser.</para>
    <code>&lt;!-- BeginExecuteVBS --&gt;
&lt;%@ Language=VBScript %&gt;
&lt;% ' use this meta tag instead of ADOVBS.inc%&gt;
&lt;!-- METADATA TYPE="typelib" uuid="00000205-0000-0010-8000-00AA006D2EA4"  --&gt;
&lt;HTML&gt;
&lt;HEAD&gt;
&lt;META name="VI60_DefaultClientScript"  content=VBScript&gt;
&lt;META NAME="GENERATOR" Content="Microsoft Visual Studio 6.0"&gt;
&lt;title&gt;ADO Execute Method&lt;/title&gt;
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
&lt;H3&gt;ADO Execute Method&lt;/H3&gt;
&lt;HR&gt;
&lt;H4&gt;Recordset Retrieved Using Connection Object&lt;/H4&gt;
&lt;!--- Recordsets retrieved using Execute method of Connection and Command Objects--&gt;
&lt;% 
     ' connection, command and recordset variables
    Dim Cnxn, strCnxn
    Dim rsCustomers, strSQLCustomers
    Dim Cmd 
    Dim rsProducts, strSQLProducts

    ' create and open connection
    Set Cnxn = Server.CreateObject("ADODB.Connection") 
    strCnxn="Provider='sqloledb';Data Source=" &amp; _
            Request.ServerVariables("SERVER_NAME") &amp; ";" &amp; _
            "Integrated Security='SSPI';Initial Catalog='Northwind';"
    Cnxn.Open  strCnxn
    ' create and open recordset
    Set rsCustomers = Server.CreateObject("ADODB.Recordset")
    strSQLCustomers = "Customers"
    rsCustomers.Open strSQLCustomers, Cnxn, adOpenKeyset, adLockOptimistic, adCmdTable

    '1st Recordset using Connection - Execute
    Set rsCustomers = Cnxn.Execute(strSQLCustomers) 

    Set Cmd = Server.CreateObject("ADODB.Command")
    Cmd.ActiveConnection = Cnxn
    strSQLProducts = "SELECT * From Products"
    Cmd.CommandText = strSQLProducts

    '2nd Recordset Cmd - execute 
    Set rsProducts = Cmd.Execute
    %&gt;
    &lt;TABLE COLSPAN=8 CELLPADDING=5 BORDER=0 ALIGN=CENTER&gt;
    &lt;!-- BEGIN column header row for Customer Table--&gt;
    &lt;TR CLASS=thead&gt;
      &lt;TH&gt;Company Name&lt;/TH&gt;
      &lt;TH&gt;Contact Name&lt;/TH&gt;
      &lt;TH&gt;City&lt;/TH&gt;
    &lt;/TR&gt;

    &lt;!--Display ADO Data from Customer Table--&gt;
    &lt;% 
    Do While Not rsCustomers.EOF %&gt;
      &lt;TR CLASS=tbody&gt;
        &lt;TD&gt; 
        &lt;%= rsCustomers("CompanyName")%&gt; 
        &lt;/TD&gt;
        &lt;TD&gt;
        &lt;%= rsCustomers("ContactName") %&gt; 
        &lt;/TD&gt;
        &lt;TD&gt; 
        &lt;%= rsCustomers("City")%&gt; 
        &lt;/TD&gt;
      &lt;/TR&gt; 
      &lt;% 
    rsCustomers.MoveNext 
    Loop 
    %&gt;
&lt;/TABLE&gt;

&lt;HR&gt;
&lt;H4&gt;Recordset Retrieved Using Command Object&lt;/H4&gt;

&lt;TABLE CELLPADDING=5 BORDER=0 ALIGN=CENTER WIDTH="80%"&gt;

&lt;!-- BEGIN column header row for Product List Table--&gt;
&lt;TR CLASS=thead2&gt;
  &lt;TH&gt;Product Name&lt;/TH&gt;
  &lt;TH&gt;Unit Price&lt;/TH&gt;
&lt;/TR&gt;

&lt;!-- Display ADO Data Product List--&gt;
&lt;% Do Until rsProducts.EOF %&gt;
  &lt;TR CLASS=tbody&gt;
    &lt;TD&gt;
    &lt;%= rsProducts("ProductName")%&gt;  
    &lt;/TD&gt;
    &lt;TD&gt; 
    &lt;%= rsProducts("UnitPrice")%&gt; 
    &lt;/TD&gt;
&lt;% 
    rsProducts.MoveNext 
    Loop
 
    ' clean up
    If rsCustomers.State = adStateOpen then
        rsCustomers.Close
    End If
    If rsProducts.State = adStateOpen then
        rsProducts.Close
    End If
    If Cnxn.State = adStateOpen then
        Cnxn.Close
    End If
    Set Cmd = Nothing
    Set rsCustomers = Nothing
    Set rsProducts = Nothing
    Set Cnxn = Nothing
%&gt;
&lt;/TABLE&gt;

&lt;/BODY&gt;
&lt;/HTML&gt;
&lt;!-- EndExecuteVBS --&gt;</code>
  </introduction>
  <relatedTopics>
<link xlink:href="0a61ba7a-20b8-426a-91a0-9040e7c5a98a">Clear Method</link>
<link xlink:href="a02c22fb-542d-465e-a629-30fd59dcbebf">Command Object</link>
<link xlink:href="ef6b1824-5b12-43db-89d7-8f3d13896d4d">Connection Object</link>
<link xlink:href="a175d453-fa55-4f49-9ede-a26d83177919">Error Object</link>
<link xlink:href="290819e1-7b39-4e1e-a93b-801257138b00">Errors Collection</link>
<link xlink:href="f84a5ff3-0528-4ad7-9bea-9a15103378dd">Execute Method (ADO Command)</link>
<link xlink:href="03c69320-96b2-4d85-8d49-a13b13e31578">Execute Method (ADO Connection)</link>
<link xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset Object</link>
<link xlink:href="d81ab76f-1aa8-4ccf-92ec-b65254dc3ea1">Requery Method</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>