---
title: "Retrieving Resultsets into Streams"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 996c1321-c926-4f57-8297-85c8c20de974
caps.latest.revision: 11
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
# Retrieving Resultsets into Streams
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Instead of receiving results in the traditional <legacyBold>Recordset</legacyBold> object, ADO can instead retrieve query results into a stream. The ADO <legacyBold>Stream</legacyBold> object (or other objects that support the COM <legacyBold>IStream</legacyBold> interface, such as the ASP <legacyBold>Request</legacyBold> and <legacyBold>Response</legacyBold> objects) can be used to contain these results. One use for this feature is to retrieve results in XML format. With SQL Server, for example, XML results can be returned in multiple ways, such as using the FOR XML clause with a SQL SELECT query or using an XPath query.</para>
    <para>To receive query results in stream format instead of in a <legacyBold>Recordset</legacyBold>, you must specify the <legacyBold>adExecuteStream</legacyBold> constant from <legacyBold>ExecuteOptionEnum</legacyBold> as a parameter of the <legacyBold>Execute</legacyBold> method of a <legacyBold>Command</legacyBold> object. If your provider supports this feature, the results will be returned in a stream upon execution. You might be required to specify additional provider-specific properties before the code executes. For example, with the Microsoft OLE DB Provider for SQL Server, properties such as <legacyBold>Output Stream</legacyBold> in the <legacyBold>Properties</legacyBold> collection of the <legacyBold>Command</legacyBold> object must be specified. For more information about SQL Server-specific dynamic properties related to this feature, see XML-Related Properties in the SQL Server Books Online.</para>
  </introduction>
  <section>
    <title>FOR XML Query Example</title>
    <content>
      <para>The following example is written in VBScript to the Northwind database:</para>
      <code>&lt;!-- BeginRecordAndStreamVBS --&gt;
&lt;%@ LANGUAGE = VBScript %&gt;
&lt;%  Option Explicit      %&gt;

&lt;HTML&gt;
&lt;HEAD&gt;
&lt;META NAME="GENERATOR" Content="Microsoft Developer Studio"/&gt;
&lt;META HTTP-EQUIV="Content-Type" content="text/html"; charset="iso-8859-1"&gt;
&lt;TITLE&gt;FOR XML Query Example&lt;/TITLE&gt;

&lt;STYLE&gt;
   BODY
   {
      FONT-FAMILY: Tahoma;
      FONT-SIZE: 8pt;
      OVERFLOW: auto
   }

   H3
   {
      FONT-FAMILY: Tahoma;
      FONT-SIZE: 8pt;
      OVERFLOW: auto
   }
&lt;/STYLE&gt;

&lt;!-- #include file="adovbs.inc" --&gt;
&lt;%
   Response.Write "&lt;H3&gt;Server-side processing&lt;/H3&gt;"

   Response.Write "Page Generated @ " &amp; Now() &amp; "&lt;BR/&gt;"

   Dim adoConn
   Set adoConn = Server.CreateObject("ADODB.Connection")

   Dim sConn
   sConn = "Provider=SQLOLEDB;Data Source=" &amp; _
      Request.ServerVariables("SERVER_NAME") &amp;amp; ";" &amp; _
      Initial Catalog=Northwind;Integrated Security=SSPI;"

   Response.write "Connect String = " &amp; sConn &amp; "&lt;BR/&gt;"

   adoConn.ConnectionString = sConn
   adoConn.CursorLocation = adUseClient

   adoConn.Open

   Response.write "ADO Version = " &amp; adoConn.Version &amp; "&lt;BR/&gt;"
   Response.write "adoConn.State = " &amp; adoConn.State &amp; "&lt;BR/&gt;"

   Dim adoCmd
   Set adoCmd = Server.CreateObject("ADODB.Command")
   Set adoCmd.ActiveConnection = adoConn

   Dim sQuery
   sQuery = "&lt;ROOT xmlns:sql='urn:schemas-microsoft-com:xml-sql'&gt;&lt;sql:query&gt;SELECT * FROM PRODUCTS WHERE ProductName='Gumbr Gummibrchen' FOR XML AUTO&lt;/sql:query&gt;&lt;/ROOT&gt;"

   Response.write "Query String = " &amp; sQuery &amp; "&lt;BR/&gt;"

   Dim adoStreamQuery
   Set adoStreamQuery = Server.CreateObject("ADODB.Stream")
   adoStreamQuery.Open
   adoStreamQuery.WriteText sQuery, adWriteChar
   adoStreamQuery.Position = 0

   adoCmd.CommandStream = adoStreamQuery
   adoCmd.Dialect = "{5D531CB2-E6Ed-11D2-B252-00C04F681B71}"

   Response.write "Pushing XML to client for processing "  &amp; "&lt;BR/&gt;"

   adoCmd.Properties("Output Stream") = Response
   Response.write "&lt;XML ID='MyDataIsle'&gt;"
   adoCmd.Execute , , 1024
   Response.write "&lt;/XML&gt;"

