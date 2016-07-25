---
title: "Aggregate Functions, the CALC Function, and the NEW Keyword"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0590b466-2a36-49a2-868e-028ef5e49394
caps.latest.revision: 10
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
# Aggregate Functions, the CALC Function, and the NEW Keyword
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Data shaping supports the following functions. The name assigned to the chapter containing the column to be operated on is the <legacyItalic>chapter-alias</legacyItalic>.</para>
    <para>A chapter-alias can be fully qualified, consisting of each chapter column name leading to the chapter containing the <legacyItalic>column-name, </legacyItalic>all separated by periods. For example, if the parent chapter, chap1, contains a child chapter, chap2, that has an amount column, amt, then the qualified name would be chap1.chap2.amt.</para>
    <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
      <thead>
        <tr>
          <TD>
            <para>Aggregate Functions</para>
          </TD>
          <TD>
            <para>Description</para>
          </TD>
        </tr>
      </thead>
      <tbody>
        <tr>
          <TD>
            <para>SUM(<legacyItalic>chapter-alias</legacyItalic>.<legacyItalic>column-name</legacyItalic>)</para>
          </TD>
          <TD>
            <para>Calculates the sum of all values in the specified column.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>AVG(<legacyItalic>chapter-alias</legacyItalic>.<legacyItalic>column-name</legacyItalic>)</para>
          </TD>
          <TD>
            <para>Calculates the average of all values in the specified column.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>MAX(<legacyItalic>chapter-alias</legacyItalic>.<legacyItalic>column-name</legacyItalic>)</para>
          </TD>
          <TD>
            <para>Calculates the maximum value in the specified column.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>MIN(<legacyItalic>chapter-alias</legacyItalic>.<legacyItalic>column-name</legacyItalic>)</para>
          </TD>
          <TD>
            <para>Calculates the minimum value in the specified column.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>COUNT(<legacyItalic>chapter-alias</legacyItalic>[.<legacyItalic>column-name</legacyItalic>])</para>
          </TD>
          <TD>
            <para>Counts the number of rows in the specified alias. If a column is specified, only rows for which that column is non-Null are included in the count.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>STDEV(<legacyItalic>chapter-alias</legacyItalic>.<legacyItalic>column-name</legacyItalic>)</para>
          </TD>
          <TD>
            <para>Calculates the standard deviation in the specified column.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>ANY(<legacyItalic>chapter-alias</legacyItalic>.<legacyItalic>column-name</legacyItalic>)</para>
          </TD>
          <TD>
            <para>A value of the specified column. ANY has a predictable value only when the value of the column is the same for all rows in the chapter.</para>
            <para>               <legacyBold>Note   </legacyBold>If the column does not contain the same value for all of the rows in the chapter, the SHAPE command arbitrarily returns one of the values to be the value of the ANY function. </para>
          </TD>
        </tr>
      </tbody>
    </table>
    <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
      <thead>
        <tr>
          <TD>
            <para>Calculated expression</para>
          </TD>
          <TD>
            <para>Description</para>
          </TD>
        </tr>
      </thead>
      <tbody>
        <tr>
          <TD>
            <para>CALC(<legacyItalic>expression</legacyItalic>)</para>
          </TD>
          <TD>
            <para>Calculates an arbitrary expression, but only on the row of the <legacyBold>Recordset</legacyBold> containing the CALC function. Any expression using these <legacyLink xlink:href="ccbdea9d-f9cf-4b0c-ade2-2d65311e12dc">Visual Basic for Applications (VBA) Functions</legacyLink> is allowed.</para>
          </TD>
        </tr>
      </tbody>
    </table>
    <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
      <thead>
        <tr>
          <TD>
            <para>NEW keyword</para>
          </TD>
          <TD>
            <para>Description</para>
          </TD>
        </tr>
      </thead>
      <tbody>
        <tr>
          <TD>
            <para>NEW <legacyItalic>field-type</legacyItalic> [(<legacyItalic>width</legacyItalic> | <legacyItalic>scale </legacyItalic>| <legacyItalic>precision</legacyItalic> | <legacyItalic>error</legacyItalic> [, <legacyItalic>scale</legacyItalic> | <legacyItalic>error</legacyItalic>])]</para>
          </TD>
          <TD>
            <para>Adds an empty column of the specified type to the <legacyBold>Recordset</legacyBold>.</para>
          </TD>
        </tr>
      </tbody>
    </table>
    <para>The <legacyItalic>field-type</legacyItalic> passed with the NEW keyword can be any of the following data types.</para>
    <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
      <thead>
        <tr>
          <TD>
            <para>OLE DB data types</para>
          </TD>
          <TD>
            <para>ADO data type equivalent(s)</para>
          </TD>
        </tr>
      </thead>
      <tbody>
        <tr>
          <TD>
            <para>DBTYPE_BSTR</para>
          </TD>
          <TD>
            <para>adBSTR</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>DBTYPE_BOOL</para>
          </TD>
          <TD>
            <para>adBoolean</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>DBTYPE_DECIMAL</para>
          </TD>
          <TD>
            <para>adDecimal</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>DBTYPE_UI1</para>
          </TD>
          <TD>
            <para>adUnsignedTinyInt</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>DBTYPE_I1</para>
          </TD>
          <TD>
            <para>adTinyInt</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>DBTYPE_UI2</para>
          </TD>
          <TD>
            <para>adUnsignedSmallInt</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>DBTYPE_UI4</para>
          </TD>
          <TD>
            <para>adUnsignedInt</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>DBTYPE_I8</para>
          </TD>
          <TD>
            <para>adBigInt</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>DBTYPE_UI8</para>
          </TD>
          <TD>
            <para>adUnsignedBigInt</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>DBTYPE_GUID</para>
          </TD>
          <TD>
            <para>adGuid</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>DBTYPE_BYTES</para>
          </TD>
          <TD>
            <para>adBinary, AdVarBinary, adLongVarBinary</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>DBTYPE_STR</para>
          </TD>
          <TD>
            <para>adChar, adVarChar, adLongVarChar</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>DBTYPE_WSTR</para>
          </TD>
          <TD>
            <para>adWChar, adVarWChar, adLongVarWChar</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>DBTYPE_NUMERIC</para>
          </TD>
          <TD>
            <para>adNumeric</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>DBTYPE_DBDATE</para>
          </TD>
          <TD>
            <para>adDBDate</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>DBTYPE_DBTIME</para>
          </TD>
          <TD>
            <para>adDBTime</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>DBTYPE_DBTIMESTAMP</para>
          </TD>
          <TD>
            <para>adDBTimeStamp</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>DBTYPE_VARNUMERIC</para>
          </TD>
          <TD>
            <para>adVarNumeric</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>DBTYPE_FILETIME</para>
          </TD>
          <TD>
            <para>adFileTime</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>DBTYPE_ERROR</para>
          </TD>
          <TD>
            <para>adError</para>
          </TD>
        </tr>
      </tbody>
    </table>
    <para>When the new field is of type decimal (in OLE DB, DBTYPE_DECIMAL, or in ADO, adDecimal), you must specify the precision and scale values.</para>
  </introduction>
  <relatedTopics>
<link xlink:href="1bfdcad4-52e1-45bc-ad21-783657ef0a44">Data Shaping</link>
<link xlink:href="ea691475-0f03-4abe-a785-b77e77712d1d">Formal Shape Grammar</link>
<link xlink:href="1fac7831-a187-4b15-9b43-aad380c5556c">Shape Commands in General</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>