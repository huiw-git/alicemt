---
title: "Cancel Method Example (VBScript)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - VB
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4ade106d-063d-486e-bc4d-a1a6b6e0bea9
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
# Cancel Method Example (VBScript)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <alert class="important">
      <para>Beginning with Windows 8 and Windows Server 2012, RDS server components are no longer included in the Windows operating system (see Windows 8 and <externalLink><linkText>Windows Server 2012 Compatibility Cookbook</linkText><linkUri>http://download.microsoft.com/download/2/C/9/2C9C7B01-A1FC-47B6-9166-2151FB6E007C/Windows 8 and Windows Server 2012 Compatibility Cookbook.docx</linkUri></externalLink> for more detail). RDS client components will be removed in a future version of Windows. Avoid using this feature in new development work, and plan to modify applications that currently use this feature. Applications that use RDS should migrate to <externalLink><linkText>WCF Data Service</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=199565</linkUri></externalLink>.</para>
    </alert>
    <para>The following example shows how to read the <legacyLink xlink:href="e0db4e15-6787-41e2-8f13-9e9b524d620a">Cancel</legacyLink> method at run time. Cut and paste the following code to Notepad or another text editor and save it as CancelVBS.asp. You can view the result in any client browser.</para>
    <code>&lt;!-- BeginCancelVBS --&gt;
&lt;Script Language="VBScript"&gt;
&lt;!--
Sub cmdCancelAsync_OnClick
   ' Terminates currently running AsyncExecute,
   ' ReadyState property set to adcReadyStateLoaded,
   ' Recordset set to Nothing
  ADC.Cancel
End Sub

Sub cmdRefreshTable_OnClick
   ADC.Refresh
End Sub
--&gt;
&lt;/Script&gt;

&lt;OBJECT CLASSID="clsid:BD96C556-65A3-11D0-983A-00C04FC29E33" ID="ADC"&gt;
.
   &lt;PARAM NAME="SQL" VALUE="Select FirstName, LastName from Employees"&gt;
   &lt;PARAM NAME="CONNECT" VALUE="Provider='sqloledb';Integrated Security='SSPI';Initial Catalog='Northwind'"&gt;
   &lt;PARAM NAME="Server" VALUE="http://&lt;%=Request.ServerVariables("SERVER_NAME")%&gt;"&gt;
.
&lt;/OBJECT&gt;

&lt;TABLE DATASRC=#ADC&gt;
&lt;TBODY&gt;
  &lt;TR&gt;
    &lt;TD&gt;&lt;SPAN DATAFLD="FirstName"&gt;&lt;/SPAN&gt;&lt;/TD&gt;
    &lt;TD&gt;&lt;SPAN DATAFLD="LastName"&gt;&lt;/SPAN&gt;&lt;/TD&gt;
  &lt;/TR&gt;
&lt;/TBODY&gt;
&lt;/TABLE&gt;

&lt;FORM&gt;
&lt;INPUT type="button" value="Refresh" id=cmdRefreshTable name=cmdRefreshTable&gt;
&lt;INPUT type="button" value="Cancel" id=cmdCancelAsync name=cmdCancelAsync&gt;
&lt;/FORM&gt;
&lt;!-- EndCancelVBS --&gt;</code>
  </introduction>
  <relatedTopics>
<link xlink:href="e0db4e15-6787-41e2-8f13-9e9b524d620a">Cancel Method</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>