---
title: "ActualSize and DefinedSize Properties Example (JScript)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - JScript
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 23575e70-2304-43b4-b8be-99d9a6842589
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
# ActualSize and DefinedSize Properties Example (JScript)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This example uses the <legacyLink xlink:href="722803d0-cef5-4d4c-b79d-3f2f58052229">ActualSize</legacyLink> and <legacyLink xlink:href="3ee27314-a305-4fbc-8433-9ee9a909afd6">DefinedSize</legacyLink> properties to display the defined size and actual size of a field. Cut and paste the following code to Notepad or another text editor, and save it as <legacyBold>ActualSizeJS.asp</legacyBold>.</para>
    <code>&lt;!-- BeginActualSizeJS --&gt;
&lt;%@LANGUAGE="JScript" %&gt;
&lt;%// use this meta tag instead of adojavas.inc%&gt;
&lt;!--METADATA TYPE="typelib" uuid="00000205-0000-0010-8000-00AA006D2EA4" --&gt;
&lt;html&gt;

&lt;head&gt;
    &lt;title&gt;ActualSize and DefinedSize Properties Example (JScript)&lt;/title&gt;
&lt;style&gt;
&lt;!--
body {
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

&lt;h1&gt;ADO ActualSize and DefinedSize Properties (JScript)&lt;/h1&gt;
&lt;%
    // connection and recordset variables
    var Cnxn = Server.CreateObject("ADODB.Connection")
    var strCnxn = "Provider='sqloledb';Data Source=" + Request.ServerVariables("SERVER_NAME") + ";" +
            "Initial Catalog='Northwind';Integrated Security='SSPI';";
    var rsSuppliers = Server.CreateObject("ADODB.Recordset");
    // display variables
    var fld, strMessage;        
    
    try
    {
        // open connection
        Cnxn.Open(strCnxn);
    
        // Open a recordset on the stores table    
        rsSuppliers.Open("Suppliers", strCnxn);
    
        // build table headers
        Response.Write("&lt;table&gt;");
        Response.Write('&lt;tr class="thead2"&gt;&lt;th&gt;Field Value&lt;/th&gt;');
        Response.Write("&lt;th&gt;Defined Size&lt;/th&gt;");
        Response.Write("&lt;th&gt;Actual Size&lt;/th&gt;&lt;/tr&gt;");
            
        while (!rsSuppliers.EOF)
        {
            // start a new line
            strMessage = '&lt;tr class="tbody"&gt;';
                    
            // Display the contents of the chosen field with
            // its defined size and actual size
            fld = rsSuppliers("CompanyName");
            strMessage += '&lt;td align="left"&gt;' + fld.Value + "&lt;/td&gt;" 
            strMessage += "&lt;td&gt;" + fld.DefinedSize + "&lt;/td&gt;";
            strMessage += "&lt;td&gt;" + fld.ActualSize + "&lt;/td&gt;";
                    
            // end the line
            strMessage += "&lt;/tr&gt;";
                
            // display data
            Response.Write(strMessage);
                    
            // get next record
            rsSuppliers.MoveNext;

        }
         // close the table
        Response.Write("&lt;/table&gt;");
    }
    catch (e)
    {
        Response.Write(e.message);
    }
    finally
    {
        // clean up
        if (rsSuppliers.State == adStateOpen)
            rsSuppliers.Close;
        if (Cnxn.State == adStateOpen)
            Cnxn.Close;
        rsSuppliers = null;
        Cnxn = null;
    }
%&gt;

&lt;/body&gt;

&lt;/html&gt;
&lt;!-- EndActualSizeJS --&gt;</code>
  </introduction>
  <relatedTopics>
<link xlink:href="722803d0-cef5-4d4c-b79d-3f2f58052229">ActualSize Property</link>
<link xlink:href="3ee27314-a305-4fbc-8433-9ee9a909afd6">DefinedSize Property</link>
<link xlink:href="b10a72fc-3c4b-4186-a70b-993dc9f7a092">Field Object</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>