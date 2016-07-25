---
title: "DataSpace Object and CreateObject Method Example (VBScript)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - VB
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 12b0e160-5e5c-441f-bed7-ac0bd061e003
caps.latest.revision: 14
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
# DataSpace Object and CreateObject Method Example (VBScript)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <alert class="important">
      <para>Beginning with Windows 8 and Windows Server 2012, RDS server components are no longer included in the Windows operating system (see Windows 8 and <externalLink><linkText>Windows Server 2012 Compatibility Cookbook</linkText><linkUri>http://download.microsoft.com/download/2/C/9/2C9C7B01-A1FC-47B6-9166-2151FB6E007C/Windows 8 and Windows Server 2012 Compatibility Cookbook.docx</linkUri></externalLink> for more detail). RDS client components will be removed in a future version of Windows. Avoid using this feature in new development work, and plan to modify applications that currently use this feature. Applications that use RDS should migrate to <externalLink><linkText>WCF Data Service</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=199565</linkUri></externalLink>.</para>
    </alert>
    <para>The following example shows how to use the <legacyLink xlink:href="dec96be6-0b31-4953-9c9a-e962b5afcd18">CreateObject</legacyLink> method of the <legacyLink xlink:href="9194bffa-5bdf-4dff-af86-f7158c23bfa7">RDS.DataSpace</legacyLink> with the default business object, <legacyLink xlink:href="e75240c2-b749-471e-b6ea-98cae232efbe">RDSServer.DataFactory</legacyLink>. To test this example, cut and paste this code between the &lt;Body&gt; and &lt;/Body&gt; tags in a normal HTML document and name it <legacyBold>DataSpaceVBS.asp</legacyBold>. ASP script will identify your server.</para>
    <code>&lt;!-- BeginDataSpaceVBS --&gt;
&lt;html&gt;
&lt;head&gt;
&lt;!--use the following META tag instead of adovbs.inc--&gt;
&lt;!--METADATA TYPE="typelib" uuid="00000205-0000-0010-8000-00AA006D2EA4" --&gt;
    &lt;meta name="VI60_DefaultClientScript"  content=VBScript&gt;
    &lt;meta name="GENERATOR" content="Microsoft Visual Studio 6.0"&gt;
    &lt;title&gt;DataSpace Object and CreateObject Method Example (VBScript)&lt;/title&gt;
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
&lt;h1&gt;DataSpace Object and CreateObject Method Example (VBScript)&lt;/h1&gt;

&lt;H2&gt;RDS API Code Examples&lt;/H2&gt;
&lt;HR&gt;
&lt;H3&gt;Using Query Method of RDSServer.DataFactory&lt;/H3&gt;

&lt;!-- RDS.DataSpace  ID rdsDS--&gt;
&lt;OBJECT ID="rdsDS" WIDTH=1 HEIGHT=1
CLASSID="CLSID:BD96C556-65A3-11D0-983A-00C04FC29E36"&gt;
&lt;/OBJECT&gt;

&lt;!-- RDS.DataControl with parameters set at run time --&gt;
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

&lt;H4&gt;Click Run -
The &lt;i&gt;CreateObject&lt;/i&gt; Method of the RDS.DataSpace Object Creates an instance of the RDSServer.DataFactory.
The &lt;i&gt;Query&lt;/i&gt; Method of the RDSServer.DataFactory is used to bring back a Recordset.&lt;/H4&gt;

&lt;Script Language="VBScript"&gt;

    Dim rdsDF
    Dim strServer
    Dim strCnxn
    Dim strSQL

    strServer = "http://&lt;%=Request.ServerVariables("SERVER_NAME")%&gt;"
    strCnxn = "Provider='sqloledb';Data Source=" &amp; _
            "&lt;%=Request.ServerVariables("SERVER_NAME")%&gt;" &amp; ";" &amp; _
            "Integrated Security='SSPI';Initial Catalog='Northwind';"
    strSQL = "Select FirstName, LastName from Employees"

    Sub Run_OnClick()
              
       Dim rs      
        ' Create Data Factory
       Set rdsDF = rdsDS.CreateObject("RDSServer.DataFactory", strServer)
        'Get Recordset  
       Set rs = rdsDF.Query(strCnxn, strSQL)   
       ' Use  RDS.DataControl to bind Recordset to data-aware Table above
       RDS.SourceRecordset = rs

    End Sub
&lt;/Script&gt;

&lt;/body&gt;
&lt;/html&gt;
&lt;!-- EndDataSpaceVBS --&gt;</code>
    <para>The following example shows how to use the <legacyBold>CreateObject</legacyBold> method to create an instance of a custom business object, VbBusObj.VbBusObjCls. It also uses the Active Server Pages scripting to identify the Web server name.</para>
    <para>To see the complete example, open the sample applications selector. In the <legacyBold>Client Tier</legacyBold> column, select <legacyBold>VBScript in Internet Explorer</legacyBold>. In the <legacyBold>Middle Tier</legacyBold> column, select <legacyBold>Custom Visual Basic Business Object</legacyBold>.</para>
    <alert class="note">
      <para>If you are connecting to a data source provider that supports Windows authentication, you should specify <system>Trusted_Connection=yes</system> or <system>Integrated Security = SSPI</system> instead of user ID and password information in the connection string.</para>
    </alert>
    <code>Sub Window_OnLoad()
   strServer = "http://&lt;%=Request.ServerVariables("SERVER_NAME")%&gt;"
   Set BO = ADS1.CreateObject("VbBusObj.VbBusObjCls", strServer)
   txtConnect.Value = "dsn=Pubs;uid=MyUserID;pwd=MyPassword;"
   txtGetRecordset.Value = "Select * From authors for Browse"
End Sub</code>
  </introduction>
  <relatedTopics>
<link xlink:href="dec96be6-0b31-4953-9c9a-e962b5afcd18">CreateObject Method (RDS)</link>
<link xlink:href="9194bffa-5bdf-4dff-af86-f7158c23bfa7">DataSpace Object (RDS)</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>