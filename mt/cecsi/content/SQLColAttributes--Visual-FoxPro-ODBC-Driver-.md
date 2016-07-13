---
title: SQLColAttributes (Visual FoxPro ODBC Driver)
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d403dfa0-c26d-47d4-91d9-2f29aa387399
manager:jhubbard
translation.priority.ht: 
  - en-gb
---
# SQLColAttributes (Visual FoxPro ODBC Driver)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <alert class="note">
      <para>This topic contains Visual FoxPro ODBC Driver-specific information. For general information about this function, see the appropriate topic under <legacyLink xlink:href="b7a49774-f458-44ce-9a04-a0457501405b">ODBC API Reference</legacyLink>.</para>
    </alert>
    <para>Support: Full </para>
    <para>ODBC API Conformance: Core Level</para>
    <para>Returns descriptor information for a column in a result set. Descriptor information is returned as a character string, a 32-bit descriptor-dependent value, or an integer value.</para>
    <alert class="note">
      <para>           <legacyBold>SQLColAttributes</legacyBold> cannot be used to return information about the bookmark column (column 0).</para>
    </alert>
    <para>The Visual FoxPro ODBC Driver supports all <legacyItalic>fDescType</legacyItalic> values. The following table includes comments on the driver's implementation of selected values.</para>
    <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
      <thead>
        <tr>
          <TD>
            <para>                 <legacyItalic>fDescType</legacyItalic>               </para>
          </TD>
          <TD>
            <para>Comment</para>
          </TD>
        </tr>
      </thead>
      <tbody>
        <tr>
          <TD>
            <para>SQL_COLUMN_AUTO_INCREMENT</para>
          </TD>
          <TD>
            <para>Returns FALSE: Visual FoxPro has no counter fields.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_COLUMN_CASE_SENSITIVE</para>
          </TD>
          <TD>
            <para>Always returns TRUE if the column type is Character.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_COLUMN_LABEL</para>
          </TD>
          <TD>
            <para>Returns the column name, which is also returned by SQL_COLUMN_NAME.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_COLUMN_MONEY</para>
          </TD>
          <TD>
            <para>Returns TRUE if the column type is Currency (represented by a "Y" in the Visual FoxPro language).</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_COLUMN_OWNER_NAME</para>
          </TD>
          <TD>
            <para>Always returns an empty string.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_COLUMN_QUALIFIER_NAME</para>
          </TD>
          <TD>
            <para>Always returns an empty string.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_COLUMN_SEARCHABLE</para>
          </TD>
          <TD>
            <para>Returns SQL_UNSEARCHABLE for columns of type General; these columns cannot be used in a WHERE clause.</para>
            <para>Returns SQL_SEARCHABLE for columns of type Character or Memo with NOCPTRANS not set; these columns can be used in a WHERE clause with any comparison operator.</para>
            <para>Returns SQL_ALL_EXCEPT_LIKE for all other column types; these columns can be used in a WHERE clause with all comparison operators except LIKE.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_COLUMN_TABLE_NAME</para>
          </TD>
          <TD>
            <para>Always returns an empty string.</para>
          </TD>
        </tr>
      </tbody>
    </table>
    <para>For more information, see <legacyLink xlink:href="3ece37af-db56-47fc-bc9d-6a7d0d8a00ec">SQLColAttributes</legacyLink> in the <legacyItalic>ODBC Programmer's Reference</legacyItalic>.</para>
  </introduction>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>