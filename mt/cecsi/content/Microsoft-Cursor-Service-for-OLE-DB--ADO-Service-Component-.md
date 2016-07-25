---
title: "Microsoft Cursor Service for OLE DB (ADO Service Component)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 420d0989-7cfb-4c66-a7b5-f4199d13165d
caps.latest.revision: 15
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
# Microsoft Cursor Service for OLE DB (ADO Service Component)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The Microsoft Cursor Service for OLE DB supplements the cursor support functions of data providers. As a result, the user perceives relatively uniform functionality from all data providers.</para>
    <para>The Cursor Service makes dynamic properties available and enhances the behavior of certain methods. For example, the <legacyLink xlink:href="a491c4ce-2b04-4c84-be83-3846bde8d16b">Optimize</legacyLink> dynamic property enables the creation of temporary indexes to facilitate certain operations, such as the <legacyLink xlink:href="55c9810a-d8ca-46c2-a9dc-80e7ee7aa188">Find</legacyLink> method.</para>
    <para>The Cursor Service enables support for batch updating in all cases. It also simulates more capable cursor types, such as dynamic cursors, when a data provider can only supply less capable cursors, such as static cursors.</para>
  </introduction>
  <section>
    <title>Keyword</title>
    <content>
      <para>To invoke this service component, set the <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink> or <legacyLink xlink:href="ef6b1824-5b12-43db-89d7-8f3d13896d4d">Connection</legacyLink> object's <legacyLink xlink:href="39c8d86e-7ee9-4182-be5e-aad5ce952f84">CursorLocation</legacyLink> property to <legacyBold>adUseClient</legacyBold>.</para>
      <code>connection.CursorLocation=adUseClient
recordset.CursorLocation=adUseClient</code>
    </content>
  </section>
  <section>
    <title>Dynamic Properties</title>
    <content>
      <para>When the Cursor Service for OLE DB is invoked, the following dynamic properties are added to the <legacyBold>Recordset </legacyBold>object's <legacyLink xlink:href="1d539aa8-ce0d-4418-ab03-8d0a3c1e9d82">Properties</legacyLink> collection. The full list of <legacyBold>Connection</legacyBold> and <legacyBold>Recordset</legacyBold> object dynamic properties is listed in the <legacyLink xlink:href="80d389dd-46ef-459f-b0d4-6f712fc4f32d">ADO Dynamic Property Index</legacyLink>. The associated OLE DB property names, where appropriate, are included in parentheses after the ADO property name.</para>
      <para>Changes to some dynamic properties are not visible to the underlying data source after the Cursor Service has been invoked. For example, setting the <legacyItalic>Command Time out</legacyItalic> property on a <legacyBold>Recordset</legacyBold> will not be visible to the underlying data provider.</para>
      <code>
Recordset1.CursorLocation = adUseClient     'invokes cursor service
Recordset1.Open "authors", _
    "Provider=SQLOLEDB;Data Source=DBServer;User Id=MyUserID;" &amp; _
    "Password=MyPassword;Initial Catalog=pubs;",,adCmdTable
