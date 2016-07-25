---
title: "Append and CreateParameter Methods Example (JScript)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - JScript
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 37000833-68f4-45f1-b2dd-7f75893d09d9
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
# Append and CreateParameter Methods Example (JScript)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This example uses the <legacyLink xlink:href="f8a9bbed-ba9c-4698-945d-317ad22d2e92">Append</legacyLink> and <legacyLink xlink:href="9666fdcc-0544-4ed7-a97b-c415f2a56d7e">CreateParameter</legacyLink> methods to execute a stored procedure with an input parameter. Cut and paste the following code to Notepad or another text editor, and save it as <legacyBold>AppendJS.asp</legacyBold>.</para>
    <code>&lt;!-- BeginAppendJS --&gt;
&lt;%@LANGUAGE="JScript" %&gt;
&lt;%// use this meta tag instead of adojavas.inc%&gt;
&lt;!--METADATA TYPE="typelib" uuid="00000205-0000-0010-8000-00AA006D2EA4" --&gt;

&lt;html&gt;
&lt;head&gt;
    &lt;title&gt;Append and CreateParameter Methods Example (JScript)&lt;/title&gt;
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
&lt;h1&gt;Append and CreateParameter Methods Example (JScript)&lt;/h1&gt;
&lt;%
    // verify user-input 
    var iRoyalty = parseInt(Request.Form("RoyaltyValue"));
    if (iRoyalty &gt; -1)
    {

        // connection, recordset and command variables
        var strCnxn = "Provider='sqloledb';Data Source=" + Request.ServerVariables("SERVER_NAME") + ";" +
            "Initial Catalog='pubs';Integrated Security='SSPI';";
        var Cnxn = Server.CreateObject("ADODB.Connection");
        var cmdByRoyalty = Server.CreateObject("ADODB.Command");
        var rsByRoyalty = Server.CreateObject("ADODB.Recordset");
        var rsAuthor = Server.CreateObject("ADODB.Recordset");
        // display variables
        var strMessage;
        
        try
        {
            // open connection and set cursor location
            Cnxn.Open(strCnxn);
            Cnxn.CursorLocation = adUseClient;
    
            // command object initial parameters
            cmdByRoyalty.CommandText = "byroyalty";
            cmdByRoyalty.CommandType = adCmdStoredProc;
        
            // create the new parameter and append to
            // the Command object's parameters collection
            var prmByRoyalty = cmdByRoyalty.CreateParameter("percentage", adInteger, adParamInput);
            cmdByRoyalty.Parameters.Append(prmByRoyalty);
            prmByRoyalty.Value = iRoyalty;
        
            cmdByRoyalty.ActiveConnection = Cnxn;
        
            // execute command
            rsByRoyalty = cmdByRoyalty.Execute();
        
            // display results
            rsAuthor.Open("Authors", Cnxn);
    
        
            while (!rsByRoyalty.EOF)
            {
                rsAuthor.Filter = "au_id='" + rsByRoyalty.Fields("au_id") + "'";
                
                // start new line
                strMessage = "&lt;P&gt;";
                    
                // recordset data
                strMessage += rsAuthor.Fields("au_fname") + " "; 
                strMessage += rsAuthor.Fields("au_lname") + " ";
                    
                // end the line
                strMessage += "&lt;/P&gt;";
                
                // show result
                Response.Write(strMessage);
                    
                // et next record
                rsByRoyalty.MoveNext;
            }
        }
        catch (e)
        {
            Response.Write(e.message);
        }
        finally
        {
            // clean up
            if (rsByRoyalty.State == adStateOpen)
                rsByRoyalty.Close;
            if (rsAuthor.State == adStateOpen)
                rsAuthor.Close;
            if (Cnxn.State == adStateOpen)
                Cnxn.Close;
            rsByRoyalty = null;
            rsAuthor = null;
            Cnxn = null;
        }
    }
%&gt;

&lt;hr&gt;


&lt;form method="POST" action="AppendJS.asp" id=form1 name=form1&gt;
  &lt;p align="left"&gt;Enter royalty percentage to find (e.g., 40): &lt;input type="text" name="RoyaltyValue" size="5"&gt;&lt;/p&gt;
  &lt;p align="left"&gt;&lt;input type="submit" value="Submit" name="B1"&gt;&lt;input type="reset" value="Reset" name="B2"&gt;&lt;/p&gt;
&lt;/form&gt;
&amp;nbsp;


&lt;/body&gt;

&lt;/html&gt;
&lt;!-- EndAppendJS --&gt;</code>
  </introduction>
  <relatedTopics>
<link xlink:href="f8a9bbed-ba9c-4698-945d-317ad22d2e92">Append Method</link>
<link xlink:href="9666fdcc-0544-4ed7-a97b-c415f2a56d7e">CreateParameter Method</link>
<link xlink:href="b10a72fc-3c4b-4186-a70b-993dc9f7a092">Field Object</link>
<link xlink:href="7c371474-b88f-4730-afa5-44163a0488d5">Fields Collection</link>
<link xlink:href="e010e794-7f0f-4026-8b5b-37328e437d63">Parameter Object</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>