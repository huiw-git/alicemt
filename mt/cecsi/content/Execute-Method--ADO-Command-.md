---
title: "Execute Method (ADO Command)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: f84a5ff3-0528-4ad7-9bea-9a15103378dd
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
# Execute Method (ADO Command)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Executes the query, SQL statement, or stored procedure specified in the <legacyLink xlink:href="4dd7e82a-8da5-4a4e-b439-11a29286fa0e">CommandText</legacyLink> or <legacyLink xlink:href="f78f61b6-87e0-48dc-961e-83d0e20da58e">CommandStream</legacyLink> property of the <legacyLink xlink:href="a02c22fb-542d-465e-a629-30fd59dcbebf">Command object</legacyLink>.</para>
  </introduction>
  <syntaxSection>
    <legacySyntax>
<legacyBold>Set</legacyBold> <parameterReference>recordset</parameterReference> = <parameterReference>command</parameterReference>.<legacyBold>Execute( </legacyBold><parameterReference>RecordsAffected</parameterReference><legacyBold>, </legacyBold><parameterReference>Parameters</parameterReference><legacyBold>, </legacyBold><parameterReference>Options </parameterReference><legacyBold>)</legacyBold></legacySyntax>
  </syntaxSection>
  <returnValue>
    <content>
      <para>Returns a <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink> object reference, a stream, or <legacyBold>Nothing</legacyBold>.</para>
    </content>
  </returnValue>
  <parameters>
    <content>
      <definitionTable>
        <definedTerm> <legacyItalic>RecordsAffected</legacyItalic> </definedTerm>
        <definition>
          <para>Optional. A <legacyBold>Long</legacyBold> variable to which the provider returns the number of records that the operation affected. The <legacyItalic>RecordsAffected</legacyItalic> parameter applies only for action queries or stored procedures. <legacyItalic>RecordsAffected</legacyItalic> does not return the number of records returned by a result-returning query or stored procedure. To obtain this information, use the <legacyLink xlink:href="834f0121-394a-44d4-ad7d-999b43a6fe63">RecordCount</legacyLink> property. The <legacyBold>Execute</legacyBold> method will not return the correct information when used with <legacyBold>adAsyncExecute</legacyBold>, simply because when a command is executed asynchronously, the number of records affected may not yet be known at the time the method returns.</para>
        </definition>
        <definedTerm> <legacyItalic>Parameters</legacyItalic> </definedTerm>
        <definition>
          <para>Optional. A <languageKeyword>Variant</languageKeyword> array of parameter values used in conjunction with the input string or stream specified in <legacyBold>CommandText</legacyBold> or <legacyBold>CommandStream</legacyBold>. (Output parameters will not return correct values when passed in this argument.)</para>
        </definition>
        <definedTerm> <legacyItalic>Options</legacyItalic> </definedTerm>
        <definition>
          <para>Optional. A <languageKeyword>Long</languageKeyword> value that indicates how the provider should evaluate the <legacyLink xlink:href="4dd7e82a-8da5-4a4e-b439-11a29286fa0e">CommandText</legacyLink> or the <legacyLink xlink:href="f78f61b6-87e0-48dc-961e-83d0e20da58e">CommandStream</legacyLink> property of the <legacyLink xlink:href="a02c22fb-542d-465e-a629-30fd59dcbebf">Command</legacyLink> object. Can be a bitmask value made using <legacyLink xlink:href="4b1feb9c-a855-40fe-a906-efe688687e9f">CommandTypeEnum</legacyLink> and/or <legacyLink xlink:href="68bfa83a-5df4-4bef-8736-0f88ae8c29ea">ExecuteOptionEnum</legacyLink> values. For example, you could use <legacyBold>adCmdText</legacyBold> and <legacyBold>adExecuteNoRecords</legacyBold> in combination if you want to have ADO evaluate the value of the <legacyBold>CommandText</legacyBold> property as text, and indicate that the command should discard and not return any records that might be generated when the command text executes.</para>
        </definition>
      </definitionTable>
      <alert class="note">
        <para>Use the <legacyBold>ExecuteOptionEnum</legacyBold> value <legacyBold>adExecuteNoRecords</legacyBold> to improve performance by minimizing internal processing. If <legacyBold>adExecuteStream</legacyBold> was specified, the options <legacyBold>adAsyncFetch</legacyBold> and <legacyBold>adAsynchFetchNonBlocking</legacyBold> are ignored. Do not use the <legacyBold>CommandTypeEnum</legacyBold> values of <legacyBold>adCmdFile</legacyBold> or <legacyBold>adCmdTableDirect</legacyBold> with <legacyBold>Execute</legacyBold>. These values can only be used as options with the <legacyLink xlink:href="3236749c-4b71-4235-89e2-ccdfaaa9319d">Open</legacyLink> and <legacyLink xlink:href="d81ab76f-1aa8-4ccf-92ec-b65254dc3ea1">Requery</legacyLink> methods of a <legacyBold>Recordset</legacyBold>.</para>
      </alert>
    </content>
  </parameters>
  <languageReferenceRemarks>
    <content>
      <para>Using the <legacyBold>Execute</legacyBold> method on a <legacyBold>Command</legacyBold> object executes the query specified in the <legacyBold>CommandText</legacyBold> property or <legacyBold>CommandStream</legacyBold> property of the object.</para>
      <para>Results are returned in a <legacyBold>Recordset</legacyBold> (by default) or as a stream of binary information. To obtain a binary stream, specify <legacyBold>adExecuteStream</legacyBold> in <legacyItalic>Options</legacyItalic>, then supply a stream by setting <legacyBold>Command.Properties("Output Stream")</legacyBold>. An ADO <legacyBold>Stream</legacyBold> object can be specified to receive the results, or another stream object such as the IIS Response object can be specified. If no stream was specified before calling <legacyBold>Execute</legacyBold> with <legacyBold>adExecuteStream</legacyBold>, an error occurs. The position of the stream on return from <legacyBold>Execute</legacyBold> is provider specific.</para>
      <para>If the command is not intended to return results (for example, an SQL UPDATE query) the provider returns <legacyBold>Nothing</legacyBold> as long as the option <legacyBold>adExecuteNoRecords</legacyBold> is specified; otherwise Execute returns a closed <legacyBold>Recordset</legacyBold>. Some application languages allow you to ignore this return value if no <legacyBold>Recordset</legacyBold> is desired.</para>
      <para>
        <legacyBold>Execute</legacyBold> raises an error if the user specifies a value for <legacyBold>CommandStream</legacyBold> when the <legacyBold>CommandType</legacyBold> is <legacyBold>adCmdStoredProc</legacyBold>, <legacyBold>adCmdTable</legacyBold>, or <legacyBold>adCmdTableDirect</legacyBold>.</para>
      <para>If the query has parameters, the current values for the <legacyBold>Command</legacyBold> object's parameters are used unless you override these with parameter values passed with the <legacyBold>Execute</legacyBold> call. You can override a subset of the parameters by omitting new values for some of the parameters when calling the <legacyBold>Execute</legacyBold> method. The order in which you specify the parameters is the same order in which the method passes them. For example, if there were four (or more) parameters and you wanted to pass new values for only the first and fourth parameters, you would pass <codeInline>Array(var1,,,var4)</codeInline> as the <legacyItalic>Parameters</legacyItalic> argument.</para>
      <alert class="note">
        <para>Output parameters will not return correct values when passed in the <legacyItalic>Parameters</legacyItalic> argument.</para>
      </alert>
      <para>An <legacyLink xlink:href="62470d42-e511-494c-bec4-ad4591734b7b">ExecuteComplete</legacyLink> event will be issued when this operation concludes.</para>
      <alert class="note">
        <para>When issuing commands containing URLs, those using the http scheme will automatically invoke the <legacyLink xlink:href="66a208d9-b580-4655-a41e-1d36e5b5bfca">Microsoft OLE DB Provider for Internet Publishing</legacyLink>. For more information, see <legacyLink xlink:href="6a34a7ef-50cc-4c3d-82f7-106b9a8f3caf">Absolute and Relative URLs</legacyLink>.</para>
      </alert>
    </content>
  </languageReferenceRemarks>
  <section>
    <title>Applies To</title>
    <content>
      <para>
        <link xlink:href="a02c22fb-542d-465e-a629-30fd59dcbebf">Command Object</link>
      </para>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="ed5e1b60-3769-4b26-a253-1d721e37941d">Visual Basic Example</link>
<link xlink:href="3a7bbf07-2fca-4892-95f4-eec93f2d5e91">VBScript Example</link>
<link xlink:href="ada6acc1-82eb-4cfa-8f2f-617a916ffd8d">Visual C++ Example</link>
<link xlink:href="3c92cb19-c13b-4bb3-b4cd-75dc8f42057c">Visual J++ Example</link>
<link xlink:href="f78f61b6-87e0-48dc-961e-83d0e20da58e">CommandStream Property</link>
<link xlink:href="4dd7e82a-8da5-4a4e-b439-11a29286fa0e">CommandText Property</link>
<link xlink:href="4b1feb9c-a855-40fe-a906-efe688687e9f">CommandTypeEnum</link>
<link xlink:href="03c69320-96b2-4d85-8d49-a13b13e31578">Execute Method (ADO Connection)</link>
<link xlink:href="62470d42-e511-494c-bec4-ad4591734b7b">ExecuteComplete Event</link>
</relatedTopics>
</developerReferenceWithSyntaxDocument>