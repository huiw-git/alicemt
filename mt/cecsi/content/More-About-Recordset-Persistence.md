---
title: "More About Recordset Persistence"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a9b287f5-04b0-4514-8143-f67879ca9842
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
# More About Recordset Persistence
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The ADO Recordset object supports storing the contents of a <legacyBold>Recordset</legacyBold> object in a file by using its <legacyLink xlink:href="ed3d9678-5c28-4e61-8bb3-7dfb66d99cf5">Save</legacyLink> method. The persistently stored file may exist on a local drive, server, or as a URL on a Web site. Later, the file can be restored with either the <legacyLink xlink:href="3236749c-4b71-4235-89e2-ccdfaaa9319d">Open</legacyLink> method of the <legacyBold>Recordset</legacyBold> object or the <legacyLink xlink:href="03c69320-96b2-4d85-8d49-a13b13e31578">Execute</legacyLink> method of the <legacyLink xlink:href="ef6b1824-5b12-43db-89d7-8f3d13896d4d">Connection</legacyLink> object.</para>
    <para>In addition, the <legacyLink xlink:href="92452940-b2a7-456e-94fc-3780c71da33c">GetString</legacyLink> method converts a <legacyBold>Recordset</legacyBold> object to a form in which the columns and rows are delimited with characters you specify.</para>
    <para>To persist a <legacyBold>Recordset</legacyBold>, begin by converting it to a form that can be stored in a file. <legacyBold>Recordset</legacyBold> objects can be stored in the proprietary Advanced Data TableGram (ADTG) format or the open Extensible Markup Language (XML) format. ADTG examples are shown in the next section. For more information about XML persistence, see <legacyLink xlink:href="f3113ec4-ae31-428f-89c6-bc1024f128ea">Persisting Records in XML format</legacyLink>.</para>
    <para>Save any pending changes in the persisted file. Doing this allows you to issue a query that returns a <legacyBold>Recordset</legacyBold> object, edits the <legacyBold>Recordset</legacyBold>, saves it and the pending changes, later restores the <legacyBold>Recordset</legacyBold>, and then updates the data source with the saved pending changes.</para>
    <para>For information about persistently storing <legacyBold>Stream</legacyBold> objects, see <legacyLink xlink:href="ad5bf52c-fd10-4cfa-bf7d-fcedcaa41eea">Streams and Persistence</legacyLink>.</para>
    <para>For an example of <legacyBold>Recordset</legacyBold> persistence, see the XML Recordset Persistence Scenario.</para>
  </introduction>
  <section>
    <title>Example</title>
    <content />
    <sections>
      <section>
        <title>Save a Recordset:</title>
        <content>
          <code>Dim rs as New ADODB.Recordset
rs.Save "c:\yourFile.adtg", adPersistADTG</code>
        </content>
      </section>
      <section>
        <title>Open a persisted file with Recordset.Open:</title>
        <content>
          <code>Dim rs as New ADODB.Recordset
rs.Open "c:\yourFile.adtg", "Provider=MSPersist",,,adCmdFile</code>
          <para>Optionally, if the <legacyBold>Recordset</legacyBold> does not have an active connection, you can accept all the defaults and code the following:</para>
          <code>Dim rs as New ADODB.Recordset
rs.Open "c:\yourFile.adtg"</code>
        </content>
      </section>
      <section>
        <title>Open a persisted file with Connection.Execute:</title>
        <content>
          <code>Dim conn as New ADODB.Connection
Dim rs as ADODB.Recordset
conn.Open "Provider=MSPersist"
Set rs = conn.execute("c:\yourFile.adtg")</code>
        </content>
      </section>
      <section>
        <title>Open a persisted file with RDS.DataControl:</title>
        <content>
          <para>In this case, the <legacyBold>Server</legacyBold> property is not set.</para>
          <code>Dim dc as New RDS.DataControl
dc.Connection = "Provider=MSPersist"
dc.SQL = "c:\yourFile.adtg"
dc.Refresh</code>
        </content>
      </section>
    </sections>
  </section>
  <relatedTopics>
<link xlink:href="92452940-b2a7-456e-94fc-3780c71da33c">GetString Method</link>
<link xlink:href="e75ef0dc-2016-4fcc-8918-23311c0d4e02">Microsoft OLE DB Persistence Provider</link>
<link xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset Object</link>
<link xlink:href="ad5bf52c-fd10-4cfa-bf7d-fcedcaa41eea">Streams and Persistence</link>
</relatedTopics>
</developerConceptualDocument>