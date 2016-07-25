---
title: "DELETE - SQL Command"
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0d5bd477-626f-4f22-a05a-f531d9f8c5e7
caps.latest.revision: 6
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# DELETE - SQL Command
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Marks records for deletion.</para>
    <para>The Visual FoxPro ODBC Driver supports the native Visual FoxPro language syntax for this command. For driver-specific information, see the Remarks.</para>
  </introduction>
  <syntaxSection>
    <legacySyntax>
DELETE FROM [<parameterReference>DatabaseName!</parameterReference>]<parameterReference>TableName</parameterReference>
   [WHERE <parameterReference>FilterCondition1</parameterReference> [AND | OR <parameterReference>FilterCondition2</parameterReference> ...]]</legacySyntax>
  </syntaxSection>
  <section>
    <title>Arguments</title>
    <content>
      <definitionTable>
        <definedTerm>FROM [ <legacyItalic>DatabaseName!</legacyItalic>] <legacyItalic>TableName</legacyItalic></definedTerm>
        <definition>
          <para>Specifies the table in which records are marked for deletion.</para>
          <para>
            <legacyItalic>DatabaseName!</legacyItalic> specifies the name of a database that contains the table if the containing database is not the database specified with the data source. You must include the name of a database that contains the table if the database is not the database specified with the data source. Include the exclamation point (!) delimiter after the database name and before the table name. </para>
        </definition>
        <definedTerm>WHERE <legacyItalic>FilterCondition1</legacyItalic>[AND | OR <legacyItalic>FilterCondition2</legacyItalic>...] </definedTerm>
        <definition>
          <para>Specifies that Visual FoxPro mark only certain records for deletion.</para>
          <para>
            <legacyItalic>FilterCondition</legacyItalic> specifies the criteria that records must meet to be marked for deletion. You can include as many filter conditions as you want, connecting them with the AND or OR operator. You can also use the NOT operator to reverse the value of a logical expression, or you can use <legacyBold>EMPTY</legacyBold>( ) to check for an empty field. </para>
        </definition>
      </definitionTable>
    </content>
  </section>
  <languageReferenceRemarks>
    <content>
      <para>If SET DELETED is set to ON, records marked for deletion are ignored by all commands that include a scope.</para>
      <para>DELETE - SQL uses record locking when marking multiple records for deletion in tables opened for shared access. This reduces record contention in multiuser situations but can decrease performance. For maximum performance, open the table for exclusive use.</para>
    </content>
  </languageReferenceRemarks>
  <section>
    <title>Driver Remarks</title>
    <content>
      <para>When your application sends the ODBC SQL statement DELETE to the data source, the Visual FoxPro ODBC Driver converts the command into the Visual FoxPro DELETE command without translation.</para>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="6b5e0086-156d-471d-8e7f-6c5fa9686cd5">SET DELETED</link>
</relatedTopics>
</developerReferenceWithSyntaxDocument>