---
title: "Connection Object (ADO)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: ef6b1824-5b12-43db-89d7-8f3d13896d4d
caps.latest.revision: 5
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
# Connection Object (ADO)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Represents an open connection to a data source.</para>
  </introduction>
  <languageReferenceRemarks>
    <content>
      <para>A <legacyBold>Connection</legacyBold> object represents a unique session with a data source. In a client/server database system, it may be equivalent to an actual network connection to the server. Depending on the functionality supported by the provider, some collections, methods, or properties of a <legacyBold>Connection</legacyBold> object may not be available.</para>
      <para>With the collections, methods, and properties of a <legacyBold>Connection</legacyBold> object, you can do the following:  </para>
      <list class="bullet">
        <listItem>
          <para>Configure the connection before opening it with the <legacyLink xlink:href="3be75b75-4d36-4479-ab64-9a456869252a">ConnectionString</legacyLink>, <legacyLink xlink:href="8904a403-1383-4b4b-b53d-5c01d6f5deac">ConnectionTimeout</legacyLink>, and <legacyLink xlink:href="808661eb-0d7c-4e6d-8e40-9dc3bef3d77a">Mode</legacyLink> properties. <legacyBold>ConnectionString</legacyBold> is the default property of the <legacyBold>Connection</legacyBold> object.</para>
        </listItem>
        <listItem>
          <para>Set the <legacyLink xlink:href="39c8d86e-7ee9-4182-be5e-aad5ce952f84">CursorLocation</legacyLink> property to client to invoke the <legacyLink xlink:href="420d0989-7cfb-4c66-a7b5-f4199d13165d">Microsoft Cursor Service for OLE DB</legacyLink>, which supports batch updates.</para>
        </listItem>
        <listItem>
          <para>Set the default database for the connection with the <legacyLink xlink:href="41e8a8dd-e69c-4a09-8736-93502e01961c">DefaultDatabase</legacyLink> property.</para>
        </listItem>
        <listItem>
          <para>Set the level of isolation for the transactions opened on the connection with the <legacyLink xlink:href="ea84e4b2-fbf2-4eef-b9ce-796b22e21800">IsolationLevel</legacyLink> property.</para>
        </listItem>
        <listItem>
          <para>Specify an OLE DB provider with the <legacyLink xlink:href="0ff70e72-0061-4ffc-90fb-e3ea23129bb2">Provider</legacyLink> property.</para>
        </listItem>
        <listItem>
          <para>Establish, and later break, the physical connection to the data source with the <legacyLink xlink:href="663defab-5545-4973-9036-24d5882c9737">Open</legacyLink> and <legacyLink xlink:href="3cdf27d1-a180-4cff-8e42-95dec5fb1b55">Close</legacyLink> methods.</para>
        </listItem>
        <listItem>
          <para>Execute a command on the connection with the <legacyLink xlink:href="03c69320-96b2-4d85-8d49-a13b13e31578">Execute</legacyLink> method and configure the execution with the <legacyLink xlink:href="c611f857-d6b0-4dca-8925-f4a02e769eb0">CommandTimeout</legacyLink> property. </para>
          <alert class="note">
            <para>To execute a query without using a Command object, pass a query string to the <legacyBold>Execute</legacyBold> method of a <legacyBold>Connection</legacyBold> object. However, a <legacyLink xlink:href="a02c22fb-542d-465e-a629-30fd59dcbebf">Command</legacyLink> object is required when you want to persist the command text and re-execute it, or use query parameters.</para>
          </alert>
        </listItem>
        <listItem>
          <para>Manage transactions on the open connection, including nested transactions if the provider supports them, with the <legacyLink xlink:href="d4683472-4120-4236-8640-fa9ae289e23e">BeginTrans</legacyLink>, <legacyLink xlink:href="d4683472-4120-4236-8640-fa9ae289e23e">CommitTrans</legacyLink>, and <legacyLink xlink:href="d4683472-4120-4236-8640-fa9ae289e23e">RollbackTrans</legacyLink> methods and the <legacyLink xlink:href="acc15d40-68a6-4ba9-85bd-12d331aecaa6">Attributes</legacyLink> property.</para>
        </listItem>
        <listItem>
          <para>Examine errors returned from the data source with the <legacyLink xlink:href="290819e1-7b39-4e1e-a93b-801257138b00">Errors</legacyLink> collection.</para>
        </listItem>
        <listItem>
          <para>Read the version from the ADO implementation used with the <legacyLink xlink:href="db4cb894-9bd9-422d-a58a-cef6941a5784">Version</legacyLink> property.</para>
        </listItem>
        <listItem>
          <para>Obtain schema information about your database with the <legacyLink xlink:href="850cf3ce-f18f-4e7c-8597-96c1dc504866">OpenSchema</legacyLink> method.</para>
        </listItem>
      </list>
      <para>You can create <legacyBold>Connection</legacyBold> objects independently of any other previously defined object.</para>
      <para>You can execute named commands or stored procedures as if they were native methods on a <legacyBold>Connection</legacyBold> object, as shown in the next section. When a named command has the same name as that of a stored procedure, invoke the "native method call" on a <legacyBold>Connection</legacyBold> object always execute the named command instead of the store procedure.</para>
      <alert class="note">
        <para>Do not use this feature (calling a named command or stored procedure as if it were a native method on the <legacyBold>Connection</legacyBold> object) in a Microsoft® .NET Framework application, because the underlying implementation of the feature conflicts with the way the .NET Framework interoperates with COM.</para>
      </alert>
    </content>
  </languageReferenceRemarks>
  <section>
    <title>Execute a command as a native method of a Connection object</title>
    <content>
      <para>To execute a command, give the command a name using the <legacyBold>Command</legacyBold> object <legacyLink xlink:href="cfd0e29c-8310-44ab-85c3-5761184b865d">Name</legacyLink> property. Set the <legacyBold>ActiveConnection</legacyBold> property of the <legacyBold>Command</legacyBold> object to the connection. Then issue a statement where the command name is used as if it were a method on the <legacyBold>Connection</legacyBold> object, followed by any parameters, and a <legacyBold>Recordset</legacyBold> object if any rows are returned. Set the <legacyBold>Recordset</legacyBold> properties to customize the resulting <legacyBold>Recordset</legacyBold>. For example:</para>
      <code>Dim cnn As New ADODB.Connection
