---
title: "Execute, Requery, and Clear Methods Example (JScript)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - JScript
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 51a87e91-c9d9-4e49-af47-79cce2c4cfe0
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
# Execute, Requery, and Clear Methods Example (JScript)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This example demonstrates the <legacyBold>Execute</legacyBold> method when run from both a <legacyLink xlink:href="a02c22fb-542d-465e-a629-30fd59dcbebf">Command</legacyLink> object and a <legacyLink xlink:href="ef6b1824-5b12-43db-89d7-8f3d13896d4d">Connection</legacyLink> object. It also uses the <legacyLink xlink:href="d81ab76f-1aa8-4ccf-92ec-b65254dc3ea1">Requery</legacyLink> method to retrieve current data in a <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink>, and the <legacyLink xlink:href="0a61ba7a-20b8-426a-91a0-9040e7c5a98a">Clear</legacyLink> method to clear the contents of the <legacyLink xlink:href="290819e1-7b39-4e1e-a93b-801257138b00">Errors</legacyLink> collection. (The <legacyBold>Errors</legacyBold> collection is accessed via the <legacyBold>Connection</legacyBold> object of the <legacyLink xlink:href="52d0a96c-14fb-4ad9-b004-4d821bc0a6db">ActiveConnection</legacyLink> property of the <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink>.) Name the file <legacyBold>ExecuteJS.asp</legacyBold>.</para>
    <code>&lt;!-- BeginExecuteJS --&gt;
&lt;%@LANGUAGE="JScript"%&gt;
&lt;%// use this meta tag instead of adojavas.inc%&gt;
&lt;!--METADATA TYPE="typelib" uuid="00000205-0000-0010-8000-00AA006D2EA4" --&gt;

&lt;%
    strLastName = new String(Request.Form("AuthorLName"));
    
    if (strLastName.indexOf("undefined") &gt; -1)
        strLastName = "";
%&gt;

&lt;html&gt;

&lt;head&gt;
&lt;title&gt;Execute, Requery and Clear Methods Example (JScript)&lt;/title&gt;
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
&lt;h1&gt;Execute, Requery and Clear Methods Example (JScript)&lt;/h1&gt;
&lt;%
    if (strLastName.length &gt; 0)
    {
        // command and recordset variables
        var Connect = "Provider='sqloledb';Data Source=" + Request.ServerVariables("SERVER_NAME") + ";" +
            "Initial Catalog='pubs';Integrated Security='SSPI';";
        var Cnxn = Server.CreateObject("ADODB.Connection");
        var cmdAuthor = Server.CreateObject("ADODB.Command");
        var rsAuthor = Server.CreateObject("ADODB.Recordset");
        var rsAuthor2 = Server.CreateObject("ADODB.Recordset");
        var SQLAuthor2, strMessage, strMessage2;
        var Err, ErrCount;
    
        try
        {
            // open connection
            Cnxn.Open(Connect);
    
            // command object parameters
            cmdAuthor.CommandText = "SELECT * FROM Authors WHERE au_lname = ?";
            cmdAuthor.Parameters.Append(cmdAuthor.CreateParameter("Last Name", adChar, adParamInput, 20, strLastName));
            cmdAuthor.ActiveConnection = Cnxn;
        
            // recordset from command.execute
            rsAuthor = cmdAuthor.Execute();
        
            // recordset from connection.execute
            SQLAuthor2 = "SELECT * FROM Authors";
            rsAuthor2 = Cnxn.Execute(SQLAuthor2);
        
                // check for errors
                ErrCount = Cnxn.errors.count;
                if(ErrCount !== 0) //write the errors
                {
                    for(Err = 0; Err = ErrCount; Err++){
                        Err = Cnxn.errors.item;
                        Response.Write(Err);
                    }
                    // clean out any existing errors
                    Cnxn.Errors.Clear;
                }
                
                // show the data    
            Response.Write("&lt;HR&gt;&lt;HR&gt;");
        
                // first recordset
            Response.Write("&lt;b&gt;Command.Execute results&lt;/b&gt;")
            while (!rsAuthor.EOF)
            {
                // build output string by starting a new line
                strMessage = "&lt;P&gt;";
                strMessage += "&lt;br&gt;";
                    
                // recordset data 
                strMessage += rsAuthor("au_fname") + " "; 
                strMessage += rsAuthor("au_lname") + " ";
                    
                // end the line
                strMessage += "&lt;/P&gt;";
                
                // show the results
                Response.Write(strMessage);
                    
                // get next record
                rsAuthor.MoveNext;
            }
        
            Response.Write("&lt;HR&gt;&lt;HR&gt;");
        
            // second recordset
            Response.Write("&lt;b&gt;Connection.Execute results&lt;/b&gt;")
            while (!rsAuthor2.EOF)
            {
                // start a new line
                strMessage2 = "&lt;P&gt;";
                    
                // first and last name are in first column
                strMessage2 += rsAuthor2("au_fname") + " " 
                strMessage2 += rsAuthor2("au_lname") + " ";
                    
                // end the line
                strMessage2 += "&lt;/P&gt;";
                
                // show results
                Response.Write(strMessage2);
                
                // get next record
                rsAuthor2.MoveNext;
            }
        }
        catch (e)
        {
            Response.Write(e.message);
        }
        finally
        {
            // clean up
            if (rsAuthor.State == adStateOpen)
                rsAuthor.Close;
            if (rsAuthor2.State == adStateOpen)
                rsAuthor2.Close;
            if (Cnxn.State == adStateOpen)
                Cnxn.Close;
            rsAuthor1 = null;
            rsAuthor2 = null;
            Cnxn = null;
        }
    }
%&gt;

&lt;hr&gt;


&lt;form method="POST" action="ExecuteJS.asp" id=form1 name=form1&gt;
  &lt;p align="left"&gt;Enter last name of author to find (e.g., Ringer): &lt;input type="text" name="AuthorLName" size="40"&gt;&lt;/p&gt;
  &lt;p align="left"&gt;&lt;input type="submit" value="Submit" name="B1"&gt;&lt;input type="reset" value="Reset" name="B2"&gt;&lt;/p&gt;
&lt;/form&gt;
&lt;/body&gt;

&lt;/html&gt;
&lt;!-- EndExecuteJS --&gt;</code>
  </introduction>
  <relatedTopics>
<link xlink:href="0a61ba7a-20b8-426a-91a0-9040e7c5a98a">Clear Method</link>
<link xlink:href="a02c22fb-542d-465e-a629-30fd59dcbebf">Command Object</link>
<link xlink:href="ef6b1824-5b12-43db-89d7-8f3d13896d4d">Connection Object</link>
<link xlink:href="a175d453-fa55-4f49-9ede-a26d83177919">Error Object</link>
<link xlink:href="f84a5ff3-0528-4ad7-9bea-9a15103378dd">Execute Method (ADO Command)</link>
<link xlink:href="03c69320-96b2-4d85-8d49-a13b13e31578">Execute Method (ADO Connection)</link>
<link xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset Object</link>
<link xlink:href="d81ab76f-1aa8-4ccf-92ec-b65254dc3ea1">Requery Method</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>