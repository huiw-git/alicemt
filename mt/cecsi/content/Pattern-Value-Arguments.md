---
title: Pattern Value Arguments
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1d3f0ea6-87af-4836-807f-955e7df2b5df
translation.priority.ht: 
  - en-gb
---
# Pattern Value Arguments
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Some arguments in the catalog functions, such as the <legacyItalic>TableName</legacyItalic> argument in <legacyBold>SQLTables</legacyBold>, accept search patterns. These arguments accept search patterns if the SQL_ATTR_METADATA_ID statement attribute is set to SQL_FALSE; they are identifier arguments that do not accept a search pattern if this attribute is set to SQL_TRUE.</para>
    <para>The search pattern characters are:  </para>
    <list class="bullet">
      <listItem>
        <para>An underscore (_), which represents any single character.</para>
      </listItem>
      <listItem>
        <para>A percent sign (%), which represents any sequence of zero or more characters.</para>
      </listItem>
      <listItem>
        <para>An escape character, which is driver-specific and is used to include underscores, percent signs, and the escape character as literals. If the escape character precedes a non-special character, the escape character has no special meaning. If the escape character precedes a special character, it escapes the special character. For example, "\a" would be treated as two characters, "\" and "a", but "\%" would be treated as the non-special single character "%".</para>
      </listItem>
    </list>
    <para>The escape character is retrieved with the SQL_SEARCH_PATTERN_ESCAPE option in <legacyBold>SQLGetInfo</legacyBold>. It must precede any underscore, percent sign, or escape character in an argument that accepts search patterns to include that character as a literal. Examples are shown in the following table.</para>
    <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
      <thead>
        <tr>
          <TD>
            <para>Search pattern</para>
          </TD>
          <TD>
            <para>Description</para>
          </TD>
        </tr>
      </thead>
      <tbody>
        <tr>
          <TD>
            <para>%A%</para>
          </TD>
          <TD>
            <para>All identifiers containing the letter A</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>ABC_</para>
          </TD>
          <TD>
            <para>All four character identifiers starting with ABC</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>ABC\_</para>
          </TD>
          <TD>
            <para>The identifier ABC_, assuming the escape character is a backslash (\)</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>\\%</para>
          </TD>
          <TD>
            <para>All identifiers starting with a backslash (\), assuming the escape character is a backslash</para>
          </TD>
        </tr>
      </tbody>
    </table>
    <para>Special care must be taken to escape search pattern characters in arguments that accept search patterns. This is particularly true for the underscore character, which is commonly used in identifiers. A common mistake in applications is to retrieve a value from one catalog function and pass that value to a search pattern argument in another catalog function. For example, suppose an application retrieves the table name MY_TABLE from the result set for <legacyBold>SQLTables</legacyBold> and passes this to <legacyBold>SQLColumns</legacyBold> to retrieve a list of columns in MY_TABLE. Instead of getting the columns for MY_TABLE, the application will get the columns for all the tables that match the search pattern MY_TABLE, such as MY_TABLE, MY1TABLE, MY2TABLE, and so on.</para>
    <alert class="note">
      <para>ODBC 2.<legacyItalic>x</legacyItalic> drivers do not support search patterns in the <legacyItalic>CatalogName</legacyItalic> argument in <legacyBold>SQLTables</legacyBold>. ODBC 3<legacyItalic>.x</legacyItalic> drivers accept search patterns in this argument if the SQL_ATTR_ ODBC_VERSION environment attribute is set to SQL_OV_ODBC3; they do not accept search patterns in this argument if it is set to SQL_OV_ODBC2.</para>
    </alert>
    <para>Passing a null pointer to a search pattern argument does not constrain the search for that argument; that is, a null pointer and the search pattern % (any characters) are equivalent. However, a zero-length search pattern — that is, a valid pointer to a string of length zero — matches only the empty string ("").</para>
  </introduction>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>