%&gt;

&lt;SCRIPT language="VBScript" For="window" Event="onload"&gt;
   Dim xmlDoc
   Set xmlDoc = MyDataIsle.XMLDocument
   xmlDoc.resolveExternals=false
   xmlDoc.async=false

   If xmlDoc.parseError.Reason &lt;&gt; "" then
      Msgbox "parseError.Reason = " &amp; xmlDoc.parseError.Reason
   End If
            
   Dim root, child
   Set root = xmlDoc.documentElement
   For each child in root.childNodes
      dim OutputXML
      OutputXML = document.all("log").innerHTML
      document.all("log").innerHTML = OutputXML &amp; "&lt;LI&gt;" &amp; child.getAttribute("ProductName") &amp; "&lt;/LI&gt;"
   Next
&lt;/SCRIPT&gt;

&lt;/HEAD&gt;

&lt;BODY&gt;

   &lt;H3&gt;Client-side processing of XML Document MyDataIsle&lt;/H3&gt;
   &lt;UL id=log&gt;
   &lt;/UL&gt;

&lt;/BODY&gt;
&lt;/HTML&gt;
&lt;!-- EndRecordAndStreamVBS --&gt;
</code>
      <para>The FOR XML clause instructs SQL Server to return data in the form of an XML document.</para>
    </content>
    <sections>
      <section>
        <title>FOR XML Syntax</title>
        <content>
          <code>FOR XML [RAW|AUTO|EXPLICIT]</code>
          <para>FOR XML RAW generates generic row elements that have column values as attributes. FOR XML AUTO uses heuristics to generate a hierarchical tree with element names based on table names. FOR XML EXPLICIT generates a universal table with relationships fully described by metadata.</para>
          <para>An example SQL SELECT FOR XML statement follows:</para>
          <code>SELECT * FROM PRODUCTS ORDER BY PRODUCTNAME FOR XML AUTO</code>
          <para>The command can be specified in a string as shown earlier, assigned to <legacyBold>CommandText</legacyBold>, or in the form of an XML template query assigned to <legacyBold>CommandStream</legacyBold>. For more information about XML template queries, see <legacyLink xlink:href="0ac09dbe-2665-411e-8fbb-d1efe6c777be">Command Streams</legacyLink> in ADO or Using Streams for Command Input in the SQL Server Books Online.</para>
          <para>As an XML template query, the FOR XML query appears as follows:</para>
          <code>&lt;sql:query&gt; SELECT * FROM PRODUCTS ORDER BY PRODUCTNAME FOR XML AUTO &lt;/sql:query&gt;</code>
          <para>This example specifies the ASP <legacyBold>Response</legacyBold> object for the <legacyBold>Output Stream</legacyBold> property:</para>
          <code>adoCmd.Properties("Output Stream") = Response</code>
          <para>Next, specify <legacyBold>adExecuteStream</legacyBold> parameter of <legacyBold>Execute</legacyBold>. This example wraps the stream in XML tags to create an XML data island:</para>
          <code>Response.write "&lt;XML ID=MyDataIsle&gt;"
adoCmd.Execute , , adExecuteStream
Response.write "&lt;/XML&gt;"</code>
        </content>
      </section>
      <section>
        <title>Remarks</title>
        <content>
          <para>At this point, XML has been streamed to the client browser and it is ready to be displayed. This is done by using client-side VBScript to bind the XML document to an instance of the DOM and looping through each child node to build a list of Products in HTML.</para>
        </content>
      </section>
    </sections>
  </section>
  <relatedTopics />
</developerConceptualDocument>