Recordset1.Properties.Item("Command Time out") = 50
' 'Command Time out' property on DBServer is still default (30).
</code>
      <para>If your application requires the Cursor Service, but you need to set dynamic properties on the underlying provider, set the properties before invoking the Cursor Service. Command object property settings are always passed to the underlying data provider regardless of cursor location. Therefore, you can also use a command object to set the properties at any time.</para>
      <alert class="note">
        <para>The dynamic property DBPROP_SERVERDATAONINSERT is not supported by the cursor service, even if it is supported by the underlying data provider.</para>
      </alert>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>Property Name</para>
            </TD>
            <TD>
              <para>Description</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>Auto Recalc (DBPROP_ADC_AUTORECALC)</para>
            </TD>
            <TD>
              <para>For recordsets created with the Data Shaping Service, this value indicates how often calculated and aggregate columns are calculated. The default (value=1) is to recalculate whenever the Data Shaping Service determines that the values have changed. If the value is 0, the calculated or aggregate columns are only calculated when the hierarchy is initially built.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Batch Size (DBPROP_ADC_BATCHSIZE)</para>
            </TD>
            <TD>
              <para>Indicates the number of update statements that can be batched before being sent to the data store. The more statements in a batch, the fewer round trips to the data store.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Cache Child Rows (DBPROP_ADC_CACHECHILDROWS)</para>
            </TD>
            <TD>
              <para>For recordsets created with the Data Shaping Service, this value indicates whether child recordsets are stored in a cache for later use.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Cursor Engine Version (DBPROP_ADC_CEVER)</para>
            </TD>
            <TD>
              <para>Indicates the version of the Cursor Service being used.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Maintain Change Status (DBPROP_ADC_MAINTAINCHANGESTATUS)</para>
            </TD>
            <TD>
              <para>Indicates the text of the command used for resynchronizing a one or more rows in a multiple table join.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyLink xlink:href="a491c4ce-2b04-4c84-be83-3846bde8d16b">Optimize</legacyLink>
              </para>
            </TD>
            <TD>
              <para>Indicates whether an index should be created. When set to <legacyBold>True</legacyBold>, authorizes the temporary creation of indexes to improve the execution of certain operations.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyLink xlink:href="690229d1-46cc-42e6-a57d-4438251fe248">Reshape Name</legacyLink>
              </para>
            </TD>
            <TD>
              <para>Indicates the name of the <legacyBold>Recordset</legacyBold>. Can be referenced within the current, or subsequent, data shaping commands.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyLink xlink:href="4e2bb601-0fe8-4d61-b00e-38341d85a6bb">Resync Command</legacyLink>
              </para>
            </TD>
            <TD>
              <para>Indicates a custom command string that is used by the <legacyLink xlink:href="73b355d4-a4c0-434b-bfc4-039b1c76b32e">Resync</legacyLink> method when the <legacyLink xlink:href="d0e775d8-e353-46a1-ad10-ed4cc240dfaa">Unique Table</legacyLink> property is in effect.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyLink xlink:href="d0e775d8-e353-46a1-ad10-ed4cc240dfaa">Unique Catalog</legacyLink>
              </para>
            </TD>
            <TD>
              <para>Indicates the name of the database containing the table referenced in the <legacyBold>Unique Table</legacyBold> property.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyLink xlink:href="d0e775d8-e353-46a1-ad10-ed4cc240dfaa">Unique Schema</legacyLink>
              </para>
            </TD>
            <TD>
              <para>Indicates the name of the owner of the table referenced in the <legacyBold>Unique Table</legacyBold> property.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyLink xlink:href="d0e775d8-e353-46a1-ad10-ed4cc240dfaa">Unique Table</legacyLink>
              </para>
            </TD>
            <TD>
              <para>Indicates the name of the one table in a <legacyBold>Recordset</legacyBold> created from multiple tables that can be modified by insertions, updates, or deletions.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Update Criteria (DBPROP_ADC_UPDATECRITERIA)</para>
            </TD>
            <TD>
              <para>Indicates which fields in the <legacyBold>WHERE</legacyBold> clause are used to handle collisions occurring during an update.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyLink xlink:href="8a3bb608-66d7-4128-a3ef-84cb0556de0d">Update Resync</legacyLink>               <legacyUnderline>               </legacyUnderline>(DBPROP_ADC_UPDATERESYNC)</para>
            </TD>
            <TD>
              <para>Indicates whether the <legacyBold>Resync</legacyBold> method is implicitly invoked after the <legacyLink xlink:href="23f9314c-b027-4a51-aeae-50caa2977740">UpdateBatch</legacyLink> method (and its behavior), when the <legacyBold>Unique Table</legacyBold> property is in effect.</para>
            </TD>
          </tr>
        </tbody>
      </table>
      <para>You can also set or retrieve a dynamic property by specifying its name as the index to the <legacyBold>Properties</legacyBold> collection. For example, get and print the current value of the <legacyLink xlink:href="a491c4ce-2b04-4c84-be83-3846bde8d16b">Optimize</legacyLink> dynamic property, then set a new value, as follows:</para>
      <code>Debug.Print rs.Properties("Optimize")
rs.Properties("Optimize") = True</code>
    </content>
  </section>
  <section>
    <title>Built-in Property Behavior</title>
    <content>
      <para>The Cursor Service for OLE DB also affects the behavior of certain built-in properties.</para>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>Property Name</para>
            </TD>
            <TD>
              <para>Description</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>
                <legacyLink xlink:href="b62c66ca-58d5-430e-9257-eb38c65e48c2">CursorType</legacyLink>             </para>
            </TD>
            <TD>
              <para>Supplements the types of cursors that are available for a <legacyBold>Recordset</legacyBold>.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyLink xlink:href="9920c14e-033a-4de1-8149-0ce9737a3246">LockType</legacyLink>             </para>
            </TD>
            <TD>
              <para>Supplements the types of locks available for a <legacyBold>Recordset</legacyBold>. Enables batch updates.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyLink xlink:href="3683ffa0-6f93-4906-9533-ef6942f24f39">Sort</legacyLink>
              </para>
            </TD>
            <TD>
              <para>Specifies one or more field names that the <legacyBold>Recordset</legacyBold> is sorted on, and whether each field is sorted in ascending or descending order.</para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <section>
    <title>Method Behavior</title>
    <content>
      <para>The Cursor Service for OLE DB enables or affects the behavior of the <legacyLink xlink:href="b10a72fc-3c4b-4186-a70b-993dc9f7a092">Field</legacyLink> object's <legacyLink xlink:href="f8a9bbed-ba9c-4698-945d-317ad22d2e92">Append</legacyLink> method; and the <legacyBold>Recordset</legacyBold> object's <legacyLink xlink:href="3236749c-4b71-4235-89e2-ccdfaaa9319d">Open</legacyLink>, <legacyLink xlink:href="73b355d4-a4c0-434b-bfc4-039b1c76b32e">Resync</legacyLink>, <legacyLink xlink:href="23f9314c-b027-4a51-aeae-50caa2977740">UpdateBatch</legacyLink>, and <legacyLink xlink:href="ed3d9678-5c28-4e61-8bb3-7dfb66d99cf5">Save</legacyLink> methods.</para>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>