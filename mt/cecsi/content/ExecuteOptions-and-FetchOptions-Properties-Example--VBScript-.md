---
title: "ExecuteOptions and FetchOptions Properties Example (VBScript)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - VB
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 753a4a3d-0fba-40b8-86e7-50b34182ca69
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
# ExecuteOptions and FetchOptions Properties Example (VBScript)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <alert class="important">
      <para>Beginning with Windows 8 and Windows Server 2012, RDS server components are no longer included in the Windows operating system (see Windows 8 and <externalLink><linkText>Windows Server 2012 Compatibility Cookbook</linkText><linkUri>http://download.microsoft.com/download/2/C/9/2C9C7B01-A1FC-47B6-9166-2151FB6E007C/Windows 8 and Windows Server 2012 Compatibility Cookbook.docx</linkUri></externalLink> for more detail). RDS client components will be removed in a future version of Windows. Avoid using this feature in new development work, and plan to modify applications that currently use this feature. Applications that use RDS should migrate to <externalLink><linkText>WCF Data Service</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=199565</linkUri></externalLink>.</para>
    </alert>
    <para>The following code shows how to set the <legacyLink xlink:href="62a4fd88-afc3-4f1f-b978-40710a30c4e9">ExecuteOptions</legacyLink> and <legacyLink xlink:href="7b2e254a-9354-4541-bc98-bb185276388f">FetchOptions</legacyLink> properties at design time. If left unset, <legacyBold>ExecuteOptions</legacyBold> defaults to <legacyBold>adcExecSync</legacyBold>. This setting indicates that when the <legacyBold>RDS.Refresh</legacyBold> method is called, it will be executed on the current calling thread—that is, synchronously. Cut and paste the following code to Notepad or another text editor and save it as <legacyBold>ExecuteOptionsDesignVBS.asp</legacyBold>.</para>
    <code>&lt;!-- BeginExecuteOptionsDesignVBS --&gt;
&lt;%@ Language=VBScript %&gt;
&lt;html&gt;
&lt;head&gt;
    &lt;meta name="VI60_DefaultClientScript"  content=VBScript&gt;
    &lt;meta name="GENERATOR" content="Microsoft Visual Studio 6.0"&gt;
    &lt;title&gt;Design-time ExecuteOptions and FetchOptions Properties Example&lt;/title&gt;
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
&lt;h2&gt;Design-time &lt;br&gt; ExecuteOptions and FetchOptions Properties Example&lt;/h2&gt;

&lt;OBJECT CLASSID="clsid:BD96C556-65A3-11D0-983A-00C04FC29E33" ID=RDS height=1 width=1&gt;
&lt;PARAM NAME="SQL" VALUE="SELECT FirstName, LastName FROM Employees ORDER BY LastName"&gt;
&lt;PARAM NAME="Connect" VALUE="Provider='sqloledb';Data Source=&lt;%=Request.ServerVariables("SERVER_NAME")%&gt;;Integrated Security='SSPI';Initial Catalog='Northwind'"&gt;
&lt;PARAM NAME="Server" VALUE="http://&lt;%=Request.ServerVariables("SERVER_NAME")%&gt;"&gt;
&lt;PARAM NAME="ExecuteOptions" VALUE="1"&gt;
&lt;PARAM NAME="FetchOptions" VALUE="3"&gt;
&lt;/OBJECT&gt;

&lt;TABLE DATASRC=#RDS&gt;
&lt;TBODY&gt;
   &lt;TR class="thead2"&gt;
      &lt;TH&gt;First Name&lt;/TH&gt;
      &lt;TH&gt;Last Name&lt;/TH&gt;
   &lt;/TR&gt;
   &lt;TR class="tbody"&gt;
     &lt;TD&gt;&lt;SPAN DATAFLD="FirstName"&gt;&lt;/SPAN&gt;&lt;/TD&gt;
     &lt;TD&gt;&lt;SPAN DATAFLD="LastName"&gt;&lt;/SPAN&gt;&lt;/TD&gt;
   &lt;/TR&gt;
&lt;/TBODY&gt;
&lt;/TABLE&gt;

&lt;/body&gt;
&lt;/html&gt;
&lt;!-- EndExecuteOptionsDesignVBS --&gt;</code>
    <para>The following example shows how to set the <legacyBold>ExecuteOptions</legacyBold> and <legacyBold>FetchOptions</legacyBold> properties at run time in VBScript code. See the <legacyLink xlink:href="c90a8050-0ff4-4c83-9925-261f2f2ccfe9">Refresh</legacyLink> method for a working example of these properties. Cut and paste the following code to Notepad or another text editor and save it as <legacyBold>ExecuteOptionsRuntimeVBS.asp</legacyBold>.</para>
    <code>&lt;!-- BeginExecuteOptionsRuntimeVBS --&gt;
&lt;%@ Language=VBScript %&gt;
&lt;html&gt;
&lt;head&gt;
    &lt;meta name="VI60_DefaultClientScript"  content=VBScript&gt;
    &lt;meta name="GENERATOR" content="Microsoft Visual Studio 6.0"&gt;
    &lt;title&gt;Run-time ExecuteOptions and FetchOptions Properties Example&lt;/title&gt;
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
&lt;h2&gt;Run-time &lt;br&gt; ExecuteOptions and FetchOptions Properties Example&lt;/h2&gt;
&lt;OBJECT CLASSID="clsid:BD96C556-65A3-11D0-983A-00C04FC29E33" ID=RDS height=1 width=1&gt;
&lt;PARAM NAME="SQL" VALUE="SELECT FirstName, LastName FROM Employees ORDER BY LastName"&gt;
&lt;PARAM NAME="Connect" VALUE="Provider='sqloledb';Data Source=&lt;%=Request.ServerVariables("SERVER_NAME")%&gt;;Integrated Security='SSPI';Initial Catalog='Northwind'"&gt;
&lt;PARAM NAME="Server" VALUE="http://&lt;%=Request.ServerVariables("SERVER_NAME")%&gt;"&gt;
&lt;/OBJECT&gt;

&lt;TABLE DATASRC=#RDS&gt;
&lt;TBODY&gt;
   &lt;TR class="thead2"&gt;
      &lt;TH&gt;First Name&lt;/TH&gt;
      &lt;TH&gt;Last Name&lt;/TH&gt;
   &lt;/TR&gt;
   &lt;TR class="tbody"&gt;
     &lt;TD&gt;&lt;SPAN DATAFLD="FirstName"&gt;&lt;/SPAN&gt;&lt;/TD&gt;
     &lt;TD&gt;&lt;SPAN DATAFLD="LastName"&gt;&lt;/SPAN&gt;&lt;/TD&gt;
   &lt;/TR&gt;
&lt;/TBODY&gt;
&lt;/TABLE&gt;
&lt;Script Language="VBScript"&gt;
Const adcExecSync = 1
Const adcFetchAsynch = 3

Sub ExecuteHow
  ' set RDS properties at run-time
  RDS1.ExecuteOptions = adcExecSync
  RDS1.FetchOptions = adcFetchAsynch
  RDS.Refresh
End Sub
&lt;/Script&gt;
&lt;/body&gt;
&lt;/html&gt;
&lt;!-- EndExecuteOptionsRuntimeVBS --&gt;</code>
  </introduction>
  <relatedTopics>
<link xlink:href="62a4fd88-afc3-4f1f-b978-40710a30c4e9">ExecuteOptions Property (RDS)</link>
<link xlink:href="7b2e254a-9354-4541-bc98-bb185276388f">FetchOptions Property (RDS)</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>