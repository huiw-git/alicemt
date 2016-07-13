---
title: UPDATE - SQL Command
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ff1e0331-c060-4304-b280-039725b45f63
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# UPDATE - SQL Command
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Updates records in a table with new values.</para>
    <para>The Visual FoxPro ODBC Driver supports the native Visual FoxPro language syntax for this command. For driver-specific information, see <legacyBold>Driver Remarks</legacyBold>.</para>
  </introduction>
  <syntaxSection>
    <legacySyntax>
UPDATE [<parameterReference>DatabaseName1!</parameterReference>]<parameterReference>TableName1</parameterReference>
SET <parameterReference>Column_Name1</parameterReference> = <parameterReference>eExpression1</parameterReference>
   [, <parameterReference>Column_Name2</parameterReference> = <parameterReference>eExpression2</parameterReference> ...]
   WHERE <parameterReference>FilterCondition1</parameterReference> [AND | OR <parameterReference>FilterCondition2</parameterReference> ...]</legacySyntax>
  </syntaxSection>
  <section>
    <title>Arguments</title>
    <content>
      <definitionTable>
        <definedTerm>UPDATE [ <legacyItalic>DatabaseName1!</legacyItalic>] <legacyItalic>TableName1</legacyItalic></definedTerm>
        <definition>
          <para>Specifies the table in which records are updated with new values.</para>
          <para>             <legacyItalic>DatabaseName1!</legacyItalic> specifies the name of a database other than the database specified with the data source containing the table. You must include the name of the database containing the table if the database is not the current one. Include the exclamation point (!) delimiter after the database name and before the table name. </para>
        </definition>
        <definedTerm>SET <legacyItalic>Column_Name1</legacyItalic>= <legacyItalic>eExpression1</legacyItalic>[, <legacyItalic>Column_Name2</legacyItalic>= <legacyItalic>eExpression2</legacyItalic></definedTerm>
        <definition>
          <para>Specifies the columns that are updated and their new values. If you omit the WHERE clause, every row in the column is updated with the same value.</para>
        </definition>
        <definedTerm>WHERE <legacyItalic>FilterCondition1</legacyItalic>[AND | OR <legacyItalic>FilterCondition2</legacyItalic>...] </definedTerm>
        <definition>
          <para>Specifies the records that are updated with new values.</para>
          <para>             <legacyItalic>FilterCondition</legacyItalic> specifies the criteria that records must meet to be updated with new values. You can include as many filter conditions as you like, connecting them with the AND or OR operator. You can also use the NOT operator to reverse the value of a logical expression, or you can use <legacyBold>EMPTY</legacyBold>( ) to check for an empty field. </para>
        </definition>
      </definitionTable>
    </content>
  </section>
  <languageReferenceRemarks>
    <content>
      <para>UPDATE - SQL can update only records in a single table.</para>
      <para>Unlike REPLACE, UPDATE - SQL uses record locking when updating multiple records in tables opened for shared access. This reduces record contention in multiuser situations but can reduce performance. For maximum performance, open the table for exclusive use or use <legacyBold>FLOCK</legacyBold>( ) to lock the table.</para>
    </content>
  </languageReferenceRemarks>
  <section>
    <title>Driver Remarks</title>
    <content>
      <para>When your application sends the ODBC SQL statement UPDATE to the data source, the Visual FoxPro ODBC Driver converts the command into the Visual FoxProUPDATE command without translation.</para>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="0d5bd477-626f-4f22-a05a-f531d9f8c5e7">DELETE - SQL</link>
<link xlink:href="9b648198-349f-46f6-b869-13d129945971">INSERT - SQL</link>
</relatedTopics>
</developerReferenceWithSyntaxDocument>