---
title: "ActiveCommand Property Example (JScript)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - JScript
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: be09e2af-ba31-4168-8ccd-2461bb24e49a
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
# ActiveCommand Property Example (JScript)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This example demonstrates the <legacyLink xlink:href="fb4088d5-5968-42d6-aeaa-3955046bb4da">ActiveCommand</legacyLink> property. Cut and paste the following code to Notepad or another text editor, and save it as <legacyBold>ActiveCommandJS.asp</legacyBold>.</para>
    <code>&lt;!-- BeginActiveCommandJS --&gt;
&lt;%@LANGUAGE="JScript" %&gt;
&lt;%// use this meta tag instead of adojavas.inc%&gt;
&lt;!--METADATA TYPE="typelib" uuid="00000205-0000-0010-8000-00AA006D2EA4" --&gt;

&lt;%
    // user input
    strName = new String(Request.Form("ContactName"))
%&gt;

&lt;html&gt;

&lt;head&gt;
&lt;title&gt;ActiveCommand Property Example (JScript)&lt;/title&gt;
&lt;style&gt;
&lt;!--
BODY {
   font-family: 'Verdana','Arial','Helvetica',sans-serif;
   BACKGROUND-COLOR:white;
   COLOR:black;
    }
--&gt;
&lt;/style&gt;
&lt;/head&gt;

&lt;body bgcolor="White"&gt;

&lt;h1&gt;ActiveCommand Property Example (JScript)&lt;/h1&gt;

&lt;%
if (strName.length &gt; 0)
    {
        // connection and recordset variables
        var Cnxn = Server.CreateObject("ADODB.Connection")
        var strCnxn = "Provider='sqloledb';Data Source=" + Request.ServerVariables("SERVER_NAME") + ";" +
            "Initial Catalog='Northwind';Integrated Security='SSPI';";
        var cmdContact = Server.CreateObject("ADODB.Command");
        var rsContact = Server.CreateObject("ADODB.Recordset");
        // display variables
        var strMessage;
    
        try
        {
            // open connection
            Cnxn.Open(strCnxn);

            // Open a recordset using a command object
            cmdContact.CommandText = "SELECT ContactName FROM Customers WHERE City = ?";
            cmdContact.ActiveConnection = Cnxn;
            // create parameter and insert variable value
            cmdContact.Parameters.Append(cmdContact.CreateParameter("ContactName", adChar, adParamInput, 30, strName));
        
            rsContact = cmdContact.Execute();

            while(!rsContact.EOF){
                // start new line
                strMessage = "&lt;P&gt;";
                    
                // get data
                strMessage += rsContact("ContactName")
                    
                // end the line
                strMessage += "&lt;/P&gt;";
                
                // show data
                Response.Write(strMessage);
                    
                // get next record
                rsContact.MoveNext;
            }
        }
        catch (e)
        {
            Response.Write(e.message);
        }
        finally
        {
            // 'clean up
            if (rsContact.State == adStateOpen)
                rsContact.Close;
            if (Cnxn.State == adStateOpen)
                Cnxn.Close;
            rsContact = null;
            Cnxn = null;
        }
    }
%&gt;

&lt;hr&gt;


&lt;form method="POST" action="ActiveCommandJS.asp"&gt;
  &lt;p align="left"&gt;Enter city of customer to find (e.g., Paris): &lt;input type="text" name="ContactName" size="40" value=""&gt;&lt;/p&gt;
  &lt;p align="left"&gt;&lt;input type="submit" value="Submit" name="B1"&gt;&lt;input type="reset" value="Reset" name="B2"&gt;&lt;/p&gt;
&lt;/form&gt;
&lt;/body&gt;

&lt;/html&gt;
&lt;!-- EndActiveCommandJS --&gt;</code>
  </introduction>
  <relatedTopics>
<link xlink:href="fb4088d5-5968-42d6-aeaa-3955046bb4da">ActiveCommand Property</link>
<link xlink:href="a02c22fb-542d-465e-a629-30fd59dcbebf">Command Object</link>
<link xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset Object</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>