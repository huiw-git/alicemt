---
title: "Current Record and Size of Recordset"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e63ff331-8655-4be7-82c6-e6cd6cc9d16d
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
# Current Record and Size of Recordset
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This section describes how to locate the current position of the cursor in the sample <legacyBold>Recordset</legacyBold> in <legacyLink xlink:href="74aad8a6-06cc-4a2c-811a-d78f9b741d84">JScript Code Example to Return a Recordset</legacyLink>.</para>
  </introduction>
  <section>
    <title>Current Record</title>
    <content>
      <para>The current record in the dataset corresponds to that pointed by the position of the cursor of the <legacyBold>Recordset</legacyBold> object. When a <legacyBold>Recordset</legacyBold> object is returned from the data source as the result of calling <legacyBold>Recordset.Open</legacyBold>, <legacyBold>Command.Execute</legacyBold>, or <legacyBold>Connection.Execute</legacyBold> (including <legacyBold>Connection.NamedCommand</legacyBold> and <legacyBold>Connection.StoredProcedure</legacyBold>), the cursor is set to point at the first record. In the sample dataset, the initial current record is the "Uncle Bob's Organic Dried Pears" item.</para>
    </content>
  </section>
  <section>
    <title>Size of Recordset</title>
    <content>
      <para>To find out the size of a <legacyBold>Recordset</legacyBold> object, get the value of the <legacyBold>Recordset.RecordCount</legacyBold> property. This value is a long integer that indicates the number of records in the <legacyBold>Recordset</legacyBold>. If the dataset is returned from the OLEDB Provider for Microsoft SQL Server, this value gives the number of rows returned. Reading the <legacyBold>RecordCount</legacyBold> property on a closed <legacyBold>Recordset</legacyBold> causes an error.</para>
      <para>If the number of records cannot be determined, the value of the property is –1. </para>
      <para>The value of the <legacyBold>RecordCount</legacyBold> property also depends on the capabilities of the provider and the type of cursor used. For a forward-only cursor, the value is -1. For a static or keyset cursor, the value is the actual number of records returned in the <legacyBold>Recordset</legacyBold> object. For a dynamic cursor, the value is either -1 or the actual number of records, depending on the data source.</para>
      <para>A cursor that supports <legacyBold>Recordcount</legacyBold> must work harder, and therefore requires more computing power, than a cursor does not support <legacyBold>Recordcount</legacyBold>. If you do not need to know the number of records, using different cursor type might help improve your application's performance, especially if you must deal with a large data set.</para>
      <para>In some cases, a provider or cursor is unable to determine the <legacyBold>RecordCount</legacyBold> value without first fetching all records from the data source. To ensure accurate counting, call the <legacyBold>Recordset</legacyBold>.<legacyBold>MoveLast</legacyBold> method before calling <legacyBold>Recordset.RecordCount</legacyBold>.</para>
      <para>The sample <legacyBold>Recordset</legacyBold> object obtained using the <legacyLink xlink:href="74aad8a6-06cc-4a2c-811a-d78f9b741d84">JScript Code Example</legacyLink> uses a forward-only cursor, so calling <legacyBold>RecordCount</legacyBold> on this object always results in –1. If you change the line of code that calls the <legacyBold>Recordset</legacyBold>.<legacyBold>Open</legacyBold> method as shown in the following example, the <legacyBold>RecordCount</legacyBold> property will return the actual number of records fetched.</para>
      <code>oRs.Open sSQL, sCnStr, adOpenStatic, adLockOptimistic, adCmdText </code>
      <para>This is because static cursors with the <legacyLink xlink:href="99bc40c4-9181-4ca1-a06f-9a1a914a0b7b">Microsoft OLE DB Provider for SQL Server</legacyLink> support <legacyBold>RecordCount</legacyBold>. In this example, there are five records and thus <legacyBold>RecordCount</legacyBold> should yield the value of 5.</para>
      <para>This section contains the following topic.</para>
      <para>
        <legacyLink xlink:href="c0dd4a0f-478d-4c5e-b5d5-7535f211d064">Boundaries of a Recordset</legacyLink>
      </para>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>