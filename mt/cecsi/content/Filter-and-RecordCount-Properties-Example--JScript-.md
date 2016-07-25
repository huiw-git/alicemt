---
title: "Filter and RecordCount Properties Example (JScript)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - JScript
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 677fa67e-9cb9-4d7d-a786-beeb5bee5236
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
# Filter and RecordCount Properties Example (JScript)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This example opens a <legacyBold>Recordset</legacyBold> on the Companies table of the Northwind database and then uses the <legacyLink xlink:href="80263a7a-5d21-45d1-84fc-34b7a9be4c22">Filter</legacyLink> property to limit the records visible to those where the CompanyName field starts with the letter D. Cut and paste the following code to Notepad or another text editor, and save it as <legacyBold>FilterJS.asp</legacyBold>.</para>
    <code>&lt;!-- BeginFilterJS --&gt;
&lt;%@  Language=JavaScript %&gt;
&lt;%// use this meta tag instead of adojavas.inc%&gt;
&lt;!--METADATA TYPE="typelib" uuid="00000205-0000-0010-8000-00AA006D2EA4" --&gt;

&lt;html&gt;

&lt;head&gt;
&lt;title&gt;ADO Recordset.Filter Example&lt;/title&gt;
&lt;style&gt;
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
&lt;/style&gt;
&lt;/head&gt;

&lt;body bgcolor="White"&gt;

&lt;h1&gt;ADO Recordset.Filter Example&lt;/h1&gt;
&lt;!-- Page text goes here --&gt;
&lt;%
    // connection and recordset variables
    var Cnxn = Server.CreateObject("ADODB.Connection")
    var strCnxn = "Provider='sqloledb';Data Source=" + Request.ServerVariables("SERVER_NAME") + ";" +
            "Initial Catalog='Northwind';Integrated Security='SSPI';";
    var rsCustomers = Server.CreateObject("ADODB.Recordset");
    var SQLCustomers = "select * from Customers;";
    // record variables
    var fld, filter
    var showBlank = " ";
    var showNull = "-NULL-";
    
    try
    {
        //open connection 
        Cnxn.Open(strCnxn);
    
        // create recordset client-side using object refs
        rsCustomers.ActiveConnection = Cnxn;
        rsCustomers.CursorLocation = adUseClient;
        rsCustomers.CursorType = adOpenKeyset;
        rsCustomers.LockType = adLockOptimistic;
        rsCustomers.Source = SQLCustomers;
        rsCustomers.Open();
    
        rsCustomers.MoveFirst();
    
        //set filter
        filter = "CompanyName LIKE 'b*'";
        rsCustomers.Filter = filter
    
        if (rsCustomers.RecordCount == 0) {
            Response.Write("No records matched ");
            Response.Write (SQLCustomers + "So cannot make table...");
            Cnxn.Close();
            Response.End
        }
        else {
        // show the data
            Response.Write('&lt;table width="100%" border="2"&gt;');    
            while(!rsCustomers.EOF) {
                Response.Write('&lt;tr class="tbody"&gt;');
                for (var thisField = 0; thisField &lt; rsCustomers.Fields.Count; thisField++) {
                    fld = rsCustomers(thisField);
                    fldValue = fld.Value;
                    if (fldValue == null)
                        fldValue = showNull;
                    if (fldValue == "")
                        thisField=showBlank;
                    Response.Write("&lt;td&gt;" + fldValue + "&lt;/td&gt;")
                }
                rsCustomers.MoveNext();
                Response.Write("&lt;/tr&gt;");
            }
            // close the table
            Response.Write("&lt;/table&gt;");
        }
    }    
    catch (e)
    {
        Response.Write(e.message);
    }
    finally
    {
        // clean up
        if (rsCustomers.State == adStateOpen)
            rsCustomers.Close;
        if (Cnxn.State == adStateOpen)
            Cnxn.Close;
        rsCustomers = null;
        Cnxn = null;
    }
%&gt;

&lt;/body&gt;

&lt;/html&gt;
&lt;!-- EndFilterJS --&gt;</code>
  </introduction>
  <relatedTopics>
<link xlink:href="80263a7a-5d21-45d1-84fc-34b7a9be4c22">Filter Property</link>
<link xlink:href="834f0121-394a-44d4-ad7d-999b43a6fe63">RecordCount Property</link>
<link xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset Object</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>