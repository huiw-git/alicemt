---
title: "RDS Tutorial (VBScript)"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - VB
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e2a48c4d-88b1-43ff-a202-9cdec54997d2
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
# RDS Tutorial (VBScript)
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This is the RDS Tutorial, written in Microsoft Visual Basic Scripting Edition. For a description of the purpose of this tutorial, see the <legacyLink xlink:href="6e3305a0-7bc7-40d1-9122-235c15d23ab2">RDS Tutorial</legacyLink>.</para>
    <alert class="important">
      <para>Beginning with Windows 8 and Windows Server 2012, RDS server components are no longer included in the Windows operating system (see Windows 8 and <externalLink><linkText>Windows Server 2012 Compatibility Cookbook</linkText><linkUri>http://download.microsoft.com/download/2/C/9/2C9C7B01-A1FC-47B6-9166-2151FB6E007C/Windows 8 and Windows Server 2012 Compatibility Cookbook.docx</linkUri></externalLink> for more detail). RDS client components will be removed in a future version of Windows. Avoid using this feature in new development work, and plan to modify applications that currently use this feature. Applications that use RDS should migrate to <externalLink><linkText>WCF Data Service</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=199565</linkUri></externalLink>.</para>
    </alert>
    <para>In this tutorial, <legacyLink xlink:href="d85ea4fc-451c-436e-97b8-58f92b149dd0">RDS.DataControl</legacyLink> and <legacyLink xlink:href="9194bffa-5bdf-4dff-af86-f7158c23bfa7">RDS.DataSpace</legacyLink> are created at design time — that is, they are defined with object tags, like this: <codeInline>&lt;OBJECT&gt;...&lt;/OBJECT&gt;</codeInline>. Alternatively, they could be created at run time with the <link xlink:href="dec96be6-0b31-4953-9c9a-e962b5afcd18">CreateObject Method (RDS)</link> method. For example, the <unmanagedCodeEntityReference>RDS.DataControl</unmanagedCodeEntityReference> object could be created like this:</para>
    <code>Set DC = <codeFeaturedElement>Server.CreateObject</codeFeaturedElement>("RDS.DataControl")
   &lt;!-- RDS.DataControl --&gt;
   &lt;OBJECT 
      ID="DC1" CLASSID="CLSID:BD96C556-65A3-11D0-983A-00C04FC29E33"&gt;
   &lt;/OBJECT&gt;

   &lt;!-- RDS.DataSpace --&gt;
   &lt;OBJECT 
      ID="DS1" WIDTH=1 HEIGHT=1
      CLASSID="CLSID:BD96C556-65A3-11D0-983A-00C04FC29E36"&gt;
   &lt;/OBJECT&gt;
   
   &lt;SCRIPT LANGUAGE="VBScript"&gt;

   Sub RDSTutorial()
   Dim DF1 </code>
  </introduction>
  <section>
    <title>Step 1 — Specify a server program</title>
    <content>
      <para>VBScript can discover the name of the IIS Web server it is running on by accessing the VBScript <legacyBold>Request.ServerVariables</legacyBold> method available to Active Server Pages:</para>
      <code>"http://&lt;%=Request.ServerVariables("SERVER_NAME")%&gt;"</code>
      <para>However, for this tutorial, use the imaginary server, "yourServer".</para>
      <alert class="note">
        <para>Pay attention to the data type of <legacyBold>ByRef</legacyBold> arguments. VBScript does not let you specify the variable type, so you must always pass a <languageKeyword>Variant</languageKeyword>. When using HTTP, RDS will allow you to pass a Variant to a method that expects a non-Variant if you invoke it with the <legacyBold>RDS.DataSpace</legacyBold> object <legacyLink xlink:href="dec96be6-0b31-4953-9c9a-e962b5afcd18">CreateObject</legacyLink> method. When using DCOM or an in-process server, you must match the parameter types on the client and server sides or you will receive a "Type Mismatch" error.</para>
      </alert>
      <code>Set DF1 = DS1.CreateObject("RDSServer.DataFactory", "http://yourServer")</code>
    </content>
  </section>
  <section>
    <title>Step 2a — Invoke the server program with RDS.DataControl</title>
    <content>
      <para>This example is merely a comment demonstrating that the default behavior of the <legacyBold>RDS.DataControl </legacyBold>is to perform the specified query.</para>
      <code>&lt;OBJECT CLASSID="clsid:BD96C556-65A3-11D0-983A-00C04FC29E33" ID="DC1"&gt;
   &lt;PARAM NAME="SQL" VALUE="SELECT * FROM Authors"&gt;
   &lt;PARAM NAME="Connect" VALUE="DSN=Pubs;"&gt;
   &lt;PARAM NAME="Server" VALUE="http://yourServer/"&gt;
&lt;/OBJECT&gt;
...
&lt;SCRIPT LANGUAGE="VBScript"&gt;

Sub RDSTutorial2A()
   Dim RS
   DC1.Refresh
   Set RS = DC1.Recordset
...</code>
    </content>
  </section>
  <section>
    <title>Step 2b — Invoke the server program with RDSServer.DataFactory</title>
    <content />
  </section>
  <section>
    <title>Step 3 — Server obtains a Recordset</title>
    <content />
  </section>
  <section>
    <title>Step 4 — Server returns the Recordset</title>
    <content>
      <code>Set RS = DF1.Query("DSN=Pubs;", "SELECT * FROM Authors")</code>
    </content>
  </section>
  <section>
    <title>Step 5 — DataControl is made usable by visual controls</title>
    <content>
      <code>' Assign the returned recordset to the DataControl.

DC1.SourceRecordset = RS</code>
    </content>
  </section>
  <section>
    <title>Step 6a — Changes are sent to the server with RDS.DataControl</title>
    <content>
      <para>This example is merely a comment demonstrating how the <legacyBold>RDS.DataControl</legacyBold> performs updates.</para>
      <code>&lt;OBJECT CLASSID="clsid:BD96C556-65A3-11D0-983A-00C04FC29E33" ID="DC1"&gt;
   &lt;PARAM NAME="SQL" VALUE="SELECT * FROM Authors"&gt;
   &lt;PARAM NAME="Connect" VALUE="DSN=Pubs;"&gt;
   &lt;PARAM NAME="Server" VALUE="http://yourServer/"&gt;
&lt;/OBJECT&gt;
...
&lt;SCRIPT LANGUAGE="VBScript"&gt;

Sub RDSTutorial6A()
Dim RS
DC1.Refresh
...
Set RS = DC1.Recordset
' Edit the Recordset object...
' The SERVER and CONNECT properties are already set from Step 2A.
Set DC1.SourceRecordset = RS
...
DC1.SubmitChanges</code>
    </content>
  </section>
  <section>
    <title>Step 6b — Changes are sent to the server with RDSServer.DataFactory</title>
    <content>
      <code>DF.SubmitChanges "DSN=Pubs", RS

End Sub
&lt;/SCRIPT&gt;
&lt;/BODY&gt;
&lt;/HTML&gt;</code>
      <para>         <legacyBold>This is the end of the tutorial.</legacyBold>       </para>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="6e3305a0-7bc7-40d1-9122-235c15d23ab2">RDS Tutorial</link>
<link xlink:href="d0d735e0-669a-41e7-ada2-8dd80924e349">RDS Tutorial (Visual J++)</link>
</relatedTopics>
</developerConceptualDocument>