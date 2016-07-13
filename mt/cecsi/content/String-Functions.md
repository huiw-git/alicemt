---
title: String Functions
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 270f669e-8aab-4db0-95a4-f2b3c69538b3
manager:jhubbard
translation.priority.ht: 
  - en-gb
---
# String Functions
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The following table lists string manipulation functions. An application can determine which string functions are supported by a driver by calling <legacyBold>SQLGetInfo</legacyBold> with an <legacyItalic>information type</legacyItalic> of SQL_STRING_FUNCTIONS.</para>
  </introduction>
  <languageReferenceRemarks>
    <content>
      <para>Arguments denoted as <legacyItalic>string_exp</legacyItalic> can be the name of a column,a <legacyItalic>character-string-literal</legacyItalic>, or the result of another scalar function, where the underlying data type can be represented as SQL_CHAR, SQL_VARCHAR, or SQL_LONGVARCHAR. </para>
      <para>Arguments denoted as <legacyItalic>character_exp</legacyItalic> are a variable-length character string.</para>
      <para>Arguments denoted as <legacyItalic>start</legacyItalic>, <legacyItalic>length</legacyItalic>, or <legacyItalic>count</legacyItalic> can be a <legacyItalic>numeric-literal</legacyItalic> or the result of another scalar function, where the underlying data type can be represented as SQL_TINYINT, SQL_SMALLINT, or SQL_INTEGER.</para>
      <para>The string functions listed here are 1-based; that is, the first character in the string is character 1. </para>
      <para>The BIT_LENGTH, CHAR_LENGTH, CHARACTER_LENGTH, OCTET_LENGTH, and POSITION string scalar functions have been added in ODBC 3.0 to align with SQL-92.</para>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>Function</para>
            </TD>
            <TD>
              <para>Description</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>
                <legacyBold>ASCII(</legacyBold>
                <legacyItalic>string_exp</legacyItalic>
                <legacyBold>) </legacyBold> (ODBC 1.0) </para>
            </TD>
            <TD>
              <para>Returns the ASCII code value of the leftmost character of <legacyItalic>string_exp</legacyItalic> as an integer.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyBold>BIT_LENGTH(</legacyBold>
                <legacyItalic>string_exp</legacyItalic>
                <legacyBold>) </legacyBold> (ODBC 3.0)</para>
            </TD>
            <TD>
              <para>Returns the length in bits of the string expression.</para>
              <para>Does not work only for string data types, therefore will not implicitly convert <legacyItalic>string_exp</legacyItalic> to string but instead will return the (internal) size of whatever datatype it is given.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyBold>CHAR(</legacyBold>
                <legacyItalic>code</legacyItalic>
                <legacyBold>) </legacyBold> (ODBC 1.0)</para>
            </TD>
            <TD>
              <para>Returns the character that has the ASCII code value specified by <legacyItalic>code</legacyItalic>. The value of <legacyItalic>code</legacyItalic> should be between 0 and 255; otherwise, the return value is data source–dependent.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyBold>CHAR_LENGTH(</legacyBold>
                <legacyItalic>string_exp</legacyItalic>
                <legacyBold>) </legacyBold> (ODBC 3.0)</para>
            </TD>
            <TD>
              <para>Returns the length in characters of the string expression, if the string expression is of a character data type; otherwise, returns the length in bytes of the string expression (the smallest integer not less than the number of bits divided by 8). (This function is the same as the CHARACTER_LENGTH function.)</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyBold>CHARACTER_LENGTH(</legacyBold>
                <legacyItalic>string_exp</legacyItalic>
                <legacyBold>) </legacyBold> (ODBC 3.0)</para>
            </TD>
            <TD>
              <para>Returns the length in characters of the string expression, if the string expression is of a character data type; otherwise, returns the length in bytes of the string expression (the smallest integer not less than the number of bits divided by 8). (This function is the same as the CHAR_LENGTH function.)</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyBold>CONCAT(</legacyBold>
                <legacyItalic>string_exp1</legacyItalic>,<legacyItalic>string_exp2</legacyItalic><legacyBold>) </legacyBold> (ODBC 1.0)</para>
            </TD>
            <TD>
              <para>Returns a character string that is the result of concatenating <legacyItalic>string_exp2</legacyItalic> to <legacyItalic>string_exp1</legacyItalic>. The resulting string is DBMS-dependent. For example, if the column represented by <legacyItalic>string_exp1</legacyItalic> contained a NULL value, DB2 would return NULL but SQL Server would return the non-NULL string.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyBold>DIFFERENCE(</legacyBold>
                <legacyItalic>string_exp1</legacyItalic>,<legacyItalic>string_exp2</legacyItalic><legacyBold>) </legacyBold> (ODBC 2.0)</para>
            </TD>
            <TD>
              <para>Returns an integer value that indicates the difference between the values returned by the SOUNDEX function for <legacyItalic>string_exp1</legacyItalic> and <legacyItalic>string_exp2</legacyItalic>.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyBold>INSERT(</legacyBold>
                <legacyItalic>string_exp1</legacyItalic>, <legacyItalic>start</legacyItalic>, <legacyItalic>length</legacyItalic>, <legacyItalic>string_exp2</legacyItalic><legacyBold>) </legacyBold> (ODBC 1.0)</para>
            </TD>
            <TD>
              <para>Returns a character string where <legacyItalic>length</legacyItalic> characters have been deleted from <legacyItalic>string_exp1</legacyItalic>, beginning at <legacyItalic>start</legacyItalic>, and where <legacyItalic>string_exp2</legacyItalic> has been inserted into <legacyItalic>string_exp,</legacyItalic> beginning at <legacyItalic>start</legacyItalic>.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyBold>LCASE(</legacyBold>
                <legacyItalic>string_exp</legacyItalic>
                <legacyBold>)</legacyBold> (ODBC 1.0)</para>
            </TD>
            <TD>
              <para>Returns a string equal to that in <legacyItalic>string_exp</legacyItalic>, with all uppercase characters converted to lowercase.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyBold>LEFT(</legacyBold>
                <legacyItalic>string_exp</legacyItalic>, <legacyItalic>count</legacyItalic><legacyBold>)</legacyBold> (ODBC 1.0)</para>
            </TD>
            <TD>
              <para>Returns the leftmost <legacyItalic>count</legacyItalic> characters of <legacyItalic>string_exp</legacyItalic>.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyBold>LENGTH(</legacyBold>
                <legacyItalic>string_exp</legacyItalic>
                <legacyBold>)</legacyBold> (ODBC 1.0)</para>
            </TD>
            <TD>
              <para>Returns the number of characters in <legacyItalic>string_exp,</legacyItalic> excluding trailing blanks.</para>
              <para>
                <legacyBold>LENGTH</legacyBold> only accepts strings. Therefore will implicitly convert <legacyItalic>string_exp</legacyItalic> to a string, and return the length of this string (not the internal size of the datatype).</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyBold>LOCATE(</legacyBold>
                <legacyItalic>string_exp1</legacyItalic>, <legacyItalic>string_exp2</legacyItalic>[, <legacyItalic>start</legacyItalic>]<legacyBold>)</legacyBold>  (ODBC 1.0)</para>
            </TD>
            <TD>
              <para>Returns the starting position of the first occurrence of <legacyItalic>string_exp1</legacyItalic> within <legacyItalic>string_exp2</legacyItalic>. The search for the first occurrence of <legacyItalic>string_exp1</legacyItalic> begins with the first character position in <legacyItalic>string_exp2</legacyItalic> unless the optional argument, <legacyItalic>start</legacyItalic>, is specified. If <legacyItalic>start</legacyItalic> is specified, the search begins with the character position indicated by the value of <legacyItalic>start</legacyItalic>. The first character position in <legacyItalic>string_exp2</legacyItalic> is indicated by the value 1. If <legacyItalic>string_exp1</legacyItalic> is not found within <legacyItalic>string_exp2</legacyItalic>, the value 0 is returned.</para>
              <para>If an application can call the LOCATE scalar function with the <legacyItalic>string_exp1</legacyItalic>, <legacyItalic>string_exp2</legacyItalic>, and <legacyItalic>start</legacyItalic> arguments, the driver returns SQL_FN_STR_LOCATE when <legacyBold>SQLGetInfo</legacyBold> is called with an <legacyItalic>Option</legacyItalic> of SQL_STRING_FUNCTIONS. If the application can call the LOCATE scalar function with only the <legacyItalic>string_exp1</legacyItalic> and <legacyItalic>string_exp2</legacyItalic> arguments, the driver returns SQL_FN_STR_LOCATE_2 when <legacyBold>SQLGetInfo</legacyBold> is called with an <legacyItalic>Option</legacyItalic> of SQL_STRING_FUNCTIONS. Drivers that support calling the LOCATE function with either two or three arguments return both SQL_FN_STR_LOCATE and SQL_FN_STR_LOCATE_2.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyBold>LTRIM(</legacyBold>
                <legacyItalic>string_exp</legacyItalic>
                <legacyBold>)</legacyBold> (ODBC 1.0)</para>
            </TD>
            <TD>
              <para>Returns the characters of <legacyItalic>string_exp</legacyItalic>, with leading blanks removed.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyBold>OCTET_LENGTH(</legacyBold>
                <legacyItalic>string_exp</legacyItalic>
                <legacyBold>)</legacyBold> (ODBC 3.0)</para>
            </TD>
            <TD>
              <para>Returns the length in bytes of the string expression. The result is the smallest integer not less than the number of bits divided by 8.</para>
              <para>Does not work only for string data types, therefore will not implicitly convert <legacyItalic>string_exp</legacyItalic> to string but instead will return the (internal) size of whatever datatype it is given.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyBold>POSITION(</legacyBold>
                <legacyItalic>character_exp</legacyItalic> <legacyBold>IN</legacyBold> <legacyItalic>character_exp</legacyItalic><legacyBold>)</legacyBold> (ODBC 3.0)</para>
            </TD>
            <TD>
              <para>Returns the position of the first character expression in the second character expression. The result is an exact numeric with an implementation-defined precision and a scale of 0.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyBold>REPEAT(</legacyBold>
                <legacyItalic>string_exp,</legacyItalic> <legacyItalic>count</legacyItalic><legacyBold>)</legacyBold> (ODBC 1.0)</para>
            </TD>
            <TD>
              <para>Returns a character string composed of <legacyItalic>string_exp</legacyItalic> repeated <legacyItalic>count</legacyItalic> times.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyBold>REPLACE(</legacyBold>
                <legacyItalic>string_exp1</legacyItalic>, <legacyItalic>string_exp2</legacyItalic>, <legacyItalic>string_exp3</legacyItalic><legacyBold>)</legacyBold> (ODBC 1.0)</para>
            </TD>
            <TD>
              <para>Search <legacyItalic>string_exp1 </legacyItalic>foroccurrences of <legacyItalic>string_exp2</legacyItalic>, and replace with <legacyItalic>string_exp3</legacyItalic>.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyBold>RIGHT(</legacyBold>
                <legacyItalic>string_exp</legacyItalic>, <legacyItalic>count</legacyItalic><legacyBold>)</legacyBold> (ODBC 1.0)</para>
            </TD>
            <TD>
              <para>Returns the rightmost <legacyItalic>count</legacyItalic> characters of <legacyItalic>string_exp</legacyItalic>.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyBold>RTRIM(</legacyBold>
                <legacyItalic>string_exp</legacyItalic>
                <legacyBold>)</legacyBold> (ODBC 1.0)</para>
            </TD>
            <TD>
              <para>Returns the characters of <legacyItalic>string_exp</legacyItalic> with trailing blanks removed.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyBold>SOUNDEX(</legacyBold>
                <legacyItalic>string_exp</legacyItalic>
                <legacyBold>)</legacyBold> (ODBC 2.0)</para>
            </TD>
            <TD>
              <para>Returns a data source–dependent character string representing the sound of the words in <legacyItalic>string_exp</legacyItalic>. For example, SQL Server returns a 4-digit SOUNDEX code; Oracle returns a phonetic representation of each word.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyBold>SPACE(</legacyBold>
                <legacyItalic>count</legacyItalic>
                <legacyBold>)</legacyBold> (ODBC 2.0)</para>
            </TD>
            <TD>
              <para>Returns a character string consisting of <legacyItalic>count</legacyItalic> spaces.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyBold>SUBSTRING(</legacyBold>
                <legacyItalic>string_exp</legacyItalic>, <legacyItalic>start</legacyItalic>, length<legacyBold>)</legacyBold> (ODBC 1.0)</para>
            </TD>
            <TD>
              <para>Returns a character string that is derived from <legacyItalic>string_exp</legacyItalic>, beginning at the character position specified by <legacyItalic>start</legacyItalic> for <legacyItalic>length</legacyItalic> characters.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyBold>UCASE(</legacyBold>
                <legacyItalic>string_exp</legacyItalic>
                <legacyBold>)</legacyBold> (ODBC 1.0)</para>
            </TD>
            <TD>
              <para>Returns a string equal to that in <legacyItalic>string_exp</legacyItalic>, with all lowercase characters converted to uppercase.</para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </languageReferenceRemarks>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>