---
title: "ActiveConnection, CommandText, CommandTimeout, CommandType, Size, and Direction Properties Example (JScript)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - JScript
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ea74e2a3-c965-43aa-9076-26a084b48ad8
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
# ActiveConnection, CommandText, CommandTimeout, CommandType, Size, and Direction Properties Example (JScript)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This example uses the <legacyLink xlink:href="52d0a96c-14fb-4ad9-b004-4d821bc0a6db">ActiveConnection</legacyLink>, <legacyLink xlink:href="4dd7e82a-8da5-4a4e-b439-11a29286fa0e">CommandText</legacyLink>, <legacyLink xlink:href="c611f857-d6b0-4dca-8925-f4a02e769eb0">CommandTimeout</legacyLink>, <legacyLink xlink:href="ca44809c-8647-48b6-a7fb-0be70a02f53e">CommandType</legacyLink>, <legacyLink xlink:href="e6bad449-ebdb-4dd3-886a-9e6f1e7ee5d2">Size</legacyLink>, and <legacyLink xlink:href="d5732578-3434-4dcd-a9f7-db1abd1b3b94">Direction</legacyLink> properties to execute a stored procedure. Cut and paste the following code to Notepad or another text editor, and save it as <legacyBold>ActiveConnectionJS.asp</legacyBold>.</para>
    <code>&lt;!-- BeginActiveConnectionJS --&gt;
&lt;%@LANGUAGE="JScript"%&gt;
&lt;%// use this meta tag instead of adojavas.inc%&gt;
&lt;!--METADATA TYPE="typelib" uuid="00000205-0000-0010-8000-00AA006D2EA4" --&gt;

&lt;html&gt;
&lt;head&gt;
    &lt;title&gt;ActiveConnection, CommandText, CommandTimeout, CommandType, Size, and Direction Properties&lt;/title&gt;
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

&lt;%
    var iRoyalty = parseInt(Request.Form("RoyaltyValue"));
    // check user input
    
    if (iRoyalty &gt; -1)
    {
            // connection and recordset variables
        var Cnxn = Server.CreateObject("ADODB.Connection")
        var strCnxn = "Provider='sqloledb';Data Source=" + Request.ServerVariables("SERVER_NAME") + ";" +
            "Initial Catalog='pubs';Integrated Security='SSPI';";
        var cmdByRoyalty = Server.CreateObject("ADODB.Command");
        var rsByRoyalty = Server.CreateObject("ADODB.Recordset");
        var rsAuthor = Server.CreateObject("ADODB.Recordset");
        // display variables
        var filter, strMessage;        
        
        try
        {
            // open connection
            Cnxn.Open(strCnxn);
    
            cmdByRoyalty.CommandText = "byroyalty";
            cmdByRoyalty.CommandType = adCmdStoredProc;
            cmdByRoyalty.CommandTimeOut = 15;
    
            // The stored procedure called above is as follows:
                //    CREATE PROCEDURE byroyalty
                //  @percentage int
                //    AS
                //  SELECT au_id from titleauthor
                //  WHERE titleauthor.royaltyper = @percentage
                //  GO
        
            prmByRoyalty = Server.CreateObject("ADODB.Parameter");
            prmByRoyalty.Type = adInteger;
            prmByRoyalty.Size = 3;
            prmByRoyalty.Direction = adParamInput;
            prmByRoyalty.Value = iRoyalty;
            cmdByRoyalty.Parameters.Append(prmByRoyalty);
        
            cmdByRoyalty.ActiveConnection = Cnxn;
        
            // recordset by Command - Execute
            rsByRoyalty = cmdByRoyalty.Execute();
        
            // recordset by Recordset - Open
            rsAuthor.Open("Authors", Cnxn);
    
            while (!rsByRoyalty.EOF)
            {
                // set filter
                filter = "au_id='" + rsByRoyalty("au_id")
                rsAuthor.Filter = filter + "'";
                
                // start new line
                strMessage = "&lt;P&gt;";
                    
                // get data
                strMessage += rsAuthor("au_fname") + " "; 
                strMessage += rsAuthor("au_lname") + " ";
                    
                // end line
                strMessage += "&lt;/P&gt;";
                
                // show data
                Response.Write(strMessage);
                    
                // get next record
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


&lt;form method="POST" action="ActiveConnectionJS.asp"&gt;
  &lt;p align="left"&gt;Enter royalty percentage to find (e.g., 40): &lt;input type="text" name="RoyaltyValue" size="5"&gt;&lt;/p&gt;
  &lt;p align="left"&gt;&lt;input type="submit" value="Submit" name="B1"&gt;&lt;input type="reset" value="Reset" name="B2"&gt;&lt;/p&gt;
&lt;/form&gt;
&amp;nbsp;


&lt;/body&gt;

&lt;/html&gt;
&lt;!-- EndActiveConnectionJS --&gt;</code>
  </introduction>
  <relatedTopics>
<link xlink:href="fb4088d5-5968-42d6-aeaa-3955046bb4da">ActiveCommand Property</link>
<link xlink:href="a02c22fb-542d-465e-a629-30fd59dcbebf">Command Object</link>
<link xlink:href="4dd7e82a-8da5-4a4e-b439-11a29286fa0e">CommandText Property</link>
<link xlink:href="c611f857-d6b0-4dca-8925-f4a02e769eb0">CommandTimeout Property</link>
<link xlink:href="ca44809c-8647-48b6-a7fb-0be70a02f53e">CommandType Property</link>
<link xlink:href="ef6b1824-5b12-43db-89d7-8f3d13896d4d">Connection Object</link>
<link xlink:href="d5732578-3434-4dcd-a9f7-db1abd1b3b94">Direction Property</link>
<link xlink:href="e010e794-7f0f-4026-8b5b-37328e437d63">Parameter Object</link>
<link xlink:href="db83ed2c-a8e3-460c-8682-64667e4d5d01">Record Object</link>
<link xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset Object</link>
<link xlink:href="e6bad449-ebdb-4dd3-886a-9e6f1e7ee5d2">Size Property</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>