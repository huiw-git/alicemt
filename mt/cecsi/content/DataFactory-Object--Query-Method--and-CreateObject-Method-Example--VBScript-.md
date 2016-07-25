---
title: "DataFactory Object, Query Method, and CreateObject Method Example (VBScript)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - VB
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b4e2844a-120a-4513-860b-f1b6e4b5dda4
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
# DataFactory Object, Query Method, and CreateObject Method Example (VBScript)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <alert class="important">
      <para>Beginning with Windows 8 and Windows Server 2012, RDS server components are no longer included in the Windows operating system (see Windows 8 and <externalLink><linkText>Windows Server 2012 Compatibility Cookbook</linkText><linkUri>http://download.microsoft.com/download/2/C/9/2C9C7B01-A1FC-47B6-9166-2151FB6E007C/Windows 8 and Windows Server 2012 Compatibility Cookbook.docx</linkUri></externalLink> for more detail). RDS client components will be removed in a future version of Windows. Avoid using this feature in new development work, and plan to modify applications that currently use this feature. Applications that use RDS should migrate to <externalLink><linkText>WCF Data Service</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=199565</linkUri></externalLink>.</para>
    </alert>
    <para>This example creates an <legacyLink xlink:href="e75240c2-b749-471e-b6ea-98cae232efbe">RDSServer.DataFactory</legacyLink> object using the <legacyLink xlink:href="dec96be6-0b31-4953-9c9a-e962b5afcd18">CreateObject</legacyLink> method of the <legacyLink xlink:href="9194bffa-5bdf-4dff-af86-f7158c23bfa7">RDS.DataSpace</legacyLink> object. To test this example, cut and paste this code between the &lt;Body&gt; and &lt;/Body&gt; tags in a normal HTML document and name it <legacyBold>DataFactoryVBS.asp</legacyBold>. ASP script will identify your server.</para>
    <code>&lt;!-- BeginDataFactoryVBS --&gt;
&lt;HTML&gt;
&lt;HEAD&gt;
&lt;!--use the following META tag instead of adovbs.inc--&gt;
&lt;!--METADATA TYPE="typelib" uuid="00000205-0000-0010-8000-00AA006D2EA4" --&gt;
&lt;META name="VI60_DefaultClientScript" Content="VBScript"&gt;

&lt;META NAME="GENERATOR" Content="Microsoft Visual Studio 6.0"&gt;
&lt;TITLE&gt;DataFactory Object, Query Method, and 
CreateObject Method Example (VBScript)&lt;/TITLE&gt;
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
&lt;/HEAD&gt;
&lt;BODY&gt;
&lt;h1&gt;DataFactory Object, Query Method, and 
CreateObject Method Example (VBScript)&lt;/h1&gt;
&lt;H2&gt;RDS API Code Examples&lt;/H2&gt;
&lt;HR&gt;
&lt;H3&gt;Using Query Method of RDSServer.DataFactory&lt;/H3&gt;

&lt;!-- RDS.DataSpace  ID RDS1--&gt;
&lt;OBJECT ID="RDS1" WIDTH=1 HEIGHT=1
CLASSID="CLSID:BD96C556-65A3-11D0-983A-00C04FC29E36"&gt;
&lt;/OBJECT&gt;

&lt;!-- RDS.DataControl with parameters 
set at run time --&gt;
&lt;OBJECT classid="clsid:BD96C556-65A3-11D0-983A-00C04FC29E33"
   ID=RDS WIDTH=1 HEIGHT=1&gt;
&lt;/OBJECT&gt;

&lt;TABLE DATASRC=#RDS&gt;
&lt;TBODY&gt;
  &lt;TR&gt;
    &lt;TD&gt;&lt;SPAN DATAFLD="FirstName"&gt;&lt;/SPAN&gt;&lt;/TD&gt;
    &lt;TD&gt;&lt;SPAN DATAFLD="LastName"&gt;&lt;/SPAN&gt;&lt;/TD&gt;
  &lt;/TR&gt;
&lt;/TBODY&gt;    
&lt;/TABLE&gt;

&lt;HR&gt;
&lt;INPUT TYPE=BUTTON NAME="Run" VALUE="Run"&gt;
&lt;BR&gt;
&lt;H4&gt;Click Run -  
The &lt;i&gt;CreateObject&lt;/i&gt; Method of the RDS.DataSpace Object Creates 
an instance of the RDSServer.DataFactory; 
The &lt;i&gt;Query&lt;/i&gt; Method of the RDSServer.DataFactory is used
to bring back a Recordset. &lt;/H4&gt;

&lt;Script Language="VBScript"&gt;

    Dim rdsDF
    Dim strServer
    Dim strCnxn
    Dim strSQL

    strServer = "http://&lt;%=Request.ServerVariables("SERVER_NAME")%&gt;"
    strCnxn = "Provider='sqloledb';Integrated Security='SSPI';Initial Catalog='Northwind';"
    strSQL = "Select FirstName, LastName from Employees"

    Sub Run_OnClick()
    
        ' Create RDSServer.DataFactory Object
        Dim rs
        ' Get Recordset
        Set DF = RDS1.CreateObject("RDSServer.DataFactory", strServer)
        Set rs = DF.Query(strCnxn, strSQL)
        ' Set parameters of RDS.DataControl at Run Time
        RDS.Server = strServer
        RDS.SQL = strSQL
        RDS.Connect = strCnxn
        RDS.Refresh
           
    End Sub
&lt;/Script&gt;


&lt;/BODY&gt;
&lt;/HTML&gt;
&lt;!-- EndDataFactoryVBS --&gt;</code>
  </introduction>
  <relatedTopics>
<link xlink:href="dec96be6-0b31-4953-9c9a-e962b5afcd18">CreateObject Method (RDS)</link>
<link xlink:href="e75240c2-b749-471e-b6ea-98cae232efbe">DataFactory Object (RDSServer)</link>
<link xlink:href="9194bffa-5bdf-4dff-af86-f7158c23bfa7">DataSpace Object (RDS)</link>
<link xlink:href="20f2480f-3758-405d-a379-05a0dce74796">Query Method (RDS)</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>