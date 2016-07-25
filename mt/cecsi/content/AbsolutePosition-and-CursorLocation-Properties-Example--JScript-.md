---
title: "AbsolutePosition and CursorLocation Properties Example (JScript)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - JScript
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: bff98617-a6ba-4f41-9c5f-915161e3ea31
caps.latest.revision: 10
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
# AbsolutePosition and CursorLocation Properties Example (JScript)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This example demonstrates how the <legacyLink xlink:href="79f8ee5e-fc70-46d8-8c29-ebf943c66592">AbsolutePosition</legacyLink> property can track the progress of a loop that enumerates all the records of a <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink>. It uses the <legacyLink xlink:href="39c8d86e-7ee9-4182-be5e-aad5ce952f84">CursorLocation</legacyLink> property to enable the <legacyBold>AbsolutePosition</legacyBold> property by setting the cursor to a client cursor. Cut and paste the following code to Notepad or another text editor, and save it as <legacyBold>AbsolutePositionJS.asp</legacyBold>.</para>
    <code>&lt;!-- BeginAbsolutePositionJS --&gt;
&lt;%@LANGUAGE="JScript" %&gt;
&lt;%// use this meta tag instead of adojavas.inc%&gt;
&lt;!--METADATA TYPE="typelib" uuid="00000205-0000-0010-8000-00AA006D2EA4" --&gt;

&lt;html&gt;

&lt;head&gt;
&lt;title&gt;AbsolutePosition and CursorLocation Properties Example (JScript)&lt;/title&gt;
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

&lt;body&gt;
&lt;h1&gt;AbsolutePosition and CursorLocation Properties Example (JScript)&lt;/h1&gt;
&lt;%
    // connection and recordset variables
    var strCnxn = "Provider='sqloledb';Data Source=" + Request.ServerVariables("SERVER_NAME") + ";" +
            "Initial Catalog='Northwind';Integrated Security='SSPI';";
    var rsEmployee = Server.CreateObject("ADODB.Recordset");
        // display string
    var strMessage;        
    
    try
    {
        // Open a recordset on the Employee table using
        // a client-side cursor to enable AbsolutePosition property.
        rsEmployee.CursorLocation = adUseClient;
        rsEmployee.Open("employees", strCnxn, adOpenStatic, adLockOptimistic, adCmdTable);

        // Write beginning of table to the document.
        Response.Write('&lt;table border="0" align="center"&gt;');
        Response.Write('&lt;tr class="thead2"&gt;');
        Response.Write("&lt;th&gt;AbsolutePosition&lt;/th&gt;&lt;th&gt;Name&lt;/th&gt;&lt;th&gt;Hire Date&lt;/th&gt;&lt;/tr&gt;");
    
        while (!rsEmployee.EOF)
        {
            strMessage = "";
                
            // Start a new table row.
            strMessage = '&lt;tr class="tbody"&gt;';
                    
            // First column in row contains AbsolutePosition value.
            strMessage += "&lt;td&gt;" + rsEmployee.AbsolutePosition + " of " + rsEmployee.RecordCount + "&lt;/td&gt;"
                        
            // First and last name are in first column.
            strMessage += "&lt;td&gt;" + rsEmployee.Fields("FirstName") + " ";
            strMessage += rsEmployee.Fields("LastName") + " " + "&lt;/td&gt;";
                    
            // Hire date in second column.
            strMessage += "&lt;td&gt;" + rsEmployee.Fields("HireDate") + "&lt;/td&gt;";
                    
            // End the row.
            strMessage += "&lt;/tr&gt;";
                
            // Write line to document.
            Response.Write(strMessage);
                    
            // Get next record.
            rsEmployee.MoveNext;
        }
    
        // Finish writing document.
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
        rsEmployee = null;
    }
%&gt;

&lt;/html&gt;
&lt;!-- EndAbsolutePositionJS --&gt;</code>
  </introduction>
  <relatedTopics>
<link xlink:href="79f8ee5e-fc70-46d8-8c29-ebf943c66592">AbsolutePosition Property</link>
<link xlink:href="39c8d86e-7ee9-4182-be5e-aad5ce952f84">CursorLocation Property</link>
<link xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset Object</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>