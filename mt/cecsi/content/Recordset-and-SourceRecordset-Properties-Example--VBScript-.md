---
title: "Recordset and SourceRecordset Properties Example (VBScript)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - VB
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 95175316-cd10-4cf7-96ba-2a226fd97701
caps.latest.revision: 13
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
# Recordset and SourceRecordset Properties Example (VBScript)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <alert class="important">
      <para>Beginning with Windows 8 and Windows Server 2012, RDS server components are no longer included in the Windows operating system (see Windows 8 and <externalLink><linkText>Windows Server 2012 Compatibility Cookbook</linkText><linkUri>http://download.microsoft.com/download/2/C/9/2C9C7B01-A1FC-47B6-9166-2151FB6E007C/Windows 8 and Windows Server 2012 Compatibility Cookbook.docx</linkUri></externalLink> for more detail). RDS client components will be removed in a future version of Windows. Avoid using this feature in new development work, and plan to modify applications that currently use this feature. Applications that use RDS should migrate to <externalLink><linkText>WCF Data Service</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=199565</linkUri></externalLink>.</para>
    </alert>
    <para>The following example shows how to set the necessary parameters of the <legacyLink xlink:href="e75240c2-b749-471e-b6ea-98cae232efbe">RDSServer.DataFactory</legacyLink> default business object at run time.</para>
    <para>To test this example, cut and paste this code between the &lt;Body&gt; and &lt;/Body&gt; tags in a normal HTML document and name it <legacyBold>RecordsetVBS.asp</legacyBold>. ASP script will identify your server.</para>
    <code>&lt;!-- BeginRecordSetVBS --&gt;
&lt;%@ Language=VBScript %&gt;
&lt;html&gt;
&lt;head&gt;
    &lt;meta name="VI60_DefaultClientScript"  content=VBScript&gt;
    &lt;meta name="GENERATOR" content="Microsoft Visual Studio 6.0"&gt;
    &lt;title&gt;Recordset and SourceRecordset Properties Example (VBScript)&lt;/title&gt;
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

&lt;body&gt;
&lt;h1&gt;Recordset and SourceRecordset Properties Example (VBScript)&lt;/h1&gt;

&lt;Center&gt;
&lt;H2&gt;RDS API Code Examples&lt;/H2&gt;
&lt;HR&gt;
&lt;H3&gt;Using SourceRecordset and Recordset with RDSServer.DataFactory&lt;/H3&gt;
&lt;!-- RDS.DataSpace ID RDS1 --&gt;
&lt;OBJECT ID="RDS1" WIDTH=1 HEIGHT=1 
CLASSID="CLSID:BD96C556-65A3-11D0-983A-00C04FC29E36"&gt;
&lt;/OBJECT&gt;

&lt;!-- RDS.DataControl with parameters set at Run Time --&gt;
&lt;OBJECT classid="clsid:BD96C556-65A3-11D0-983A-00C04FC29E33"
   ID=RDC WIDTH=1 HEIGHT=1&gt;
&lt;/OBJECT&gt;

&lt;TABLE DATASRC=#RDC&gt;
   &lt;TR&gt;
      &lt;TD&gt; &lt;INPUT DATAFLD="FirstName" SIZE=15&gt; &lt;/TD&gt;
      &lt;TD&gt; &lt;INPUT DATAFLD="LastName" SIZE=15&gt;&lt;/TD&gt;
   &lt;/TR&gt;
&lt;/TABLE&gt;
&lt;HR&gt;
&lt;Input Size=70 Name="txtServer" Value="http://&lt;%=Request.ServerVariables("SERVER_NAME")%&gt;"&gt;&lt;BR&gt;
&lt;Input Size=70 Name="txtConnect" Value="Provider='sqloledb';Integrated Security='SSPI';Initial Catalog='Northwind'"&gt;&lt;BR&gt;
&lt;Input Size=70 Name="txtSQL" Value="SELECT FirstName, LastName FROM Employees"&gt;
&lt;HR&gt;
&lt;INPUT TYPE=BUTTON NAME="Run" VALUE="Run"&gt;&lt;BR&gt;

&lt;/Center&gt;
&lt;Script Language="VBScript"&gt;

   Dim rdsDF
   Dim strServer
   strServer = "http://&lt;%=Request.ServerVariables("SERVER_NAME")%&gt;"

   Sub Run_OnClick()
   
      Dim rs         
      ' Create RDSServer.DataFactory Object
      Set rdsDF = RDS1.CreateObject("RDSServer.DataFactory", strServer)               
      ' Get Recordset
      Set rs = rdsDF.Query(txtConnect.Value,txtSQL.Value)

      ' Set parameters of RDS.DataControl at run time
      RDC.Server = txtServer.Value
      RDC.SQL = txtSQL.Value
      RDC.Connect = txtConnect.Value
      RDC.Refresh
   
   End Sub

&lt;/Script&gt;

&lt;/body&gt;
&lt;/html&gt;
&lt;!-- EndRecordsetVBS --&gt;</code>
  </introduction>
  <relatedTopics>
<link xlink:href="e75240c2-b749-471e-b6ea-98cae232efbe">DataFactory Object (RDSServer)</link>
<link xlink:href="a29e3fb9-306d-497a-9a59-1856a914e5e9">Recordset, SourceRecordset Properties (RDS)</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>