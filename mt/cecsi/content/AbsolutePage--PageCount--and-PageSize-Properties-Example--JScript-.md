---
title: "AbsolutePage, PageCount, and PageSize Properties Example (JScript)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - JScript
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2db6dd3f-5a9c-438c-ae62-d09242906c98
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
# AbsolutePage, PageCount, and PageSize Properties Example (JScript)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This example demonstrates the AbsolutePage, PageCount and PageSize properties. Cut and paste the following code to Notepad or another text editor, and save it as <legacyBold>AbsolutePageJS.asp</legacyBold>.</para>
    <code>&lt;!-- BeginAbsolutePageJS --&gt;
&lt;%@LANGUAGE="JScript" %&gt;
&lt;%// use this meta tag instead of adojavas.inc%&gt;
&lt;!--METADATA TYPE="typelib" uuid="00000205-0000-0010-8000-00AA006D2EA4" --&gt;

&lt;html&gt;

&lt;head&gt;
&lt;title&gt;AbsolutePage, PageSize, and PageSize Properties (JScript)&lt;/title&gt;
&lt;style&gt;
&lt;!--
BODY {
   font-family: 'Verdana','Arial','Helvetica',sans-serif;
   BACKGROUND-COLOR:white;
   COLOR:black;
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
&lt;h1&gt;AbsolutePage, PageSize, and PageSize Properties (JScript)&lt;/h1&gt;
&lt;%
    // connection and recordset variables
    var Cnxn = Server.CreateObject("ADODB.Connection")
    var strCnxn = "Provider='sqloledb';Data Source=" + Request.ServerVariables("SERVER_NAME") + ";" +
            "Initial Catalog='Northwind';Integrated Security='SSPI';";
    var rsEmployee = Server.CreateObject("ADODB.Recordset");
    // display variables
    var strMessage, iRecord, iPageCount;
    
    try
    {
        // open connection
        Cnxn.Open(strCnxn);
    
        // Open a recordset on the Employee table using
        // a client-side cursor to enable AbsolutePage property.
        rsEmployee.CursorLocation = adUseClient;
        rsEmployee.Open("employees", strCnxn, adOpenStatic, adLockOptimistic, adCmdTable);
    
        // Set PageSize to five to display names and hire dates of five employees at a time
        rsEmployee.PageSize = 5; 
        iPageCount = rsEmployee.PageCount;
    
        // Write header information to the document
        Response.Write('&lt;p align="center"&gt;There are ' + iPageCount);
        Response.Write(" pages, each containing ");
        Response.Write(rsEmployee.PageSize + " or fewer records.&lt;/p&gt;");
        Response.Write('&lt;table border="0" align="center"&gt;');
        Response.Write('&lt;tr class="thead2"&gt;');
        Response.Write("&lt;th&gt;Page&lt;/th&gt;&lt;th&gt;Name&lt;/th&gt;&lt;th&gt;Hire Date&lt;/th&gt;&lt;/tr&gt;");
    
        for (var i=1; i&lt;=iPageCount; i++)
        {
            rsEmployee.AbsolutePage = i;
            
            for (iRecord = 1; iRecord &lt;= rsEmployee.PageSize; iRecord++)
            {
                strMessage = "";
                
                    // Start a new table row.
                    strMessage = '&lt;tr class="tbody"&gt;';
                    
                    // First column in row contains page number on
                    // first record of each page. Otherwise, the column
                    // contains a non-breaking space.
                    if (iRecord == 1)
                        strMessage += "&lt;td&gt;Page " + i + " of " + rsEmployee.PageCount + "&lt;/td&gt;"
                    else
                        strMessage += "&lt;td&gt;&amp;nbsp;&lt;/td&gt;";
                        
                    // First and last name are in first column.
                    strMessage += "&lt;TD&gt;" + rsEmployee.Fields("FirstName") + " ";
                    strMessage += rsEmployee.Fields("LastName") + " " + "&lt;/td&gt;";
                    
                    // Hire date in second column.
                    strMessage += "&lt;td&gt;" + rsEmployee.Fields("HireDate") + "&lt;/td&gt;";
                    
                    // End the row.
                    strMessage += "&lt;/tr&gt;";
                
                    // Write line to document.
                    Response.Write(strMessage);
                    
                    // Get next record.
                    rsEmployee.MoveNext;
                    
                    if (rsEmployee.EOF)
                        break;
            }
        }
    
        // Finish writing table.
        Response.Write("&lt;/table&gt;");
    }
    catch (e)
    {
        Response.Write(e.message);
    }
    finally
    {
        // 'clean up
        if (rsEmployee.State == adStateOpen)
            rsEmployee.Close;
        if (Cnxn.State == adStateOpen)
            Cnxn.Close;
        rsEmployee = null;
        Cnxn = null;
    }
%&gt;

&lt;/body&gt;

&lt;/html&gt;
&lt;!-- EndAbsolutePageJS --&gt;</code>
  </introduction>
  <relatedTopics>
<link xlink:href="ddb58a35-ec3a-423c-a504-3c65e62c23d4">AbsolutePage Property</link>
<link xlink:href="b601b56c-0ac4-44ee-bc91-c3d2d104f00a">PageCount Property</link>
<link xlink:href="e57930a6-46c4-4a17-a3b6-f79e94d5c9c7">PageSize Property</link>
<link xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset Object</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>