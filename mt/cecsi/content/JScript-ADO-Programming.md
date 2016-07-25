---
title: "JScript ADO Programming"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - JScript
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 62273658-0fe7-4aac-b4d8-f725e6baf043
caps.latest.revision: 9
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
# JScript ADO Programming
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction />
  <section>
    <title>Creating an ADO Project</title>
    <content>
      <para>Microsoft JScript does not support type libraries, so you do not need to reference ADO in your project. Consequently, no associated features such as command line completion are supported. Also, by default, ADO enumerated constants are not defined in JScript.</para>
      <para>However, ADO provides you with two include files containing the following definitions to be used with JScript:  </para>
      <list class="bullet">
        <listItem>
          <para>For server-side scripting use Adojavas.inc, which is installed in the ADO library folders.</para>
        </listItem>
        <listItem>
          <para>For client-side scripting use Adcjavas.inc, which is installed in the ADO library folders.</para>
        </listItem>
      </list>
      <para>You can either copy and paste constant definitions from these files into your ASP pages, or, if you are doing server-side scripting, copy Adojavas.inc file to a folder on your Web site and references it from your ASP page like this:</para>
      <code>&lt;!--#include File="adojavas.inc"--&gt;</code>
    </content>
  </section>
  <section>
    <title>Creating ADO Objects in JScript</title>
    <content>
      <para>You must instead use the <legacyBold>CreateObject</legacyBold> function call:</para>
      <code>var Rs1;
Rs1 = Server.CreateObject("ADODB.Recordset");</code>
    </content>
  </section>
  <section>
    <title>JScript Example</title>
    <content>
      <para>The following code is a generic example of JScript server-side programming in an Active Server Page (ASP) file that opens a <legacyBold>Recordset</legacyBold> object:</para>
      <code>&lt;%  @LANGUAGE="JScript" %&gt;
&lt;!--#include File="adojavas.inc"--&gt;
&lt;HTML&gt;
&lt;BODY BGCOLOR="White" topmargin="10" leftmargin="10"&gt;
&lt;%
var Source = "SELECT * FROM Authors";
var Connect =  "Provider=sqloledb;Data Source=srv;" +
    "Initial Catalog=Pubs;Integrated Security=SSPI;"
var Rs1 = Server.CreateObject( "ADODB.Recordset.2.5" );
Rs1.Open(Source,Connect,adOpenForwardOnly);
Response.Write("Success!");
%&gt;
&lt;/BODY&gt;
&lt;/HTML&gt;</code>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>