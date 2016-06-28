---
title: SET PATH Command
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: db488d1e-0963-4f45-8c76-a23b9bde9e9d
translation.priority.ht: 
  - en-gb
---
# SET PATH Command
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Specifies a path for file searches. For driver-specific information, see the Remarks.</para>
  </introduction>
  <syntaxSection>
    <legacySyntax>
SET PATH TO [<parameterReference>Path</parameterReference>]</legacySyntax>
  </syntaxSection>
  <section>
    <title>Arguments</title>
    <content>
      <definitionTable>
        <definedTerm>TO [ <legacyItalic>Path</legacyItalic>] </definedTerm>
        <definition>
          <para>Specifies the directories you want Visual FoxPro to search. Use commas or semicolons to separate the directories.</para>
        </definition>
      </definitionTable>
    </content>
  </section>
  <languageReferenceRemarks>
    <content>
      <para>SET PATH allows you to specify search paths for other Visual FoxPro programs that can be called within stored procedures. SET PATH will not change the path of the data source that you've specified for the connection.</para>
      <para>Issue SET PATH TO without <legacyItalic>Path</legacyItalic> to restore the path to the default directory or folder.</para>
    </content>
  </languageReferenceRemarks>
  <section>
    <title>Driver Remarks</title>
    <content>
      <para>If you issue SET PATH in a stored procedure, it will be ignored by the following functions and commands:  </para>
      <list class="bullet">
        <listItem>
          <para>Catalog functions such as <legacyLink xlink:href="69e2a038-5def-423f-91aa-8756e069dd2a">SQLTables</legacyLink> and <legacyLink xlink:href="b588a875-0153-43a0-9b76-f89e728cfa65">SQLColumns</legacyLink> will ignore the new path and continue to reference the path specified by the data source in <legacyLink xlink:href="0c4cb5a4-9729-4b2e-a0c6-52027b92e8fc">SQLPrepare</legacyLink> or <legacyLink xlink:href="5004060f-8510-4018-87a4-d41789e69d3e">SQLExecDirect</legacyLink>.</para>
        </listItem>
        <listItem>
          <para>Commands such as SELECT, INSERT, UPDATE, DELETE, and CREATE TABLE will ignore the new path and continue to reference the path specified by the data source in <legacyBold>SQLPrepare</legacyBold> or <legacyBold>SQLExecDirect</legacyBold>.</para>
        </listItem>
      </list>
      <para>If you issue SET PATH in a stored procedure and don't subsequently set the path back to its original state, other connections to the database will use the new path (because SET PATH is not scoped to data sessions).</para>
      <para>If you want to create, select, or update tables in a directory other than that specified by the data source, specify the full path of the file with your command.</para>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="de020197-7f53-4643-9cbf-b7887ba88de9">ODBC Visual FoxPro Setup Dialog Box</link>
<link xlink:href="b588a875-0153-43a0-9b76-f89e728cfa65">SQLColumns</link>
<link xlink:href="10492c8f-3a18-4971-9db8-879e878083b9">SQLDriverConnect</link>
<link xlink:href="69e2a038-5def-423f-91aa-8756e069dd2a">SQLTables</link>
</relatedTopics>
</developerReferenceWithSyntaxDocument>