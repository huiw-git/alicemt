---
title: "Command Object (ADO)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: a02c22fb-542d-465e-a629-30fd59dcbebf
caps.latest.revision: 6
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
# Command Object (ADO)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Defines a specific command that you intend to execute against a data source.</para>
  </introduction>
  <languageReferenceRemarks>
    <content>
      <para>Use a <legacyBold>Command</legacyBold> object to query a database and return records in a <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink> object, to execute a bulk operation, or to manipulate the structure of a database. Depending on the functionality of the provider, some <legacyBold>Command</legacyBold> collections, methods, or properties may generate an error when they are referenced.</para>
      <para>With the collections, methods, and properties of a <legacyBold>Command</legacyBold> object, you can do the following:  </para>
      <list class="bullet">
        <listItem>
          <para>Define the executable text of the command (for example, an SQL statement) with the <legacyLink xlink:href="4dd7e82a-8da5-4a4e-b439-11a29286fa0e">CommandText</legacyLink> property. Alternatively, for command or query structures other than simple strings (for example, XML template queries) define the command with the <legacyLink xlink:href="f78f61b6-87e0-48dc-961e-83d0e20da58e">CommandStream</legacyLink> property.</para>
        </listItem>
        <listItem>
          <para>Optionally, indicate the command dialect used in the <legacyBold>CommandText</legacyBold> or <legacyBold>CommandStream</legacyBold> with the <legacyLink xlink:href="329c3a71-ba88-4009-b04f-2f52195a5957">Dialect</legacyLink> property.</para>
        </listItem>
        <listItem>
          <para>Define parameterized queries or stored-procedure arguments with <legacyLink xlink:href="e010e794-7f0f-4026-8b5b-37328e437d63">Parameter</legacyLink> objects and the <legacyLink xlink:href="497cae10-3913-422a-9753-dcbb0a639b1b">Parameters</legacyLink> collection.</para>
        </listItem>
        <listItem>
          <para>Indicate whether parameter names should be passed to the provider with the <legacyLink xlink:href="42409387-026c-435f-a9b1-bf4167095875">NamedParameters</legacyLink> property.</para>
        </listItem>
        <listItem>
          <para>Execute a command and return a <legacyBold>Recordset</legacyBold> object if appropriate with the <legacyLink xlink:href="f84a5ff3-0528-4ad7-9bea-9a15103378dd">Execute</legacyLink> method.</para>
        </listItem>
        <listItem>
          <para>Specify the type of command with the <legacyLink xlink:href="ca44809c-8647-48b6-a7fb-0be70a02f53e">CommandType</legacyLink> property prior to execution to optimize performance.</para>
        </listItem>
        <listItem>
          <para>Control whether the provider saves a prepared (or compiled) version of the command prior to execution with the <legacyLink xlink:href="11ca8825-765e-4bb4-a6ce-3f6564ad8755">Prepared</legacyLink> property.</para>
        </listItem>
        <listItem>
          <para>Set the number of seconds that a provider will wait for a command to execute with the <legacyLink xlink:href="c611f857-d6b0-4dca-8925-f4a02e769eb0">CommandTimeout</legacyLink> property.</para>
        </listItem>
        <listItem>
          <para>Associate an open connection with a <legacyBold>Command</legacyBold> object by setting its <legacyLink xlink:href="52d0a96c-14fb-4ad9-b004-4d821bc0a6db">ActiveConnection</legacyLink> property.</para>
        </listItem>
        <listItem>
          <para>Set the <legacyLink xlink:href="cfd0e29c-8310-44ab-85c3-5761184b865d">Name</legacyLink> property to identify the <legacyBold>Command</legacyBold> object as a method on the associated <legacyLink xlink:href="ef6b1824-5b12-43db-89d7-8f3d13896d4d">Connection</legacyLink> object.</para>
        </listItem>
        <listItem>
          <para>Pass a <legacyBold>Command</legacyBold> object to the <legacyLink xlink:href="a05ba2c9-2821-4343-8607-4de9b764ec91">Source</legacyLink> property of a <legacyBold>Recordset</legacyBold> to obtain data.</para>
        </listItem>
        <listItem>
          <para>Access provider-specific attributes with the <legacyLink xlink:href="1d539aa8-ce0d-4418-ab03-8d0a3c1e9d82">Properties</legacyLink> collection.</para>
        </listItem>
      </list>
      <alert class="note">
        <para>To execute a query without using a <legacyBold>Command</legacyBold> object, pass a query string to the <legacyLink xlink:href="03c69320-96b2-4d85-8d49-a13b13e31578">Execute</legacyLink> method of a <legacyBold>Connection</legacyBold> object or to the <legacyLink xlink:href="3236749c-4b71-4235-89e2-ccdfaaa9319d">Open</legacyLink> method of a <legacyBold>Recordset</legacyBold> object. However, a <legacyBold>Command</legacyBold> object is required when you want to persist the command text and re-execute it, or use query parameters.</para>
      </alert>
      <para>To create a <legacyBold>Command</legacyBold> object independently of a previously defined <legacyBold>Connection</legacyBold> object, set its <legacyBold>ActiveConnection</legacyBold> property to a valid connection string. ADO still creates a <legacyBold>Connection</legacyBold> object, but it does not assign that object to an object variable. However, if you are associating multiple <legacyBold>Command</legacyBold> objects with the same connection, you should explicitly create and open a <legacyBold>Connection</legacyBold> object; this assigns the <legacyBold>Connection</legacyBold> object to an object variable. Make sure that the <legacyBold>Connection</legacyBold> object was opened successfully before you assign it to the <legacyBold>ActiveConnection</legacyBold> property of the <legacyBold>Command</legacyBold> object, because assigning a closed <legacyBold>Connection</legacyBold> object causes an error. If you do not set the <legacyBold>ActiveConnection</legacyBold> property of the <legacyBold>Command</legacyBold> object to this object variable, ADO creates a new <legacyBold>Connection</legacyBold> object for each <legacyBold>Command</legacyBold> object, even if you use the same connection string.</para>
      <para>To execute a <legacyBold>Command</legacyBold>, call it by its <legacyLink xlink:href="cfd0e29c-8310-44ab-85c3-5761184b865d">Name</legacyLink> property on the associated <legacyBold>Connection</legacyBold> object. The <legacyBold>Command</legacyBold> must have its <legacyBold>ActiveConnection</legacyBold> property set to the <legacyBold>Connection</legacyBold> object. If the <legacyBold>Command</legacyBold> has parameters, pass their values as arguments to the method.</para>
      <para>If two or more <legacyBold>Command</legacyBold> objects are executed on the same connection and either <legacyBold>Command</legacyBold> object is a stored procedure with output parameters, an error occurs. To execute each <legacyBold>Command</legacyBold> object, use separate connections or disconnect all other <legacyBold>Command</legacyBold> objects from the connection.</para>
      <para>The <legacyBold>Parameters</legacyBold> collection is the default member of the <legacyBold>Command</legacyBold> object. As a result, the following two code statements are equivalent.</para>
      <code>objCmd.Parameters.Item(0)
objCmd(0)</code>
      <list class="bullet">
        <listItem>
          <para>The <legacyBold>Command</legacyBold> object is not safe for scripting.</para>
        </listItem>
      </list>
      <para>This section contains the following topic.  </para>
      <list class="bullet">
        <listItem>
          <para>
            <legacyLink xlink:href="0389f21c-06da-4090-9da1-28d912f888d7">Command Object Properties, Methods, and Events</legacyLink>           </para>
        </listItem>
      </list>
    </content>
  </languageReferenceRemarks>
  <relatedTopics>
<link xlink:href="ef6b1824-5b12-43db-89d7-8f3d13896d4d">Connection Object</link>
<link xlink:href="497cae10-3913-422a-9753-dcbb0a639b1b">Parameters Collection</link>
<link xlink:href="1d539aa8-ce0d-4418-ab03-8d0a3c1e9d82">Properties Collection</link>
<link xlink:href="e2581b47-b11e-4e1e-b96c-d39c77c5b48a">Appendix A: Providers</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>