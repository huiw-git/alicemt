---
title: "Find Method Example (JScript)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - JScript
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: adb5c37e-7874-41db-b4ee-572c1323deff
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
# Find Method Example (JScript)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This example uses the <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink> object's <legacyLink xlink:href="55c9810a-d8ca-46c2-a9dc-80e7ee7aa188">Find</legacyLink> method to locate and display the companies in the <legacyBold><legacyItalic>Northwind</legacyItalic></legacyBold> database whose name begins with the letter G. Cut and paste the following code to Notepad or another text editor, and save it as <legacyBold>FindJS.asp</legacyBold>.</para>
    <code>&lt;!-- BeginFindJS --&gt;
&lt;%@  Language=JavaScript %&gt;
&lt;%// use this meta tag instead of adojavas.inc%&gt;
&lt;!--METADATA TYPE="typelib" uuid="00000205-0000-0010-8000-00AA006D2EA4" --&gt;

&lt;html&gt;

&lt;head&gt;
&lt;title&gt;ADO Recordset.Find Example&lt;/title&gt;
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

&lt;body bgcolor="white"&gt;

&lt;h1&gt;ADO Recordset.Find Example&lt;/h1&gt;
&lt;%
    // connection and recordset variables
    var Cnxn = Server.CreateObject("ADODB.Connection");
    var strCnxn = "Provider='sqloledb';Data Source=" + Request.ServerVariables("SERVER_NAME") + ";" +
            "Initial Catalog='Northwind';Integrated Security='SSPI';";
    var rsCustomers = Server.CreateObject("ADODB.Recordset");
        // display string
    var strMessage;    
    var strFind;
    
    try
    {
            // open connection
        Cnxn.Open(strCnxn);
    
            //create recordset using object refs
        SQLCustomers = "select * from Customers;";
    
        rsCustomers.ActiveConnection = Cnxn;
        rsCustomers.CursorLocation = adUseClient;
        rsCustomers.CursorType = adOpenKeyset;
        rsCustomers.LockType = adLockOptimistic;
        rsCustomers.Source = SQLCustomers;
    
        rsCustomers.Open();
        rsCustomers.MoveFirst();
    
            //find criteria
        strFind = "CompanyName like 'g%'"
        rsCustomers.Find(strFind);
    
        if (rsCustomers.EOF) {
            Response.Write("No records matched ");
            Response.Write(SQLCustomers &amp; "So cannot make table...");
            Cnxn.Close();
            Response.End();
        } 
        else {
            Response.Write('&lt;table width="100%" border="2"&gt;');
            Response.Write('&lt;tr class="thead2"&gt;');
            // Put Headings On The Table for each Field Name
            for (thisField = 0; thisField &lt; rsCustomers.Fields.Count; thisField++) {
                fieldObject = rsCustomers.Fields(thisField);
                Response.Write('&lt;th width="' + Math.floor(100 / rsCustomers.Fields.Count) + '%"&gt;' + fieldObject.Name + "&lt;/th&gt;");
            }
            Response.Write("&lt;/tr&gt;");
            
            while (!rsCustomers.EOF) {
                Response.Write('&lt;tr class="tbody"&gt;');
                for(thisField=0; thisField&lt;rsCustomers.Fields.Count; thisField++) {
                    fieldObject = rsCustomers.Fields(thisField);
                    strField = fieldObject.Value;
                    if (strField == null)
                        strField = "-Null-";
                    if (strField == "")
                        strField = "";
                    Response.Write("&lt;td&gt;" + strField + "&lt;/td&gt;");
                }
                rsCustomers.Find(strFind, 1, adSearchForward)
                Response.Write("&lt;/tr&gt;");
            }
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
&lt;!-- EndFindJS --&gt;</code>
  </introduction>
  <relatedTopics>
<link xlink:href="55c9810a-d8ca-46c2-a9dc-80e7ee7aa188">Find Method</link>
<link xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset Object</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>