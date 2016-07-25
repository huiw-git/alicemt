---
title: "Streams and Persistence"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ad5bf52c-fd10-4cfa-bf7d-fcedcaa41eea
caps.latest.revision: 8
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
# Streams and Persistence
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink> object <legacyLink xlink:href="ed3d9678-5c28-4e61-8bb3-7dfb66d99cf5">Save</legacyLink> method stores, or <legacyItalic>persists</legacyItalic>, a <legacyBold>Recordset</legacyBold> in a file, and the <legacyLink xlink:href="3236749c-4b71-4235-89e2-ccdfaaa9319d">Open</legacyLink> method restores the <legacyBold>Recordset</legacyBold> from that file.</para>
    <para>With ADO 2.7 or later, the <legacyBold>Save</legacyBold> and <legacyBold>Open</legacyBold> methods can persist a <legacyBold>Recordset</legacyBold> to a <legacyLink xlink:href="0514531f-009d-4519-abc3-d727014a39f1">Stream</legacyLink> object as well. This feature is especially useful when working with Remote Data Service (RDS) and Active Server Pages (ASP).</para>
    <para>For more information about how persistence can be used by itself on ASP pages, see the current ASP documentation.</para>
    <para>The following are a few scenarios that show how <legacyBold>Stream</legacyBold> objects and persistence can be used.</para>
  </introduction>
  <section>
    <title>Scenario 1</title>
    <content>
      <para>This scenario simply saves a <legacyBold>Recordset</legacyBold> to a file and then to a <legacyBold>Stream</legacyBold>. It then opens the persisted stream into another <legacyBold>Recordset</legacyBold>.</para>
      <code>Dim rs1 As ADODB.Recordset
Dim rs2 As ADODB.Recordset
Dim stm As ADODB.Stream

Set rs1 = New ADODB.Recordset
Set rs2 = New ADODB.Recordset
Set stm = New ADODB.Stream

rs1.<codeFeaturedElement>Open</codeFeaturedElement>   "SELECT * FROM Customers", "Provider=sqloledb;" &amp; _
        "Data Source=MyServer;Initial Catalog=Northwind;" &amp; _
        "Integrated Security=SSPI;""", adopenStatic, adLockReadOnly, adCmdText
rs1.<codeFeaturedElement>Save</codeFeaturedElement> "c:\myfolder\mysubfolder\myrs.xml", <codeFeaturedElement>adPersistXML</codeFeaturedElement>
rs1.<codeFeaturedElement>Save</codeFeaturedElement> stm, <codeFeaturedElement>adPersistXML</codeFeaturedElement>
rs2.<codeFeaturedElement>Open</codeFeaturedElement> stm</code>
    </content>
  </section>
  <section>
    <title>Scenario 2</title>
    <content>
      <para>This scenario persists a <legacyBold>Recordset</legacyBold> into a <legacyBold>Stream</legacyBold> in XML format. It then reads the <legacyBold>Stream</legacyBold> into a string that you can examine, manipulate, or display.</para>
      <code>Dim rs As ADODB.Recordset
Dim stm As ADODB.Stream
Dim strRst As String

Set rs = New ADODB.Recordset
Set stm = New ADODB.Stream

' Open, save, and close the recordset. 
rs.<codeFeaturedElement>Open</codeFeaturedElement> "SELECT * FROM Customers", "Provider=sqloledb;" &amp; _
        "Data Source=MyServer;Initial Catalog=Northwind;" &amp; _
        "Integrated Security=SSPI;"""
rs.<codeFeaturedElement>Save</codeFeaturedElement> stm, <codeFeaturedElement>adPersistXML</codeFeaturedElement>
rs.Close
Set rs = nothing

' Put saved Recordset into a string variable.
strRst = stm.<codeFeaturedElement>ReadText</codeFeaturedElement>(adReadAll)

' Examine, manipulate, or display the XML data.
...</code>
    </content>
  </section>
  <section>
    <title>Scenario 3</title>
    <content>
      <para>This example code shows ASP code persisting a <legacyBold>Recordset</legacyBold> as XML directly to the <legacyBold>Response</legacyBold> object:</para>
      <code>...
&lt;%
response.ContentType = "text/xml"

' Create and open a Recordset.
Set rs = Server.CreateObject("ADODB.Recordset")
rs.Open "select * from Customers", "Provider=sqloledb;" &amp; _
        "Data Source=MyServer;Initial Catalog=Northwind;" &amp; _
        "Integrated Security=SSPI;"""

