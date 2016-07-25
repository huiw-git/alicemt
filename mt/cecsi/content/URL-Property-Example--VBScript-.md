---
title: "URL Property Example (VBScript)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - VB
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6ae5ac50-c88c-4262-b7ab-f2b3de382a0b
caps.latest.revision: 12
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
# URL Property Example (VBScript)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <alert class="important">
      <para>Beginning with Windows 8 and Windows Server 2012, RDS server components are no longer included in the Windows operating system (see Windows 8 and <externalLink><linkText>Windows Server 2012 Compatibility Cookbook</linkText><linkUri>http://download.microsoft.com/download/2/C/9/2C9C7B01-A1FC-47B6-9166-2151FB6E007C/Windows 8 and Windows Server 2012 Compatibility Cookbook.docx</linkUri></externalLink> for more detail). RDS client components will be removed in a future version of Windows. Avoid using this feature in new development work, and plan to modify applications that currently use this feature. Applications that use RDS should migrate to <externalLink><linkText>WCF Data Service</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=199565</linkUri></externalLink>.</para>
    </alert>
    <para>The following code demonstrates how to set the <legacyBold>URL</legacyBold> property on the client side to specify an .asp file that in turn handles the submission of changes to the data source.</para>
    <code>&lt;!-- BeginURLClientVBS --&gt;
&lt;%@ Language=VBScript %&gt;
&lt;html&gt;
&lt;head&gt;
    &lt;meta name="VI60_DefaultClientScript"  content=VBScript&gt;
    &lt;meta name="GENERATOR" content="Microsoft Visual Studio 6.0"&gt;
    &lt;title&gt;URL Property Example (VBScript)&lt;/title&gt;
&lt;style&gt;
&lt;!--
body {
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

&lt;body onload=Getdata()&gt;
&lt;h1&gt;URL Property Example (VBScript)&lt;/h1&gt;
&lt;OBJECT classid=clsid:BD96C556-65A3-11D0-983A-00C04FC29E33 height=1 id=ADC width=1&gt;
&lt;/OBJECT&gt;

&lt;table datasrc="#ADC" align="center"&gt;
&lt;thead&gt;
&lt;tr id="ColHeaders" class="thead2"&gt;
   &lt;th&gt;FirstName&lt;/th&gt;
   &lt;th&gt;LastName&lt;/th&gt;
   &lt;th&gt;Extension&lt;/th&gt;
&lt;/tr&gt;
&lt;/thead&gt;
&lt;tbody class="tbody"&gt;
&lt;tr&gt;
   &lt;td&gt;&lt;input datafld="FirstName" size=15&gt; &lt;/td&gt;
   &lt;td&gt;&lt;input datafld="LastName" size=25&gt; &lt;/td&gt;
   &lt;td&gt;&lt;input datafld="Extension" size=15&gt; &lt;/td&gt;
&lt;/tr&gt;
&lt;/tbody&gt;
&lt;/table&gt;

&lt;script Language="VBScript"&gt;
Sub Getdata()

      ADC.URL = "http://MyServer/URLServerVBS.asp"
      ADC.Refresh
End Sub

&lt;/script&gt;



&lt;/body&gt;
&lt;/html&gt;
&lt;!-- EndURLClientVBS --&gt;</code>
    <para>The server-side code that exists in <legacyBold>URLServerVBS.asp</legacyBold> submits the updated <legacyBold>Recordset</legacyBold> to the data source.</para>
    <code>&lt;!-- BeginURLServerVBS --&gt;
&lt;%@ Language=VBScript %&gt;
&lt;%

        ' XML output req's
    Response.ContentType = "text/xml"
    const adPersistXML  = 1
    
        ' recordset vars
    Dim strSQL, rsEmployees 
    Dim strCnxn, Cnxn
    
    strCnxn = "Provider='sqloledb';Data Source=" &amp; _
            Request.ServerVariables("SERVER_NAME") &amp; ";" &amp; _
            "Integrated Security='SSPI';Initial Catalog='Northwind';"
    Set Cnxn = Server.CreateObject("ADODB.Connection")
    Set rsEmployees = Server.CreateObject("ADODB.Recordset")
    
    strSQL = "SELECT FirstName, LastName, Extension FROM Employees"

    Cnxn.Open strCnxn
    rsEmployees.Open strSQL, Cnxn
    
        ' output as XML
    rsEmployees.Save Response, adPersistXML

        ' Clean up
    rsEmployees.Close
    Cnxn.Close
    Set rsEmployees = Nothing
    Set Cnxn = Nothing
%&gt;
&lt;!-- EndURLServerVBS --&gt;</code>
  </introduction>
  <relatedTopics>
<link xlink:href="8c56b233-1be8-442c-8d0e-a4c96465bc99">URL Property (RDS)</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>