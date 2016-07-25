---
title: "CacheSize Property Example (JScript)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - JScript
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3675f641-b4b1-48ff-ba33-8d9ea064cd04
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
# CacheSize Property Example (JScript)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This example uses the <legacyLink xlink:href="49dc9a49-af7b-433b-be36-7a14ca984fb7">CacheSize</legacyLink> property to show the difference in performance for an operation performed with and without a 30-record cache. Cut and paste the following code to Notepad or another text editor, and save it as <legacyBold>CacheSizeJS.asp</legacyBold>.</para>
    <code>&lt;!-- BeginCacheSizeJS --&gt;
&lt;%@ Language="JScript" %&gt;
&lt;%// use this meta tag instead of adojavas.inc%&gt;
&lt;!--METADATA TYPE="typelib" uuid="00000205-0000-0010-8000-00AA006D2EA4" --&gt;

&lt;HTML&gt;
&lt;HEAD&gt;
&lt;title&gt;CacheSize Property Example (JScript)&lt;/title&gt;
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
&lt;/HEAD&gt;
&lt;BODY&gt;
&lt;h1&gt;CacheSize Property Example (JScript)&lt;/h1&gt;
&lt;%
    // connection and recordset variables
    var Cnxn = Server.CreateObject("ADODB.Connection")
    var strCnxn = "Provider='sqloledb';Data Source=" + Request.ServerVariables("SERVER_NAME") + ";" +
            "Initial Catalog='Northwind';Integrated Security='SSPI';";
    var rsCustomer = Server.CreateObject("ADODB.Recordset");
    // caching variables
    var Now = new Date();
    var Start = Now.getTime();
    var End, Cache, NoCache
    
    try
    {
        // open connection
        Cnxn.Open(strCnxn)
    
        // open a recordset on the Employee table using client-side cursor
        rsCustomer.CursorLocation = adUseClient;
        rsCustomer.Open("Customers", strCnxn);
    
        // loop through the recordset 20 times
        for (var i=1; i&lt;=20; i++)
        {
            rsCustomer.MoveFirst();
            while (!rsCustomer.EOF)
            {
                // do something with the record
                var strTemp = new String(rsCustomer("CompanyName"));
                rsCustomer.MoveNext();
            }
        }
    
        Now = new Date();
        End = Now.getTime();
        NoCache = End - Start;

        // cache records in groups of 30
        rsCustomer.MoveFirst();
        rsCustomer.CacheSize = 30;
    
        Now = new Date();
        Start = Now.getTime();
    
        // loop through the recordset 20 times
        for (var i=1; i&lt;=20; i++)
        {
            rsCustomer.MoveFirst();
            while (!rsCustomer.EOF)
            {
                // do something with the record
                var strTemp = new String(rsCustomer("CompanyName"));
                rsCustomer.MoveNext();
            }
        }
    
        Now = new Date();
        End = Now.getTime();
        var Cache = End - Start;
    }
    catch (e)
    {
        Response.Write(e.message);
    }
    finally
    {
        // clean up
        if (rsCustomer.State == adStateOpen)
            rsCustomer.Close;
        if (Cnxn.State == adStateOpen)
            Cnxn.Close;
        rsCustomer = null;
        Cnxn = null;
    }
%&gt;

    &lt;table border="2"&gt;
        &lt;tr class="thead2"&gt;
            &lt;th&gt;No Cache&lt;/th&gt;
            &lt;th&gt;30 Record Cache&lt;/th&gt;
        &lt;/tr&gt;
        &lt;tr class="tbody"&gt;
            &lt;td&gt;&lt;%=NoCache%&gt;&lt;/td&gt;
            &lt;td&gt;&lt;%=Cache%&gt;&lt;/td&gt;
        &lt;/tr&gt;
    &lt;/table&gt;

&lt;/BODY&gt;
&lt;/HTML&gt;
&lt;!-- EndCacheSizeJS --&gt;</code>
  </introduction>
  <relatedTopics>
<link xlink:href="49dc9a49-af7b-433b-be36-7a14ca984fb7">CacheSize Property</link>
<link xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset Object</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>