' Save Recordset directly into output stream.
rs.<codeFeaturedElement>Save</codeFeaturedElement> Response, <codeFeaturedElement>adPersistXML</codeFeaturedElement> 

' Close Recordset.
rs.Close
Set rs = nothing
%&gt;
...</code>
    </content>
  </section>
  <section>
    <title>Scenario 4</title>
    <content>
      <para>In this scenario, ASP code writes the contents of the <legacyBold>Recordset</legacyBold> in ADTG format to the client. The <legacyLink xlink:href="420d0989-7cfb-4c66-a7b5-f4199d13165d">Microsoft Cursor Service for OLE DB</legacyLink> can use this data to create a disconnected <legacyBold>Recordset</legacyBold>.</para>
      <para>A new property on the RDS <legacyLink xlink:href="d85ea4fc-451c-436e-97b8-58f92b149dd0">DataControl</legacyLink>, <legacyLink xlink:href="8c56b233-1be8-442c-8d0e-a4c96465bc99">URL</legacyLink>, points to the .asp page that generates the <legacyBold>Recordset</legacyBold>. This means a <legacyBold>Recordset</legacyBold> object can be obtained without RDS using the server-side <legacyLink xlink:href="e75240c2-b749-471e-b6ea-98cae232efbe">DataFactory</legacyLink> object or the user writing a business object. This simplifies the RDS programming model significantly.</para>
      <para>Server-side code, named http://server/directory/recordset.asp:</para>
      <code>&lt;%
Dim rs 
Set rs = Server.CreateObject("ADODB.Recordset")
rs.Open "select au_fname, au_lname, phone from Authors", ""&amp; _
        "Provider=sqloledb;Data Source=MyServer;" &amp; _
        "Initial Catalog=Pubs;Integrated Security=SSPI;"
response.ContentType = "multipart/mixed"
rs.<codeFeaturedElement>Save</codeFeaturedElement> response, <codeFeaturedElement>adPersistADTG</codeFeaturedElement>
%&gt;</code>
      <para>Client-side code:</para>
      <code>&lt;HTML&gt;
&lt;HEAD&gt;
&lt;TITLE&gt;RDS Query Page&lt;/TITLE&gt;
&lt;/HEAD&gt;
&lt;body&gt;
&lt;CENTER&gt;
&lt;H1&gt;Remote Data Service 2.5&lt;/H1&gt;
&lt;TABLE DATASRC="#DC1"&gt;
   &lt;TR&gt; 
      &lt;TD&gt;&lt;SPAN DATAFLD="au_fname"&gt;&lt;/SPAN&gt;&lt;/TD&gt;
      &lt;TD&gt;&lt;SPAN DATAFLD="au_lname"&gt;&lt;/SPAN&gt;&lt;/TD&gt;
      &lt;TD&gt;&lt;SPAN DATAFLD="phone"&gt;&lt;/SPAN&gt;&lt;/TD&gt;
   &lt;/TR&gt;
&lt;/TABLE&gt;
&lt;BR&gt;

&lt;OBJECT classid="clsid:BD96C556-65A3-11D0-983A-00C04FC29E33"
    ID=DC1 HEIGHT=1 WIDTH = 1&gt;
    &lt;PARAM NAME="<codeFeaturedElement>URL</codeFeaturedElement>" VALUE="http://server/directory/recordset.asp"&gt;
&lt;/OBJECT&gt;

&lt;/SCRIPT&gt;
&lt;/BODY&gt;
&lt;/HTML&gt;</code>
      <para>Developers also have the option of using a <legacyBold>Recordset</legacyBold> object on the client:</para>
      <code>...
function GetRs() 
    {
    rs = CreateObject("ADODB.Recordset");
    rs.<codeFeaturedElement>Open</codeFeaturedElement> "http://server/directory/recordset.asp"
    DC1.SourceRecordset = rs;
    }
...</code>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="3236749c-4b71-4235-89e2-ccdfaaa9319d">Open Method (ADO Recordset)</link>
<link xlink:href="db83ed2c-a8e3-460c-8682-64667e4d5d01">Record Object</link>
<link xlink:href="ed3d9678-5c28-4e61-8bb3-7dfb66d99cf5">Save Method</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>