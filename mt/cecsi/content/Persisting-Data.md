---
title: "Persisting Data"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 21c162ca-2845-4dd8-a49d-e715aba8c461
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
# Persisting Data
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Portable computing (for example, using laptops) has generated the need for applications that can run in both a connected and disconnected state. ADO has added support for this by giving the developer the ability to save a client cursor <legacyBold>Recordset</legacyBold> to disk and reload it later.</para>
    <para>There are several scenarios in which you could use this type of feature, including the following:  </para>
    <list class="bullet">
      <listItem>
        <para>
          <legacyBold>Traveling:</legacyBold> When taking the application on the road, it is vital to supply the ability to make changes and add new records that can then be reconnected to the database later and committed.</para>
      </listItem>
      <listItem>
        <para>
          <legacyBold>Infrequently updated lookups:</legacyBold> Often in an application, tables are used as lookups—for example, state tax tables. They are infrequently updated and are read-only. Instead of rereading this data from the server each time the application is started, the application can simply load the data from a locally persisted <legacyBold>Recordset</legacyBold>.</para>
      </listItem>
    </list>
    <para>In ADO, to save and load <legacyBold>Recordsets</legacyBold>, use the <legacyBold>Recordset.Save</legacyBold> and <legacyBold>Recordset.Open(,,,,adCmdFile)</legacyBold> methods on the ADO <legacyBold>Recordset</legacyBold> object.</para>
    <para>You can use the <legacyBold>Recordset</legacyBold> <legacyBold>Save</legacyBold> method to persist your ADO <legacyBold>Recordset</legacyBold> to a file on a disk. (You can also save a <legacyBold>Recordset</legacyBold> to an ADO <legacyBold>Stream</legacyBold> object. <legacyBold>Stream</legacyBold> objects are discussed later in the guide.) Later, you can use the <legacyBold>Open</legacyBold> method to reopen the <legacyBold>Recordset</legacyBold> when you are ready to use it. By default, ADO saves the <legacyBold>Recordset</legacyBold> into the proprietary Microsoft Advanced Data TableGram (ADTG) format. This binary format is specified using the <legacyBold>adPersistADTG</legacyBold> <legacyBold>PersistFormatEnum</legacyBold> value. Alternatively, you can choose to save your <legacyBold>Recordset</legacyBold> out as XML instead using <legacyBold>adPersistXML</legacyBold>. For more information about saving Recordsets as XML, see <legacyLink xlink:href="f3113ec4-ae31-428f-89c6-bc1024f128ea">Persisting Records in XML Format</legacyLink>.</para>
    <para>The syntax of the <legacyBold>Save</legacyBold> method is as follows:</para>
    <code>
        recordset.
        Save
        Destination, PersistFormat
      </code>
    <para>The first time you save the <legacyBold>Recordset</legacyBold>, it is optional to specify <legacyItalic>Destination</legacyItalic>. If you omit <legacyItalic>Destination</legacyItalic>, a new file will be created with a name set to the value of the <legacyLink xlink:href="a05ba2c9-2821-4343-8607-4de9b764ec91">Source</legacyLink> property of the <legacyBold>Recordset</legacyBold>.</para>
    <para>Omit <legacyItalic>Destination</legacyItalic> when you subsequently call <legacyBold>Save</legacyBold> after the first save or a run-time error will occur. If you subsequently call <legacyBold>Save</legacyBold> with a new <legacyItalic>Destination</legacyItalic>, the <legacyBold>Recordset</legacyBold> is saved to the new destination. However, the new destination and the original destination will both be open.</para>
    <para>         <legacyBold>Save</legacyBold> does not close the <legacyBold>Recordset</legacyBold> or <legacyItalic>Destination</legacyItalic>, so you can continue to work with the <legacyBold>Recordset</legacyBold> and save your most recent changes. <legacyItalic>Destination</legacyItalic> remains open until the <legacyBold>Recordset</legacyBold> is closed, during which time other applications can read but not write to <legacyItalic>Destination</legacyItalic>.</para>
    <para>For reasons of security, the <legacyBold>Save</legacyBold> method permits only the use of low and custom security settings from a script executed by Microsoft Internet Explorer. </para>
    <para>If the <legacyBold>Save</legacyBold> method is called while an asynchronous <legacyBold>Recordset</legacyBold> fetch, execute, or update operation is in progress, <legacyBold>Save</legacyBold> waits until the asynchronous operation is complete.</para>
    <para>Records are saved beginning with the first row of the <legacyBold>Recordset</legacyBold>. When the <legacyBold>Save</legacyBold> method is finished, the current row position is moved to the first row of the <legacyBold>Recordset</legacyBold>.</para>
    <para>For best results, set the <legacyLink xlink:href="39c8d86e-7ee9-4182-be5e-aad5ce952f84">CursorLocation</legacyLink> property to <legacyBold>adUseClient</legacyBold> with <legacyBold>Save</legacyBold>. If your provider does not support all of the functionality necessary to save <legacyBold>Recordset</legacyBold> objects, the Cursor Service will provide that functionality.</para>
    <para>When a <legacyBold>Recordset</legacyBold> is persisted with the <legacyBold>CursorLocation</legacyBold> property set to <legacyBold>adUseServer</legacyBold>, the update capability for the <legacyBold>Recordset</legacyBold> is limited. Typically, only single-table updates, insertions, and deletions are allowed (dependent on provider functionality). The <legacyLink xlink:href="73b355d4-a4c0-434b-bfc4-039b1c76b32e">Resync</legacyLink> method is also unavailable in this configuration.</para>
    <para>Because the <legacyItalic>Destination</legacyItalic> parameter can accept any object that supports the OLE DB <legacyBold>IStream</legacyBold> interface, you can save a <legacyBold>Recordset</legacyBold> directly to the ASP <legacyBold>Response</legacyBold> object.</para>
    <para>In the following example, the <legacyBold>Save</legacyBold> and <legacyBold>Open</legacyBold> methods are used to persist a <legacyBold>Recordset</legacyBold> and later reopen it:</para>
    <code>'BeginPersist
   conn.ConnectionString = _
   "Provider=SQLOLEDB;Data Source=MySQLServer;" _
      &amp; "Integrated Security=SSPI;Initial Catalog=pubs"
   conn.Open

   conn.Execute "create table testtable (dbkey int " &amp; _
      "primary key, field1 char(10))"
   conn.Execute "insert into testtable values (1, 'string1')"

   Set rst.ActiveConnection = conn
   rst.CursorLocation = adUseClient

   rst.Open "select * from testtable", conn, adOpenStatic, _
      adLockBatchOptimistic

   'Change the row on the client
   rst!field1 = "NewValue"

   'Save to a file--the .dat extension is an example; choose
   'your own extension. The changes will be saved in the file
   'as well as the original data.
   MyFile = Dir("c:\temp\temptbl.dat")
   If MyFile &lt;&gt; "" Then
       Kill "c:\temp\temptbl.dat"
   End If
   
   rst.Save "c:\temp\temptbl.dat", adPersistADTG
   Set rst = Nothing

   'Now reload the data from the file
   Set rst = New ADODB.Recordset
   rst.Open "c:\temp\temptbl.dat", , adOpenStatic, _
      adLockBatchOptimistic, adCmdFile

   Debug.Print "After Loading the file from disk"
   Debug.Print "   Current Edited Value: " &amp; rst!field1.Value
   Debug.Print "   Value Before Editing: " &amp; rst!field1.OriginalValue

   'Note that you can reconnect to a connection and
   'submit the changes to the data source
   Set rst.ActiveConnection = conn
   rst.UpdateBatch
'EndPersist</code>
  </introduction>
  <section>
    <title>Remarks</title>
    <content>
      <para>This section contains the following topics.  </para>
      <list class="bullet">
        <listItem>
          <para>
            <legacyLink xlink:href="a9b287f5-04b0-4514-8143-f67879ca9842">More About Recordset Persistence</legacyLink>           </para>
        </listItem>
        <listItem>
          <para>
            <legacyLink xlink:href="d01aeb4d-4e43-450b-b3f2-0c27eaaf9f86">Persisting Filtered and Hierarchical Recordsets</legacyLink>           </para>
        </listItem>
        <listItem>
          <para>
            <legacyLink xlink:href="f3113ec4-ae31-428f-89c6-bc1024f128ea">Persisting Records in XML Format</legacyLink>           </para>
        </listItem>
      </list>
    </content>
  </section>
  <relatedTopics />
</developerConceptualDocument>