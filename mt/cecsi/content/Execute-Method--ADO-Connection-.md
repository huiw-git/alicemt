---
title: "Execute Method (ADO Connection)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
apitype: COM
ms.assetid: 03c69320-96b2-4d85-8d49-a13b13e31578
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
# Execute Method (ADO Connection)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Executes the specified query, SQL statement, stored procedure, or provider-specific text.</para>
  </introduction>
  <syntaxSection>
    <legacySyntax>
<legacyBold>Set recordset = connection.Execute (CommandText, RecordsAffected, Options)</legacyBold>
<legacyBold>Set recordset = connection.Execute (CommandText, RecordsAffected, Options)</legacyBold></legacySyntax>
  </syntaxSection>
  <returnValue>
    <content>
      <para>Returns a <link xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset Object_ADO</link> object reference.</para>
    </content>
  </returnValue>
  <parameters>
    <content>
      <definitionTable>
        <definedTerm> <legacyItalic>CommandText</legacyItalic> </definedTerm>
        <definition>
          <para>A <legacyBold>String</legacyBold> value that contains the SQL statement, stored procedure, a URL, or provider-specific text to execute. <legacyBold>Optionally</legacyBold>, table names can be used but only if the provider is SQL aware. For example if a table name of "Customers" is used, ADO will automatically prepend the standard SQL Select syntax to form and pass "SELECT * FROM Customers" as a <token>tsql</token> statement to the provider.</para>
        </definition>
        <definedTerm> <legacyItalic>RecordsAffected</legacyItalic> </definedTerm>
        <definition>
          <para>Optional. A <legacyBold>Long</legacyBold> variable to which the provider returns the number of records that the operation affected.</para>
        </definition>
        <definedTerm> <legacyItalic>Options</legacyItalic> </definedTerm>
        <definition>
          <para>Optional. A <legacyBold>Long</legacyBold> value that indicates how the provider should evaluate the CommandText argument. Can be a bitmask of one or more <link xlink:href="4b1feb9c-a855-40fe-a906-efe688687e9f">CommandTypeEnum</link> or <link xlink:href="68bfa83a-5df4-4bef-8736-0f88ae8c29ea">ExecuteOptionEnum</link> values.</para>
        </definition>
      </definitionTable>
      <para>
        <embeddedLabel>Note</embeddedLabel>   Use the <legacyBold>ExecuteOptionEnum</legacyBold> value <legacyBold>adExecuteNoRecords</legacyBold> to improve performance by minimizing internal processing and for applications that you are porting from Visual Basic 6.0.</para>
      <para>Do not use <legacyBold>adExecuteStream</legacyBold> with the <legacyBold>Execute</legacyBold> method of a <legacyBold>Connection</legacyBold> object.</para>
      <para>Do not use the CommandTypeEnum values of adCmdFile or adCmdTableDirect with Execute. These values can only be used as options with the <link xlink:href="3236749c-4b71-4235-89e2-ccdfaaa9319d">Open Method (ADO Recordset)</link> and <link xlink:href="d81ab76f-1aa8-4ccf-92ec-b65254dc3ea1">Requery Method</link> methods of a <legacyBold>Recordset</legacyBold>.</para>
    </content>
  </parameters>
  <languageReferenceRemarks>
    <content>
      <para>Using the <legacyBold>Execute</legacyBold> method on a <link xlink:href="ef6b1824-5b12-43db-89d7-8f3d13896d4d">Connection Object_ADO</link> object executes whatever query you pass to the method in the CommandText argument on the specified connection. If the CommandText argument specifies a row-returning query, any results that the execution generates are stored in a new <legacyBold>Recordset</legacyBold> object. If the command is not intended to return results (for example, an SQL UPDATE query) the provider returns <legacyBold>Nothing</legacyBold> as long as the option <legacyBold>adExecuteNoRecords</legacyBold> is specified; otherwise Execute returns a closed <legacyBold>Recordset</legacyBold>.</para>
      <para>The returned <legacyBold>Recordset</legacyBold> object is always a read-only, forward-only cursor. If you need a <legacyBold>Recordset</legacyBold> object with more functionality, first create a <legacyBold>Recordset</legacyBold> object with the desired property settings, then use the <legacyBold>Recordset</legacyBold> object's <link xlink:href="3236749c-4b71-4235-89e2-ccdfaaa9319d">Open Method (ADO Recordset)</link> method to execute the query and return the desired cursor type.</para>
      <para>The contents of the <legacyItalic>CommandText</legacyItalic> argument are specific to the provider and can be standard SQL syntax or any special command format that the provider supports.</para>
      <para>An ExecuteComplete event will be issued when this operation concludes.</para>
      <alert class="note">
        <para>URLs using the http scheme will automatically invoke the <link xlink:href="66a208d9-b580-4655-a41e-1d36e5b5bfca">Microsoft OLE DB Provider for Internet Publishing</link>. For more information, see <link xlink:href="6a34a7ef-50cc-4c3d-82f7-106b9a8f3caf">Absolute and Relative URLs</link>.</para>
      </alert>
    </content>
  </languageReferenceRemarks>
  <section>
    <title>Applies To</title>
    <content>
      <para>
        <link xlink:href="ef6b1824-5b12-43db-89d7-8f3d13896d4d">Connection Object</link>
      </para>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithSyntaxDocument>