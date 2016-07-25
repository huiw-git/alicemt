---
title: "VBScript ADO Programming"
ms.custom: na
ms.date: 07/11/2016
ms.devlang: 
  - VB
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6aaaf6d0-1376-4473-bea6-b81f2645a9ac
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
# VBScript ADO Programming
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction />
  <section>
    <title>Creating an ADO Project</title>
    <content>
      <para>Microsoft Visual Basic, Scripting Edition does not support type libraries, so you do not need to reference ADO in your project. Consequently, no associated features such as command line completion are supported. Also, by default, ADO enumerated constants are not defined in VBScript.</para>
      <para>However, ADO provides you with two include files containing the following definitions to be used with VBScript:  </para>
      <list class="bullet">
        <listItem>
          <para>For server-side scripting use Adovbs.inc, which is installed in the c:\Program Files\Common Files\System\ado\ folder by default.</para>
        </listItem>
        <listItem>
          <para>For client-side scripting use Adcvbs.inc, which is installed in the c:\Program Files\Common Files\System\msdac\ folder by default.</para>
        </listItem>
      </list>
      <para>You can either copy and paste constant definitions from these files into your ASP pages, or, if you are doing server-side scripting, copy Adovbs.inc file to a folder on your Web site and referencing it from your ASP page like this:</para>
      <code>&lt;!--#include File="adovbs.inc"--&gt;</code>
    </content>
  </section>
  <section>
    <title>Creating ADO Objects in VBScript</title>
    <content>
      <para>You cannot use the <legacyBold>Dim</legacyBold> statement to assign objects to a specific type in VBScript. Also, VBScript does not support the <legacyBold>New</legacyBold> syntax used with the <legacyBold>Dim</legacyBold> statement in Visual Basic for Applications. You must instead use the <legacyBold>CreateObject</legacyBold> function call:</para>
      <code>Dim Rs1
Set Rs1 = Server.CreateObject( "ADODB.Recordset" )</code>
    </content>
  </section>
  <section>
    <title>VBScript Examples</title>
    <content>
      <para>The following code is a generic example of VBScript server-side programming in an Active Server Page (ASP) file:</para>
      <code>&lt;%  @LANGUAGE="VBSCRIPT" %&gt;
&lt;%  Option Explicit %&gt;
&lt;!--#include File="adovbs.inc"--&gt;
&lt;HTML&gt;
    &lt;BODY BGCOLOR="White" topmargin="10" leftmargin="10"&gt;

    &lt;!-- Your ASP Code goes here --&gt;
&lt;%
Dim Source
Dim Connect
Dim Rs1
    
Source = "SELECT * FROM Authors"
Connect = "Provider=sqloledb;Data Source=srv;" &amp; _
    "Initial Catalog=Pubs;Integrated Security=SSPI;"

Set Rs1 = Server.CreateObject( "ADODB.Recordset" )
Rs1.Open Source, Connect, adOpenForwardOnly
Response.Write("Success!")
%&gt;
    &lt;/BODY&gt;
&lt;/HTML&gt;</code>
      <para>More specific VBScript examples are included with the ADO documentation. For more information, see <legacyLink xlink:href="78bb9a95-7ac4-44b6-818b-d1787f952ed7">ADO Code Examples in Microsoft Visual Basic Scripting Edition</legacyLink>.</para>
    </content>
  </section>
  <section>
    <title>Differences Between VBScript and Visual Basic</title>
    <content>
      <para>Using ADO with VBScript is similar to using ADO with Visual Basic in many ways, including how syntax is used. However, some significant differences exist:  </para>
      <list class="bullet">
        <listItem>
          <para>VBScript supports only the Variant data type, which can hold different types of data. You can store the data you need in a Variant data type, and the data will function appropriately due to casting performed by VBScript. It recognizes the type required by ADO, and converts the value in the Variant accordingly.</para>
        </listItem>
        <listItem>
          <para>You cannot use <legacyBold>on error goto &lt;label&gt;</legacyBold> within VBScript.</para>
        </listItem>
        <listItem>
          <para>VBScript supports some of the built-in Visual Basic functions such as <legacyBold>Msgbox</legacyBold>, <legacyBold>Date</legacyBold>, and <legacyBold>IsNumeric</legacyBold>. However, because VBScript is a subset of Visual Basic, not all built-in functions are supported. For example, VBScript does not support the <legacyBold>Format</legacyBold> function and the file I/O functions.</para>
        </listItem>
      </list>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>