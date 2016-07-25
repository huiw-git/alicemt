---
title: "Connect Property Example (VBScript)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - VB
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 06297993-fe72-4446-aa76-3b8bc25444f6
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
# Connect Property Example (VBScript)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <alert class="important">
      <para>Beginning with Windows 8 and Windows Server 2012, RDS server components are no longer included in the Windows operating system (see Windows 8 and <externalLink><linkText>Windows Server 2012 Compatibility Cookbook</linkText><linkUri>http://download.microsoft.com/download/2/C/9/2C9C7B01-A1FC-47B6-9166-2151FB6E007C/Windows 8 and Windows Server 2012 Compatibility Cookbook.docx</linkUri></externalLink> for more detail). RDS client components will be removed in a future version of Windows. Avoid using this feature in new development work, and plan to modify applications that currently use this feature. Applications that use RDS should migrate to <externalLink><linkText>WCF Data Service</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=199565</linkUri></externalLink>.</para>
    </alert>
    <para>This code shows how to set the <legacyLink xlink:href="dbad5e77-b213-4eb8-aecf-d60f203fdb59">Connect</legacyLink> property at design time:</para>
    <code>&lt;OBJECT CLASSID="clsid:BD96C556-65A3-11D0-983A-00C04FC29E33" ID="ADC1"&gt;
.
   &lt;PARAM NAME="SQL" VALUE="Select * from Sales"&gt;
   &lt;PARAM NAME="CONNECT" VALUE="Provider=SQLOLEDB;Integrated Security=SSPI;Initial Catalog=Pubs"&gt;
   &lt;PARAM NAME="Server" VALUE="http://MyWebServer"&gt;
.
&lt;/OBJECT&gt;</code>
    <para>The following example shows how to set the <legacyBold>Connect</legacyBold> property at run time in VBScript code.</para>
    <para>To test this example, cut and paste the code between the &lt;Body&gt; and &lt;/Body&gt; tags in a normal HTML document and name it <legacyBold>ConnectVBS.asp</legacyBold>. ASP script will identify your server.</para>
    <code>&lt;!-- BeginConnectVBS --&gt;
&lt;%@ Language=VBScript %&gt;
&lt;HTML&gt;
&lt;HEAD&gt;
&lt;title&gt;ADO Connect Property&lt;/title&gt;
    
    &lt;%' local style sheet used for display%&gt;
&lt;STYLE&gt;
&lt;!--
BODY {
   font-family: 'Verdana','Arial','Helvetica',sans-serif;
   BACKGROUND-COLOR:white;
   COLOR:black;
    }

.tbody { 
   text-align: center;
   background-color: #f7efde;
   font-family: 'Verdana','Arial','Helvetica',sans-serif; 
   font-size: x-small;
    }
--&gt;
&lt;/STYLE&gt;
&lt;/HEAD&gt;

&lt;BODY&gt;
&lt;h1&gt;ADO Connect Property (RDS)&lt;/h1&gt;

&lt;HR&gt;
&lt;H3&gt;Set Connect Property at Run Time&lt;/H3&gt;

&lt;% ' RDS.DataControl with no parameters set at design time %&gt;
&lt;OBJECT classid="clsid:BD96C556-65A3-11D0-983A-00C04FC29E33" ID=RDS HEIGHT=1 WIDTH=1&gt;&lt;/OBJECT&gt;
&lt;% ' Bind table to control for data display  %&gt;
&lt;TABLE DATASRC=#RDS&gt;
&lt;TBODY&gt;
  &lt;TR class="tbody"&gt;
    &lt;TD&gt;&lt;SPAN DATAFLD="FirstName"&gt;&lt;/SPAN&gt;&lt;/TD&gt;
    &lt;TD&gt;&lt;SPAN DATAFLD="LastName"&gt;&lt;/SPAN&gt;&lt;/TD&gt;
  &lt;/TR&gt;
&lt;/TBODY&gt;
&lt;/TABLE&gt;
&lt;FORM name="frmInput"&gt;
    SERVER: &lt;INPUT Name="txtServer" Size="103" Value="http://&lt;%=Request.ServerVariables("SERVER_NAME")%&gt;"&gt;&lt;BR&gt;
    DATA SOURCE: &lt;INPUT Name="txtDataSource" Size="93" Value="&lt;%=Request.ServerVariables("SERVER_NAME")%&gt;"&gt;&lt;BR&gt;
    CONNECT: &lt;INPUT Name="txtConnect" Size="100"&gt;&lt;BR&gt;
    SQL: &lt;INPUT Name="txtSQL" Size="110" Value="Select FirstName, LastName from Employees"&gt;
    &lt;BR&gt;
    &lt;INPUT TYPE=BUTTON NAME="Run" VALUE="Run"&gt;
    &lt;h4&gt;
    To make data grid appear, click 'Run' to see the connect string in text box above.
    &lt;/h4&gt; 
&lt;/FORM&gt;
&lt;Script Language="VBScript"&gt;

    ' Set parameters of RDS.DataControl at Run Time
    Sub Run_OnClick

        Dim Cnxn
            ' build connection string
        Cnxn = "Provider='sqloledb';"
        Cnxn = Cnxn &amp; "Data Source="
        Cnxn = Cnxn &amp; document.frmInput.txtDataSource.value &amp; ";"
        Cnxn = Cnxn &amp; "Initial Catalog='Northwind';"
        Cnxn = Cnxn &amp; "Integrated Security='SSPI';"
            ' assign the value
        document.frmInput.txtConnect.value = Cnxn
        MsgBox "Here we go!"
            ' set RDS properties
        RDS.Server = document.frmInput.txtServer.value
        RDS.SQL = document.frmInput.txtSQL.value
        RDS.Connect = document.frmInput.txtConnect.value
        RDS.Refresh

    End Sub

&lt;/Script&gt;

&lt;/BODY&gt;
&lt;/HTML&gt;
&lt;!-- EndConnectVBS --&gt;</code>
  </introduction>
  <relatedTopics>
<link xlink:href="dbad5e77-b213-4eb8-aecf-d60f203fdb59">Connect Property (RDS)</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>