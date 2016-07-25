---
title: "Command Streams"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0ac09dbe-2665-411e-8fbb-d1efe6c777be
caps.latest.revision: 10
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
# Command Streams
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>ADO has always supported command input in string format specified by the <legacyBold>CommandText</legacyBold> property. As an alternative, with ADO 2.7 or later, you can also use a stream of information for command input by assigning the stream to the <legacyBold>CommandStream</legacyBold> property. You can assign an ADO <legacyBold>Stream</legacyBold> object, or any object that supports the COM <legacyBold>IStream</legacyBold> interface.</para>
    <para>The content of the command stream is simply passed from ADO to your provider, so your provider must support command input by stream for this feature to work. For example, SQL Server supports queries in the form of XML templates or OpenXML extensions to Transact-SQL. </para>
    <para>Because the details of the stream must be interpreted by the provider, you must specify the command dialect by setting the <legacyBold>Dialect</legacyBold> property. The value of <legacyBold>Dialect</legacyBold> is a string containing a GUID, which is defined by your provider. For information about valid values for <legacyBold>Dialect</legacyBold> supported by your provider, see your provider documentation. </para>
  </introduction>
  <section>
    <title>XML Template Query Example</title>
    <content>
      <para>The following example is written in VBScript to the Northwind database.</para>
      <para>First, initialize and open the <legacyBold>Stream</legacyBold> object that will be used to contain the query stream:</para>
      <code>Dim adoStreamQuery
Set adoStreamQuery = Server.CreateObject("ADODB.Stream")
adoStreamQuery.Open</code>
      <para>The content of the query stream will be an XML template query. </para>
      <para>The template query requires a reference to the XML namespace identified by the sql: prefix of the &lt;sql:query&gt; tag. A SQL SELECT statement is included as the content of the XML template and assigned to a string variable as follows:</para>
      <code>sQuery = "&lt;ROOT xmlns:sql='urn:schemas-microsoft-com:xml-sql'&gt;
&lt;sql:query&gt; SELECT * FROM PRODUCTS ORDER BY PRODUCTNAME &lt;/sql:query&gt;
&lt;/ROOT&gt;"</code>
      <para>Next, write the string to the stream:</para>
      <code>adoStreamQuery.WriteText sQuery, adWriteChar
adoStreamQuery.Position = 0</code>
      <para>Assign adoStreamQuery to the <legacyBold>CommandStream</legacyBold> property of an ADO <legacyBold>Command</legacyBold> object:</para>
      <code>Dim adoCmd
Set adoCmd  = Server.CreateObject("ADODB.Command"")
adoCmd.CommandStream = adoStreamQuery</code>
      <para>Specify the command language <legacyBold>Dialect</legacyBold>, which indicates how the SQL Server OLE DB Provider should interpret the command stream. The dialect specified by a provider-specific GUID:</para>
      <code>adoCmd.Dialect = "{5D531CB2-E6Ed-11D2-B252-00C04F681B71}"</code>
      <para>Finally, execute the query and return the results to a <legacyBold>Recordset</legacyBold> object:</para>
      <code>Set objRS = adoCmd.Execute</code>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>