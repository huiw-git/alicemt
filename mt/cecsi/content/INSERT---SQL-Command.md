---
title: INSERT - SQL Command
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9b648198-349f-46f6-b869-13d129945971
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# INSERT - SQL Command
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Appends a record to the end of a table that contains the specified field values.</para>
    <para>The Visual FoxPro ODBC Driver supports the native Visual FoxPro language syntax for this command. For driver-specific information, see the Remarks.</para>
  </introduction>
  <syntaxSection>
    <legacySyntax>
INSERT INTO <parameterReference>dbf_name</parameterReference> [(<parameterReference>fname1</parameterReference> [, <parameterReference>fname2</parameterReference>, ...])]
   VALUES (<parameterReference>eExpression1</parameterReference> [, <parameterReference>eExpression2</parameterReference>, ...])</legacySyntax>
  </syntaxSection>
  <section>
    <title>Arguments</title>
    <content>
      <definitionTable>
        <definedTerm>INSERT INTO <legacyItalic>dbf_name</legacyItalic></definedTerm>
        <definition>
          <para>Specifies the name of the table to which the new record is appended. <legacyItalic>dbf_name</legacyItalic> can include a path and can be a name expression.</para>
          <para>If the table you specify isn't open, it is opened exclusively in a new work area and the new record is appended to the table. The new work area isn't selected; the current work area remains selected.   </para>
          <para>If the table you specify is open, INSERT appends the new record to the table. If the table is open in a work area other than the current work area, it isn't selected after the record is appended; the current work area remains selected. </para>
        </definition>
        <definedTerm>[( <legacyItalic>fname1</legacyItalic>[, <legacyItalic>fname2</legacyItalic>[, ...]])] </definedTerm>
        <definition>
          <para>Specifies in the new record the names of the fields into which the values are inserted.</para>
        </definition>
        <definedTerm>VALUES ( <legacyItalic>eExpression1</legacyItalic>[, <legacyItalic>eExpression2</legacyItalic>[, ...]]) </definedTerm>
        <definition>
          <para>Specifies the field values inserted into the new record. If you omit the field names, you must specify the field values in the order defined by the table structure.</para>
        </definition>
      </definitionTable>
    </content>
  </section>
  <languageReferenceRemarks>
    <content>
      <para>The new record contains the data listed in the VALUES clause.</para>
    </content>
  </languageReferenceRemarks>
  <section>
    <title>Driver Remarks</title>
    <content>
      <para>When your application sends the ODBC SQL statement INSERT to the data source, the Visual FoxPro ODBC Driver converts the command into the Visual FoxProINSERT command without translation.</para>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="be2143ba-fc16-42c9-84f7-8985cd924860">CREATE TABLE - SQL</link>
<link xlink:href="2149c3ca-3a71-446d-8d53-3d056e2f301a">SELECT - SQL</link>
</relatedTopics>
</developerReferenceWithSyntaxDocument>