---
title: "Server Property Example (VBScript)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - VB
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0fe57af9-a4d0-4986-a2e3-beaa4d26ed58
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
# Server Property Example (VBScript)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <alert class="important">
      <para>Beginning with Windows 8 and Windows Server 2012, RDS server components are no longer included in the Windows operating system (see Windows 8 and <externalLink><linkText>Windows Server 2012 Compatibility Cookbook</linkText><linkUri>http://download.microsoft.com/download/2/C/9/2C9C7B01-A1FC-47B6-9166-2151FB6E007C/Windows 8 and Windows Server 2012 Compatibility Cookbook.docx</linkUri></externalLink> for more detail). RDS client components will be removed in a future version of Windows. Avoid using this feature in new development work, and plan to modify applications that currently use this feature. Applications that use RDS should migrate to <externalLink><linkText>WCF Data Service</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=199565</linkUri></externalLink>.</para>
    </alert>
    <para>The following code shows how to set the <legacyLink xlink:href="d85ea4fc-451c-436e-97b8-58f92b149dd0">RDS.DataControl</legacyLink> parameter at design time and bind it to a data-aware control using the SQLOLEDB provider. Cut and paste this code into a normal ASP document and name it <legacyBold>ServerDesignVBS.asp</legacyBold>. ASP script will identify your server.</para>
    <code>&lt;!-- BeginServerDesignVBS --&gt;
&lt;%@ Language=VBScript %&gt;
&lt;html&gt;
&lt;head&gt;
    &lt;meta name="VI60_DefaultClientScript"  content=VBScript&gt;
    &lt;meta name="GENERATOR" content="Microsoft Visual Studio 6.0"&gt;
    &lt;title&gt;Server Property Example (VBScript)&lt;/title&gt;
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
&lt;h1&gt;Server Property Example (VBScript)&lt;/h1&gt;

&lt;TABLE DATASRC=#RDS&gt;
   &lt;TR&gt;
      &lt;TD&gt; &lt;SPAN DATAFLD="FirstName"&gt;&lt;/SPAN&gt; &lt;/TD&gt;
      &lt;TD&gt; &lt;SPAN DATAFLD="LastName"&gt;&lt;/SPAN&gt; &lt;/TD&gt;
      &lt;TD&gt; &lt;SPAN DATAFLD="Title"&gt;&lt;/SPAN&gt; &lt;/TD&gt;
      &lt;TD&gt; &lt;SPAN DATAFLD="Type"&gt;&lt;/SPAN&gt; &lt;/TD&gt;
      &lt;TD&gt; &lt;SPAN DATAFLD="Email"&gt;&lt;/SPAN&gt; &lt;/TD&gt;
   &lt;/TR&gt;
&lt;/TABLE&gt;
&lt;!-- Remote Data Service with Parameters set at Design Time --&gt;
&lt;OBJECT classid="clsid:BD96C556-65A3-11D0-983A-00C04FC29E33"
   ID=RDS HEIGHT=1 WIDTH=1&gt;
   &lt;PARAM NAME="SQL" VALUE="Select * from Employees"&gt;
   &lt;PARAM NAME="SERVER" VALUE="http://&lt;%=Request.ServerVariables("SERVER_NAME")%&gt;"&gt;
   &lt;PARAM NAME="CONNECT" VALUE="Provider='sqloledb';Integrated Security='SSPI';Initial Catalog='Northwind'"&gt;
&lt;/OBJECT&gt;

&lt;/body&gt;
&lt;/html&gt;
&lt;!-- EndServerDesignVBS --&gt;</code>
    <para>The following example shows how to set the necessary parameters of <legacyBold>RDS.DataControl</legacyBold> at run time. To test this example, cut and paste this code into a normal ASP document and name it <legacyBold>ServerRuntimeVBS.asp</legacyBold>. ASP script will identify your server.</para>
    <code>&lt;!-- BeginServerRuntimeVBS --&gt;
&lt;%@ Language=VBScript %&gt;
&lt;html&gt;
&lt;head&gt;
    &lt;meta name="VI60_DefaultClientScript"  content=VBScript&gt;
    &lt;meta name="GENERATOR" content="Microsoft Visual Studio 6.0"&gt;
    &lt;title&gt;Server Property Example (VBScript)&lt;/title&gt;
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
&lt;h1&gt;Server Property Example (VBScript)&lt;/h1&gt;

&lt;H2&gt;RDS API Code Examples&lt;/H2&gt;

&lt;H3&gt;Remote Data Service Server Property Set at Run Time&lt;/H3&gt;

&lt;!-- RDS.DataControl with no parameters set at design time --&gt;
&lt;OBJECT classid="clsid:BD96C556-65A3-11D0-983A-00C04FC29E33"
   ID=RDC HEIGHT=1 WIDTH=1&gt;
&lt;/OBJECT&gt;

&lt;TABLE DATASRC=#RDC&gt;
   &lt;TR&gt;
      &lt;TD&gt; &lt;SPAN DATAFLD="FirstName"&gt;&lt;/SPAN&gt; &lt;/TD&gt;
      &lt;TD&gt; &lt;SPAN DATAFLD="LastName"&gt;&lt;/SPAN&gt; &lt;/TD&gt;
      &lt;TD&gt; &lt;SPAN DATAFLD="Title"&gt;&lt;/SPAN&gt; &lt;/TD&gt;
      &lt;TD&gt; &lt;SPAN DATAFLD="Type"&gt;&lt;/SPAN&gt; &lt;/TD&gt;
      &lt;TD&gt; &lt;SPAN DATAFLD="Email"&gt;&lt;/SPAN&gt; &lt;/TD&gt;
   &lt;/TR&gt;
&lt;/TABLE&gt;

&lt;HR&gt;
&lt;Input Size=70 Name="txtServer" Value="HTTP://&lt;%= Request.ServerVariables("SERVER_NAME")%&gt;"&gt;
&lt;BR&gt;
&lt;Input Size=70 Name="txtConnect" Value="Provider='sqloledb';Integrated Security='SSPI';Initial Catalog='Northwind'"&gt;
&lt;BR&gt;
&lt;Input Size=70 Name="txtSQL" Value="Select * from Employees"&gt;
&lt;HR&gt;
&lt;INPUT TYPE=BUTTON NAME="Run" VALUE="Run"&gt;&lt;BR&gt;

&lt;Script Language="VBScript"&gt;
&lt;!--
' Set parameters of RDS.DataControl at Run Time
Sub Run_OnClick
   RDC.Server = txtServer.Value
   RDC.SQL = txtSQL.Value
   RDC.Connect = txtConnect.Value
   RDC.Refresh
End Sub
--&gt;
&lt;/Script&gt;

&lt;/body&gt;
&lt;/html&gt;
&lt;!-- EndServerRuntimeVBS --&gt;</code>
  </introduction>
  <relatedTopics>
<link xlink:href="d85ea4fc-451c-436e-97b8-58f92b149dd0">DataControl Object (RDS)</link>
<link xlink:href="d2727ce7-da9f-4271-ae3c-9334ef477c14">Server Property (RDS)</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>