Dim cmd As New ADODB.Command
Dim rst As New ADODB.Recordset
...
cnn.Open "..."
cmd.Name = "yourCommandName"
cmd.ActiveConnection = cnn
...
'Your command name, any parameters, and an optional Recordset.
cnn. "parameter", rst</code>
    </content>
  </section>
  <section>
    <title>Execute a stored procedure as a native method of a Connection object</title>
    <content>
      <para>To execute a stored procedure, issue a statement where the stored procedure name is used as if it were a method on the <legacyBold>Connection</legacyBold> object, followed by any parameters. ADO will make a "best guess" of parameter types. For example:</para>
      <code>Dim cnn As New ADODB.Connection
...
'Your stored procedure name and any parameters.
cnn. "parameter"</code>
      <para>The <legacyBold>Connection</legacyBold> object is safe for scripting.</para>
      <para>This section contains the following topic.  </para>
      <list class="bullet">
        <listItem>
          <para>
            <legacyLink xlink:href="f571b74d-b796-4009-9c66-6a36ab995a2a">Connection Object Properties, Methods, and Events</legacyLink>  </para>
        </listItem>
      </list>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="a02c22fb-542d-465e-a629-30fd59dcbebf">Command Object</link>
<link xlink:href="290819e1-7b39-4e1e-a93b-801257138b00">Errors Collection</link>
<link xlink:href="1d539aa8-ce0d-4418-ab03-8d0a3c1e9d82">Properties Collection</link>
<link xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset Object</link>
<link xlink:href="e2581b47-b11e-4e1e-b96c-d39c77c5b48a">Appendix A: Providers</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>