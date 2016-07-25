---
title: "GetRows Method Example (JScript)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - JScript
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d33467a5-5a56-450d-98c1-c3ce6f9f103c
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
# GetRows Method Example (JScript)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This example uses the <legacyLink xlink:href="14b92860-4171-47d9-a413-dd60dd6a8880">GetRows</legacyLink> method to retrieve all rows of the <legacyItalic>Custiomers</legacyItalic> table from a <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink> and to fill an array with the resulting data. The <legacyBold>GetRows</legacyBold> method will return fewer than the desired number of rows in two cases: either if <legacyLink xlink:href="36c31ab2-f3b6-4281-89b6-db7e04e38fd2">EOF</legacyLink> has been reached, or if <legacyBold>GetRows</legacyBold> tried to retrieve a record that was deleted by another user. The function returns <legacyBold>False</legacyBold> only if the second case occurs. Cut and paste the following code to Notepad or another text editor, and save it as <legacyBold>GetRowsJS.asp</legacyBold>.</para>
    <code>&lt;!-- BeginGetRowsJS --&gt;
&lt;%@ LANGUAGE="JScript" %&gt;
&lt;%// use this meta tag instead of adojavas.inc%&gt;
&lt;!--METADATA TYPE="typelib" uuid="00000205-0000-0010-8000-00AA006D2EA4" --&gt;

&lt;html&gt;

&lt;head&gt;
&lt;title&gt;ADO Recordset.GetRows Example (JScript)&lt;/title&gt;
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

&lt;h1&gt;ADO Recordset.GetRows Example (JScript)&lt;/h1&gt;
    &lt;!-- Page text goes here --&gt;
&lt;%
        var Connect = "Provider='sqloledb';Data Source=" + Request.ServerVariables("SERVER_NAME") + ";" +
            "Initial Catalog='Northwind';Integrated Security='SSPI';";
    var mySQL = "select * from customers;";
    var showblank = " ";
    var shownull = "-null-";
    
    var connTemp = Server.CreateObject("ADODB.Connection");
    
    try
    {
        connTemp.Open(Connect);
        var rsTemp = Server.CreateObject("ADODB.Recordset");
        rsTemp.ActiveConnection = connTemp;
        rsTemp.CursorLocation = adUseClient;
        rsTemp.CursorType = adOpenKeyset;
        rsTemp.LockType = adLockOptimistic;
        rsTemp.Open(mySQL);
    
        rsTemp.MoveFirst();
    
        if (rsTemp.RecordCount == 0)
        {
            Response.Write("No records matched ");
            Response.Write (mySQL &amp; "So cannot make table...");
            connTemp.Close();
            Response.End();
        } else
        {
            Response.Write('&lt;table width="100%" border="2"&gt;');
            Response.Write('&lt;tr class="thead2"&gt;');
            
            //  Headings On The Table for each Field Name
            for (var i=0; i&lt;rsTemp.Fields.Count; i++)
            {
                fieldObject = rsTemp.fields(i);
                Response.Write('&lt;td width="' + Math.floor(100 / rsTemp.Fields.Count) + '%"&gt;' + fieldObject.name + "&lt;/td&gt;");
            }
            
            Response.Write("&lt;/tr&gt;");
            
            // JScript doesn't support multi-dimensional arrays
            // so we'll convert the returned array to a single
            // dimensional JScript array and then display the data.
            tempArray = rsTemp.GetRows();
            recArray = tempArray.toArray();
            
            var col = 1;
            var maxCols = rsTemp.Fields.Count;
                    
            for (var thisField=0; thisField&lt;recArray.length; thisField++)
            {
                if (col == 1)
                    Response.Write('&lt;tr class="tbody"&gt;');
                if (recArray[thisField] == null)
                        recArray[thisField] = shownull;
                if (recArray[thisField] == "")
                        recArray[thisField] = showblank;
                Response.Write("&lt;td&gt;" + recArray[thisField] + "&lt;/td&gt;");
                col++
                if (col &gt; maxCols)
                {
                    Response.Write("&lt;/tr&gt;");
                    col = 1;
                }
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
        if (rsTemp.State == adStateOpen)
            rsTemp.Close;
        if (connTemp.State == adStateOpen)
            connTemp.Close;
        rsTemp = null;
        connTemp = null;
    }
%&gt;

&lt;/body&gt;

&lt;/html&gt;
&lt;!-- EndGetRowsJS --&gt;</code>
  </introduction>
  <relatedTopics>
<link xlink:href="14b92860-4171-47d9-a413-dd60dd6a8880">GetRows Method</link>
<link xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset Object</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>