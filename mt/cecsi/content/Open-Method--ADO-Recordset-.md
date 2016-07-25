---
title: "Open Method (ADO Recordset)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: 3236749c-4b71-4235-89e2-ccdfaaa9319d
caps.latest.revision: 14
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
# Open Method (ADO Recordset)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Opens a cursor on a <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink> object.</para>
  </introduction>
  <syntaxSection>
    <legacySyntax>
<parameterReference>recordset</parameterReference><legacyBold>.Open</legacyBold> <parameterReference>Source</parameterReference><legacyBold>, </legacyBold><parameterReference>ActiveConnection</parameterReference><legacyBold>, </legacyBold><parameterReference>CursorType</parameterReference><legacyBold>, </legacyBold><parameterReference>LockType</parameterReference><legacyBold>, </legacyBold><parameterReference>Options</parameterReference></legacySyntax>
  </syntaxSection>
  <parameters>
    <content>
      <definitionTable>
        <definedTerm>
          <parameterReference>Source </parameterReference>
        </definedTerm>
        <definition>
          <para>Optional. A <languageKeyword>Variant</languageKeyword> that evaluates to a valid <legacyLink xlink:href="a02c22fb-542d-465e-a629-30fd59dcbebf">Command</legacyLink> object, an SQL statement, a table name, a stored procedure call, a URL, or the name of a file or <legacyLink xlink:href="0514531f-009d-4519-abc3-d727014a39f1">Stream</legacyLink> object containing a persistently stored <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink>.</para>
        </definition>
        <definedTerm>
          <parameterReference>ActiveConnection </parameterReference>
        </definedTerm>
        <definition>
          <para>Optional. Either a <languageKeyword>Variant</languageKeyword> that evaluates to a valid <legacyLink xlink:href="ef6b1824-5b12-43db-89d7-8f3d13896d4d">Connection</legacyLink> object variable name, or a <languageKeyword>String</languageKeyword> that contains <legacyLink xlink:href="3be75b75-4d36-4479-ab64-9a456869252a">ConnectionString</legacyLink> parameters.</para>
        </definition>
        <definedTerm>
          <parameterReference>CursorType </parameterReference>
        </definedTerm>
        <definition>
          <para>Optional. A <legacyLink xlink:href="ffc6e245-4471-42ae-84dd-e85bddfce983">CursorTypeEnum</legacyLink> value that determines the type of cursor that the provider should use when opening the <unmanagedCodeEntityReference>Recordset</unmanagedCodeEntityReference>. The default value is <legacyBold>adOpenForwardOnly</legacyBold>.</para>
        </definition>
        <definedTerm>
          <parameterReference>LockType </parameterReference>
        </definedTerm>
        <definition>
          <para>Optional. A <legacyLink xlink:href="d2894eaf-4450-4ace-aa51-c8b875fd3010">LockTypeEnum</legacyLink> value that determines what type of locking (concurrency) the provider should use when opening the <unmanagedCodeEntityReference>Recordset</unmanagedCodeEntityReference>. The default value is <legacyBold>adLockReadOnly</legacyBold>.</para>
        </definition>
        <definedTerm>
          <parameterReference>Options </parameterReference>
        </definedTerm>
        <definition>
          <para>Optional. A <languageKeyword>Long</languageKeyword> value that indicates how the provider should evaluate the <parameterReference>Source</parameterReference> argument if it represents something other than a <unmanagedCodeEntityReference>Command</unmanagedCodeEntityReference> object, or that the <unmanagedCodeEntityReference>Recordset</unmanagedCodeEntityReference> should be restored from a file where it was previously saved. Can be one or more <legacyLink xlink:href="4b1feb9c-a855-40fe-a906-efe688687e9f">CommandTypeEnum</legacyLink> or <legacyLink xlink:href="68bfa83a-5df4-4bef-8736-0f88ae8c29ea">ExecuteOptionEnum</legacyLink> values, which can be combined with a bitwise OR operator.</para>
        </definition>
      </definitionTable>
      <alert class="note">
        <para>If you open a <unmanagedCodeEntityReference>Recordset</unmanagedCodeEntityReference> from a <unmanagedCodeEntityReference>Stream</unmanagedCodeEntityReference> containing a persisted <unmanagedCodeEntityReference>Recordset</unmanagedCodeEntityReference>, using an <legacyLink xlink:href="68bfa83a-5df4-4bef-8736-0f88ae8c29ea">ExecuteOptionEnum</legacyLink> value of <legacyBold>adAsyncFetchNonBlocking</legacyBold> will have no effect; the fetch will be synchronous and blocking. </para>
      </alert>
      <alert class="note">
        <para>The <legacyBold>ExecuteOpenEnum</legacyBold> values of <legacyBold>adExecuteNoRecords</legacyBold> or <legacyBold>adExecuteStream</legacyBold> should not be used with <unmanagedCodeEntityReference>Open</unmanagedCodeEntityReference>.</para>
      </alert>
    </content>
  </parameters>
  <languageReferenceRemarks>
    <content>
      <para>The default cursor for an ADO <unmanagedCodeEntityReference>Recordset</unmanagedCodeEntityReference> is a forward-only, read-only cursor located on the server.</para>
      <para>Using the <unmanagedCodeEntityReference>Open</unmanagedCodeEntityReference> method on a <unmanagedCodeEntityReference>Recordset</unmanagedCodeEntityReference> object opens a cursor that represents records from a base table, the results of a query, or a previously saved <unmanagedCodeEntityReference>Recordset</unmanagedCodeEntityReference>.</para>
      <para>Use the optional <parameterReference>Source</parameterReference> argument to specify a data source using one of the following: a <unmanagedCodeEntityReference>Command</unmanagedCodeEntityReference> object variable, an SQL statement, a stored procedure, a table name, a URL, or a complete file path name. If <parameterReference>Source</parameterReference> is a file path name, it can be a full path ("c:\dir\file.rst"), a relative path ("..\file.rst"), or a URL ("http://files/file.rst").</para>
      <para>It is not a good idea to use the <parameterReference>Source</parameterReference> argument of the <unmanagedCodeEntityReference>Open</unmanagedCodeEntityReference> method to perform an action query that does not return records because there is no easy way to determine whether the call succeeded. The <unmanagedCodeEntityReference>Recordset</unmanagedCodeEntityReference> returned by such a query will be closed. To perform a query that does not return records, such as a SQL INSERT statement, call the <legacyLink xlink:href="f84a5ff3-0528-4ad7-9bea-9a15103378dd">Execute</legacyLink> method of a <unmanagedCodeEntityReference>Command</unmanagedCodeEntityReference> object or the <legacyLink xlink:href="03c69320-96b2-4d85-8d49-a13b13e31578">Execute</legacyLink> method of a <legacyLink xlink:href="ef6b1824-5b12-43db-89d7-8f3d13896d4d">Connection</legacyLink> object instead.</para>
      <para>The <parameterReference>ActiveConnection</parameterReference> argument corresponds to the <legacyLink xlink:href="52d0a96c-14fb-4ad9-b004-4d821bc0a6db">ActiveConnection</legacyLink> property and specifies in which connection to open the <unmanagedCodeEntityReference>Recordset</unmanagedCodeEntityReference> object. If you pass a connection definition for this argument, ADO opens a new connection using the specified parameters. After you open the <unmanagedCodeEntityReference>Recordset</unmanagedCodeEntityReference> with a client-side cursor by setting the <legacyLink xlink:href="39c8d86e-7ee9-4182-be5e-aad5ce952f84">CursorLocation</legacyLink> property to <legacyBold>adUseClient</legacyBold>, you can change the value of this property to send updates to another provider. Or you can set this property to <legacyBold>Nothing</legacyBold> (in Microsoft Visual Basic) or NULL to disconnect the <unmanagedCodeEntityReference>Recordset</unmanagedCodeEntityReference> from any provider. Changing <parameterReference>ActiveConnection</parameterReference> for a server-side cursor generates an error, however.</para>
      <para>For the other arguments that correspond directly to properties of a <unmanagedCodeEntityReference>Recordset</unmanagedCodeEntityReference> object (<parameterReference>Source</parameterReference>, <parameterReference>CursorType</parameterReference>, and <parameterReference>LockType</parameterReference>), the relationship of the arguments to the properties is as follows:  </para>
      <list class="bullet">
        <listItem>
          <para>The property is read/write before the <unmanagedCodeEntityReference>Recordset</unmanagedCodeEntityReference> object is opened.</para>
        </listItem>
        <listItem>
          <para>The property settings are used unless you pass the corresponding arguments when executing the <unmanagedCodeEntityReference>Open</unmanagedCodeEntityReference> method. If you pass an argument, it overrides the corresponding property setting, and the property setting is updated with the argument value.</para>
        </listItem>
        <listItem>
          <para>After you open the <unmanagedCodeEntityReference>Recordset</unmanagedCodeEntityReference> object, these properties become read-only.</para>
        </listItem>
      </list>
      <alert class="note">
        <para>The <unmanagedCodeEntityReference>ActiveConnection</unmanagedCodeEntityReference> property is read-only for <unmanagedCodeEntityReference>Recordset</unmanagedCodeEntityReference> objects whose <legacyLink xlink:href="a05ba2c9-2821-4343-8607-4de9b764ec91">Source</legacyLink> property is set to a valid <unmanagedCodeEntityReference>Command</unmanagedCodeEntityReference> object, even if the <unmanagedCodeEntityReference>Recordset</unmanagedCodeEntityReference> object is not open.</para>
      </alert>
      <para>If you pass a <unmanagedCodeEntityReference>Command</unmanagedCodeEntityReference> object in the <parameterReference>Source</parameterReference> argument and also pass an <parameterReference>ActiveConnection</parameterReference> argument, an error occurs. The <unmanagedCodeEntityReference>ActiveConnection</unmanagedCodeEntityReference> property of the <unmanagedCodeEntityReference>Command</unmanagedCodeEntityReference> object must already be set to a valid <unmanagedCodeEntityReference>Connection</unmanagedCodeEntityReference> object or connection string.</para>
      <para>If you pass something other than a <unmanagedCodeEntityReference>Command</unmanagedCodeEntityReference> object in the <parameterReference>Source</parameterReference> argument, you can use the <parameterReference>Options</parameterReference> argument to optimize evaluation of the <parameterReference>Source</parameterReference> argument. If the <parameterReference>Options</parameterReference> argument is not defined, you may experience diminished performance because ADO must make calls to the provider to determine if the argument is an SQL statement, a stored procedure, a URL, or a table name. If you know what <parameterReference>Source</parameterReference> type you are using, setting the <parameterReference>Options</parameterReference> argument instructs ADO to jump directly to the relevant code. If the <parameterReference>Options</parameterReference> argument does not match the <parameterReference>Source</parameterReference> type, an error occurs.</para>
      <para>If you pass a <unmanagedCodeEntityReference>Stream</unmanagedCodeEntityReference> object in the <parameterReference>Source</parameterReference> argument, you should not pass information into the other arguments. Doing so will generate an error. The <unmanagedCodeEntityReference>ActiveConnection</unmanagedCodeEntityReference> information is not retained when a <unmanagedCodeEntityReference>Recordset</unmanagedCodeEntityReference> is opened from a <unmanagedCodeEntityReference>Stream</unmanagedCodeEntityReference>.</para>
      <para>The default for the <parameterReference>Options</parameterReference> argument is <legacyBold>adCmdFile</legacyBold> if no connection is associated with the <unmanagedCodeEntityReference>Recordset</unmanagedCodeEntityReference>. This will typically be the case for persistently stored <unmanagedCodeEntityReference>Recordset</unmanagedCodeEntityReference> objects.</para>
      <para>If the data source returns no records, the provider sets both the <legacyLink xlink:href="36c31ab2-f3b6-4281-89b6-db7e04e38fd2">BOF</legacyLink> and <legacyLink xlink:href="36c31ab2-f3b6-4281-89b6-db7e04e38fd2">EOF</legacyLink> properties to <languageKeyword>True</languageKeyword>, and the current record position is undefined. You can still add new data to this empty <unmanagedCodeEntityReference>Recordset</unmanagedCodeEntityReference> object if the cursor type allows it.</para>
      <para>When you have concluded your operations over an open <unmanagedCodeEntityReference>Recordset</unmanagedCodeEntityReference> object, use the <legacyLink xlink:href="3cdf27d1-a180-4cff-8e42-95dec5fb1b55">Close</legacyLink> method to free any associated system resources. Closing an object does not remove it from memory; you can change its property settings and use the <unmanagedCodeEntityReference>Open</unmanagedCodeEntityReference> method to open it again later. To completely eliminate an object from memory, set the object variable to <parameterReference>Nothing</parameterReference>.</para>
      <para>Before the <unmanagedCodeEntityReference>ActiveConnection</unmanagedCodeEntityReference> property is set, call <unmanagedCodeEntityReference>Open</unmanagedCodeEntityReference> with no operands to create an instance of a <unmanagedCodeEntityReference>Recordset</unmanagedCodeEntityReference> created by appending fields to the <unmanagedCodeEntityReference>Recordset</unmanagedCodeEntityReference> <legacyLink xlink:href="7c371474-b88f-4730-afa5-44163a0488d5">Fields</legacyLink> collection.</para>
      <para>If you have set the <legacyLink xlink:href="39c8d86e-7ee9-4182-be5e-aad5ce952f84">CursorLocation</legacyLink> property to <legacyBold>adUseClient</legacyBold>, you can retrieve rows asynchronously in one of two ways. The recommended method is to set <parameterReference>Options</parameterReference> to <legacyBold>adAsyncFetch</legacyBold>. Alternatively, you can use the "Asynchronous Rowset Processing" dynamic property in the <legacyLink xlink:href="1d539aa8-ce0d-4418-ab03-8d0a3c1e9d82">Properties</legacyLink> collection, but related retrieved events can be lost if you do not set the <parameterReference>Options</parameterReference> parameter to <legacyBold>adAsyncFetch</legacyBold>.</para>
      <alert class="note">
        <para>Background fetching in the MS Remote provider is supported only through the <unmanagedCodeEntityReference>Open</unmanagedCodeEntityReference> method's <parameterReference>Options</parameterReference> parameter.</para>
      </alert>
      <alert class="note">
        <para>URLs using the http scheme will automatically invoke the <legacyLink xlink:href="66a208d9-b580-4655-a41e-1d36e5b5bfca">Microsoft OLE DB Provider for Internet Publishing</legacyLink>. For more information, see <legacyLink xlink:href="6a34a7ef-50cc-4c3d-82f7-106b9a8f3caf">Absolute and Relative URLs</legacyLink>.</para>
      </alert>
      <para>Certain combinations of <legacyLink xlink:href="4b1feb9c-a855-40fe-a906-efe688687e9f">CommandTypeEnum</legacyLink> and <legacyLink xlink:href="68bfa83a-5df4-4bef-8736-0f88ae8c29ea">ExecuteOptionEnum</legacyLink> values are not valid. For information about which options cannot be combined, see the topics for the <legacyLink xlink:href="68bfa83a-5df4-4bef-8736-0f88ae8c29ea">ExecuteOptionEnum</legacyLink>, and <legacyLink xlink:href="4b1feb9c-a855-40fe-a906-efe688687e9f">CommandTypeEnum</legacyLink>.</para>
    </content>
  </languageReferenceRemarks>
  <section>
    <title>Applies To</title>
    <content>
      <para>
        <link xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</link>
      </para>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="1311d561-0e86-40f5-8cbc-ad8f13e626d1">Visual Basic Example</link>
<link xlink:href="66eca011-e258-4d8f-bd67-e017bcf0871b">VBScript Example</link>
<link xlink:href="f74a81fd-cbcc-4143-b9f8-774c88dd4fad">Visual C++ Example</link>
<link xlink:href="0b7dd9f8-4751-48fb-a75d-c6f75d80d928">Visual J++ Example</link>
<link xlink:href="ddccdf58-9c57-4c9b-8b7f-0cf193f955fb">Visual Basic Example</link>
<link xlink:href="663defab-5545-4973-9036-24d5882c9737">Open Method (ADO Connection)</link>
<link xlink:href="ab79a623-88a9-40b6-a017-a658bf19b778">Open Method (ADO Record)</link>
<link xlink:href="d26f48fb-904e-4932-a245-3b4332ca1600">Open Method (ADO Stream)</link>
<link xlink:href="850cf3ce-f18f-4e7c-8597-96c1dc504866">OpenSchema Method</link>
<link xlink:href="ed3d9678-5c28-4e61-8bb3-7dfb66d99cf5">Save Method</link>
</relatedTopics>
</developerReferenceWithSyntaxDocument>