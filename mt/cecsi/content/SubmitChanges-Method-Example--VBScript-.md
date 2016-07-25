---
title: "SubmitChanges Method Example (VBScript)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - VB
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 619bc7fd-ad0a-44ea-9678-ad40a662c258
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
# SubmitChanges Method Example (VBScript)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <alert class="important">
      <para>Beginning with Windows 8 and Windows Server 2012, RDS server components are no longer included in the Windows operating system (see Windows 8 and <externalLink><linkText>Windows Server 2012 Compatibility Cookbook</linkText><linkUri>http://download.microsoft.com/download/2/C/9/2C9C7B01-A1FC-47B6-9166-2151FB6E007C/Windows 8 and Windows Server 2012 Compatibility Cookbook.docx</linkUri></externalLink> for more detail). RDS client components will be removed in a future version of Windows. Avoid using this feature in new development work, and plan to modify applications that currently use this feature. Applications that use RDS should migrate to <externalLink><linkText>WCF Data Service</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=199565</linkUri></externalLink>.</para>
    </alert>
    <para>The following code fragment shows how to use the <legacyLink xlink:href="250062a4-13c4-4bed-807d-8b9ad81536d4">SubmitChanges</legacyLink> method with an <legacyLink xlink:href="d85ea4fc-451c-436e-97b8-58f92b149dd0">RDS.DataControl</legacyLink> object.</para>
    <para>To test this example, cut and paste this code into a normal ASP document and name it <legacyBold>SubmitChangesCtrlVBS.asp</legacyBold>. ASP script will identify your server.</para>
    <code>&lt;!-- BeginCancelUpdateVBS --&gt;
&lt;%@Language=VBScript%&gt;

&lt;%'Option Explicit%&gt;
&lt;% 'use the following META tag instead of adovbs.inc%&gt;
&lt;!--METADATA TYPE="typelib" uuid="00000205-0000-0010-8000-00AA006D2EA4" --&gt;
&lt;HTML&gt;
&lt;HEAD&gt;
&lt;META NAME="GENERATOR" Content="Microsoft Visual Studio 6.0"&gt;
&lt;TITLE&gt;&lt;/TITLE&gt;
&lt;/HEAD&gt;
&lt;BODY&gt;
&lt;CENTER&gt;
&lt;H1&gt;Remote Data Service&lt;/H1&gt;
&lt;H2&gt;SubmitChanges and CancelUpdate Methods&lt;/H2&gt;

&lt;%  ' to integrate/test this code replace the Server property value and 
    ' the Data Source value in the Connect property with identical values%&gt;

&lt;HR&gt;
&lt;OBJECT id="RDS" classid="clsid:BD96C556-65A3-11D0-983A-00C04FC29E33" HEIGHT="1" WIDTH="1"&gt;&lt;/OBJECT&gt;
&lt;SCRIPT Language="VBScript"&gt;

     'set RDS properties for control just created
    RDS.Server = "http://&lt;%=Request.ServerVariables("SERVER_NAME")%&gt;"
    RDS.Connect = "Provider='sqloledb';Integrated Security='SSPI';Initial Catalog='Northwind';"
    RDS.SQL = "Select * from Employees"
    RDS.Refresh
&lt;/SCRIPT&gt;

&lt;TABLE DATASRC="#RDS"&gt;
&lt;THEAD&gt;
&lt;TR ID="ColHeaders"&gt;
   &lt;TH&gt;ID&lt;/TH&gt;
   &lt;TH&gt;FName&lt;/TH&gt;
   &lt;TH&gt;LName&lt;/TH&gt;
   &lt;TH&gt;Title&lt;/TH&gt;
   &lt;TH&gt;Hire Date&lt;/TH&gt;
   &lt;TH&gt;Birth Date&lt;/TH&gt;
   &lt;TH&gt;Extension&lt;/TH&gt;
   &lt;TH&gt;Home Phone&lt;/TH&gt;
&lt;/TR&gt;
&lt;/THEAD&gt;
&lt;TBODY&gt;
&lt;TR&gt;
   &lt;TD&gt; &lt;INPUT DATAFLD="EmployeeID" size=4 id=text1 name=text1&gt; &lt;/TD&gt;
   &lt;TD&gt; &lt;INPUT DATAFLD="FirstName" size=10 id=text2 name=text2&gt; &lt;/TD&gt;
   &lt;TD&gt; &lt;INPUT DATAFLD="LastName" size=10 id=text3 name=text3&gt; &lt;/TD&gt;
   &lt;TD&gt; &lt;INPUT DATAFLD="Title" size=10 id=text4 name=text4&gt; &lt;/TD&gt;
   &lt;TD&gt; &lt;INPUT DATAFLD="HireDate" size=10 id=text5 name=text5&gt; &lt;/TD&gt;
   &lt;TD&gt; &lt;INPUT DATAFLD="BirthDate" size=10 id=text6 name=text6&gt; &lt;/TD&gt;
   &lt;TD&gt; &lt;INPUT DATAFLD="Extension" size=10 id=text7 name=text7&gt; &lt;/TD&gt;
   &lt;TD&gt; &lt;INPUT DATAFLD="HomePhone" size=8 id=text8 name=text8&gt; &lt;/TD&gt;
&lt;/TR&gt;
&lt;/TBODY&gt;
&lt;/TABLE&gt;
&lt;HR&gt;
&lt;INPUT TYPE=button NAME="SubmitChange" VALUE="Submit Changes"&gt;
&lt;INPUT TYPE=button NAME="CancelChange" VALUE="Cancel Update"&gt;
&lt;BR&gt;
&lt;H4&gt;Alter a current entry on the grid. Move off that Row. &lt;BR&gt;
Submit the Changes to your DBMS or cancel the updates. &lt;/H4&gt;
&lt;/CENTER&gt;
&lt;SCRIPT Language="VBScript"&gt;

Sub SubmitChange_OnClick
    
    msgbox "Changes will be made"
    RDS.SubmitChanges   
    RDS.Refresh

End Sub

Sub CancelChange_OnClick

    msgbox "Changes will be cancelled"
    RDS.CancelUpdate
    RDS.Refresh

End Sub
&lt;/SCRIPT&gt;


&lt;/BODY&gt;
&lt;/HTML&gt;
&lt;!-- EndCancelUpdateVBS --&gt;</code>
  </introduction>
  <relatedTopics>
<link xlink:href="d85ea4fc-451c-436e-97b8-58f92b149dd0">DataControl Object (RDS)</link>
<link xlink:href="250062a4-13c4-4bed-807d-8b9ad81536d4">SubmitChanges Method (RDS)</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>