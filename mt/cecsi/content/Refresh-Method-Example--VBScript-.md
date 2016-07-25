---
title: "Refresh Method Example (VBScript)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - VB
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f2926578-bc60-464b-916e-ddfdb8014253
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
# Refresh Method Example (VBScript)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <alert class="important">
      <para>Beginning with Windows 8 and Windows Server 2012, RDS server components are no longer included in the Windows operating system (see Windows 8 and <externalLink><linkText>Windows Server 2012 Compatibility Cookbook</linkText><linkUri>http://download.microsoft.com/download/2/C/9/2C9C7B01-A1FC-47B6-9166-2151FB6E007C/Windows 8 and Windows Server 2012 Compatibility Cookbook.docx</linkUri></externalLink> for more detail). RDS client components will be removed in a future version of Windows. Avoid using this feature in new development work, and plan to modify applications that currently use this feature. Applications that use RDS should migrate to <externalLink><linkText>WCF Data Service</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=199565</linkUri></externalLink>.</para>
    </alert>
    <para>The following example shows how to set the necessary parameters of <legacyLink xlink:href="d85ea4fc-451c-436e-97b8-58f92b149dd0">RDS.DataControl</legacyLink> at run time. The manner in which a <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink> is retrieved using the <legacyLink xlink:href="089b7ca7-684f-4259-8032-5bd1ecc54426">Refresh</legacyLink> method is determined by the settings of the <legacyLink xlink:href="62a4fd88-afc3-4f1f-b978-40710a30c4e9">ExecuteOptions</legacyLink> and <legacyLink xlink:href="7b2e254a-9354-4541-bc98-bb185276388f">FetchOptions</legacyLink> properties. To test this example, cut and paste the following code into a normal ASP document and name it <legacyBold>RefreshVBS.asp</legacyBold>. Use <legacyBold>Find</legacyBold> to locate the file Adovbs.inc and place it in the directory you plan to use. ASP script will identify your server.</para>
    <code>&lt;!-- BeginRefreshVBS --&gt;
&lt;%@ Language=VBScript %&gt;
&lt;!--use the following META tag instead of adovbs.inc--&gt;
&lt;!--METADATA TYPE="typelib" uuid="00000205-0000-0010-8000-00AA006D2EA4" --&gt;
&lt;html&gt;
&lt;head&gt;
    &lt;meta name="VI60_DefaultClientScript"  content=VBScript&gt;
    &lt;meta name="GENERATOR" content="Microsoft Visual Studio 6.0"&gt;
    &lt;title&gt;Refresh Method Example (VBScript)&lt;/title&gt;
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
&lt;h1&gt;Refresh Method Example (VBScript)&lt;/h1&gt;

&lt;H2&gt;RDS API Code Examples &lt;/H2&gt;
&lt;HR&gt;
&lt;TABLE DATASRC=#RDC&gt;
   &lt;TR&gt;
      &lt;TD&gt; &lt;INPUT DATAFLD="FirstName" SIZE=15&gt; &lt;/TD&gt;
      &lt;TD&gt; &lt;INPUT DATAFLD="LastName" SIZE=15&gt; &lt;/TD&gt;
      &lt;TD&gt; &lt;INPUT DATAFLD="Title" SIZE=15&gt; &lt;/TD&gt;
      &lt;TD&gt; &lt;INPUT DATAFLD="HireDate" SIZE=15&gt; &lt;/TD&gt;
   &lt;/TR&gt;
&lt;/TABLE&gt;

&lt;!-- RDS.DataControl with no parameters set at design time --&gt;
&lt;OBJECT classid="clsid:BD96C556-65A3-11D0-983A-00C04FC29E33"
   ID=RDC HEIGHT=1 WIDTH=1&gt;
&lt;/OBJECT&gt;
&lt;HR&gt;
Server: &lt;Input Size=70 Name="txtServer" Value="http://&lt;%=Request.ServerVariables("SERVER_NAME")%&gt;"&gt;&lt;BR&gt;
Connect: &lt;Input Size=70 Name="txtConnect" Value="Provider='sqloledb';Integrated Security='SSPI';Initial Catalog='Northwind'"&gt;&lt;BR&gt;
SQL: &lt;Input Size=70 Name="txtSQL" Value="Select * from Employees"&gt;
&lt;HR&gt;
&lt;TABLE BORDER=1 WIDTH="60%"&gt;
&lt;TR&gt;
   &lt;TD COLSPAN=3 BGCOLOR=silver&gt;
   Choose if you want the Recordset brought back Synchronously on the 
   current calling thread or Asynchronously on another thread. 
   &lt;/TD&gt;
&lt;/TR&gt;
&lt;TR&gt;
   &lt;TD&gt;Synchronously: &lt;BR&gt;
      &lt;Input Type="Radio" Name="optExecuteOptions" Checked OnClick="SetExO('adcExecSync')"&gt;
   &lt;/TD&gt;
   &lt;TD&gt;Asynchronously: &lt;BR&gt;
      &lt;Input Type="Radio" Name="optExecuteOptions"  OnClick="SetExO('adcExecAsync')"&gt;
   &lt;/TD&gt;
   &lt;TD&gt;&amp;nbsp;&lt;/TD&gt;
&lt;/TR&gt;
&lt;TR&gt;
   &lt;TD COLSPAN=3 BGCOLOR=silver&gt;
   Fetch Up Front, Background Fetch with Blocking or Background Fetch 
   without Blocking 
   &lt;/TD&gt;
&lt;TR&gt;
   &lt;TD&gt;Up Front:&lt;BR&gt;
       &lt;Input Type="Radio" Name="optFetchOptions"  OnClick="SetFO('adcFetchUpFront')"&gt;
   &lt;/TD&gt;
   &lt;TD&gt;Background w/ Blocking:&lt;BR&gt;
       &lt;Input Type="Radio" Name="optFetchOptions" Checked OnClick="SetFO('adcFetchBackground')"&gt;
   &lt;/TD&gt;
   &lt;TD&gt;Background w/o Blocking:&lt;BR&gt;
      &lt;Input Type="Radio" Name="optFetchOptions"  OnClick="SetFO('adcFetchAsync')"&gt;
   &lt;/TD&gt;
&lt;/TR&gt;
&lt;/TABLE&gt;

&lt;INPUT TYPE=BUTTON NAME="Run" VALUE="Run"&gt;&lt;BR&gt;

&lt;Script Language="VBScript"&gt;
&lt;!--
Dim EO         'ExecuteOptions
Dim FO         'FetchOptions
EO = "adcExecSync"   'Default value
FO = "adcFetchBackground"   'Default value

Sub SetExO(NewEO)
   EO = NewEO
End Sub

Sub SetFO(NewFO)
   FO = NewFO
End Sub

' Set parameters of RDS.DataControl at Run Time
Sub Run_OnClick
   RDC.Server = txtServer.Value
   RDC.SQL = txtSQL.Value
   RDC.Connect = txtConnect.Value
   If EO = "adcExecSync" Then   'Determine which ExecuteOption chosen
      RDC.ExecuteOptions = adcExecSync
      MsgBox "Recordset brought in on current calling thread Syncronously"
   Else
      RDC.ExecuteOptions = adcExecAsync
      MsgBox "Recordset brought in on another thread Asyncronously"
   End If

   If FO = "adcFetchBackground" Then      'Determine                 which FetchOption chosen
      RDC.FetchOptions = adcFetchBackground
      MsgBox "Control goes back to user after first batch of records returned"
   ElseIf FO = " adcFetchUpFront" Then
      RDC.FetchOptions = adcFetchUpFront
      MsgBox "All records returned before control goes back to user"
   Else
      RDC.FetchOptions = adcFetchAsync
      MsgBox "Control goes back to user immediately"
   End If

   RDC.Refresh
End Sub
--&gt;
&lt;/Script&gt;

&lt;/body&gt;
&lt;/html&gt;
&lt;!-- EndRefreshVBS --&gt;</code>
  </introduction>
  <relatedTopics>
<link xlink:href="d85ea4fc-451c-436e-97b8-58f92b149dd0">DataControl Object (RDS)</link>
<link xlink:href="62a4fd88-afc3-4f1f-b978-40710a30c4e9">ExecuteOptions Property (RDS)</link>
<link xlink:href="7b2e254a-9354-4541-bc98-bb185276388f">FetchOptions Property (RDS)</link>
<link xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset Object</link>
<link xlink:href="089b7ca7-684f-4259-8032-5bd1ecc54426">Refresh Method</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>