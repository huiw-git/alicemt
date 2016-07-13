---
title: DROP TABLE Command
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: bc50459b-8861-4889-84a9-129ae9065aa8
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# DROP TABLE Command
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Removes a table from the database specified with the data source and deletes it from disk.</para>
    <para>The Visual FoxPro ODBC Driver supports the native Visual FoxPro language syntax for this command. For driver-specific information, see the Remarks.</para>
  </introduction>
  <syntaxSection>
    <legacySyntax>
DROP TABLE <parameterReference>TableName</parameterReference> | <parameterReference>FileName</parameterReference> | ?</legacySyntax>
  </syntaxSection>
  <section>
    <title>Settings</title>
    <content>
      <definitionTable>
        <definedTerm> <legacyItalic>TableName</legacyItalic> </definedTerm>
        <definition>
          <para>Specifies the table to remove from the database specified with the data source and to delete from disk.</para>
        </definition>
        <definedTerm> <legacyItalic>FileName</legacyItalic> </definedTerm>
        <definition>
          <para>Specifies a free table to delete from disk.</para>
        </definition>
        <definedTerm>? </definedTerm>
        <definition>
          <para>Displays the Remove dialog from which you can choose a table to remove from the database specified with the data source and to delete from disk.</para>
        </definition>
      </definitionTable>
    </content>
  </section>
  <languageReferenceRemarks>
    <content>
      <para>When DROP TABLE is issued, all primary indexes, default values, and validation rules associated with the table are also removed. DROP TABLE also affects other tables in the database specified with the data source if those tables have rules or relations associated with the table being removed. The rules and relations are no longer valid when the table is removed from the database.</para>
    </content>
  </languageReferenceRemarks>
  <section>
    <title>Driver Remarks</title>
    <content>
      <para>When your application sends the ODBC SQL statement DROP TABLE to the data source, the Visual FoxPro ODBC Driver converts the command into the Visual FoxProDROP TABLE command using the syntax shown in the following table.</para>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>ODBC syntax</para>
            </TD>
            <TD>
              <para>Data source</para>
            </TD>
            <TD>
              <para>Visual FoxPro syntax</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>DROP TABLE <legacyItalic>base-table-name</legacyItalic></para>
            </TD>
            <TD>
              <para>Database (.dbc file)</para>
            </TD>
            <TD>
              <para>REMOVE TABLE <legacyItalic>TableName</legacyItalic> DELETE</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para> </para>
            </TD>
            <TD>
              <para>Directory of free tables (.dbf files)</para>
            </TD>
            <TD>
              <para>ERASE <legacyItalic>dbfName</legacyItalic></para>
              <para>ERASE <legacyItalic>cdxName</legacyItalic></para>
              <para>ERASE <legacyItalic>fptName</legacyItalic></para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithSyntaxDocument>