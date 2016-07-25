---
title: "AddNew Method Example (JScript)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - JScript
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: eabdd278-6576-4be7-9315-fb79cb8ef678
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
# AddNew Method Example (JScript)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This example uses the <legacyLink xlink:href="a9f54be9-5763-45d0-a6eb-09981b03bc08">AddNew</legacyLink> method to create a new record with the specified name. Cut and paste the following code to Notepad or another text editor, and save it as <legacyBold>AddNewJS.asp</legacyBold>.</para>
    <code>&lt;!-- BeginAddNewJS --&gt;
&lt;%@LANGUAGE="JScript" %&gt;
&lt;!-- Include file for JScript ADO Constants --&gt;
&lt;%// use this meta tag instead of adojavas.inc%&gt;
&lt;!--METADATA TYPE="typelib" uuid="00000205-0000-0010-8000-00AA006D2EA4" --&gt;

&lt;html&gt;

&lt;head&gt;
    &lt;title&gt;Add New Method Example (JScript)&lt;/title&gt;
&lt;style&gt;
&lt;!--
body {
   font-family: 'Verdana','Arial','Helvetica',sans-serif;
   BACKGROUND-COLOR:white;
   COLOR:black;
    }
--&gt;
&lt;/style&gt;
&lt;/head&gt;

&lt;body&gt;
&lt;h1&gt;AddNew Method Example (JScript)&lt;/h1&gt;

&lt;%
    if (Request.Form("Addit") == "AddNew")
    {
        // connection and recordset variables
        var Cnxn = Server.CreateObject("ADODB.Connection")
        var strCnxn = "Provider='sqloledb';Data Source=" + Request.ServerVariables("SERVER_NAME") + ";" +
            "Initial Catalog='Northwind';Integrated Security='SSPI';";
        var rsEmployee = Server.CreateObject("ADODB.Recordset");
        //record variables
        var FName = String(Request.Form("FirstName"));
        var LName = String(Request.Form("LastName"));
    
        try
        {
            // open connection
            Cnxn.Open(strCnxn)
        
            // open Employee recordset using client-side cursor
            rsEmployee.CursorLocation = adUseClient;
            rsEmployee.Open("Employees", strCnxn, adOpenKeyset, adLockOptimistic, adCmdTable);
    
            rsEmployee.AddNew();
            rsEmployee("FirstName") = FName;
            rsEmployee("LastName") = LName;
            rsEmployee.Update;

            // of course, you would normally do error handling here
            Response.Write("New record added.")
        }
        catch (e)
        {
            Response.Write(e.message);
        }
        finally
        {
            // clean up
            if (rsEmployee.State == adStateOpen)
                rsEmployee.Close;
            if (Cnxn.State == adStateOpen)
                Cnxn.Close;
            rsEmployee = null;
            Cnxn = null;
        }
    }
%&gt;

&lt;form method="post" action="AddNewJS.asp" id=form1 name=form1&gt;
&lt;table&gt;
&lt;tr&gt;
    &lt;td colspan="2"&gt;
    &lt;h4&gt;Please enter the record to add:&lt;/h4&gt;
    &lt;/td&gt;
&lt;/tr&gt;
&lt;tr&gt;
    &lt;td&gt;
        First Name:
    &lt;/td&gt;
    &lt;td&gt;
        &lt;input name="FirstName" maxLength=20&gt;
    &lt;/td&gt;
&lt;/tr&gt;
&lt;tr&gt;
    &lt;td&gt;
        Last Name:
    &lt;/td&gt;
    &lt;td&gt;
        &lt;input name="LastName" size="30" maxLength=30&gt;
    &lt;/td&gt;
&lt;/tr&gt;
&lt;tr&gt;
    &lt;td align="right"&gt;
        &lt;input type="submit" value="Submit" name="Submit"&gt;
    &lt;/td&gt;
    &lt;TD align="left"&gt;
        &lt;INPUT type="reset" value="Reset" name="Reset"&gt;
    &lt;/TD&gt;
&lt;/tr&gt;
&lt;/table&gt;
&lt;INPUT type="hidden" value="AddNew" name="Addit"&gt;
&lt;/form&gt;
&lt;/body&gt;
&lt;/HTML&gt;
&lt;!-- EndAddNewJS --&gt;</code>
  </introduction>
  <relatedTopics>
<link xlink:href="a9f54be9-5763-45d0-a6eb-09981b03bc08">AddNew Method</link>
<link xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset Object</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>