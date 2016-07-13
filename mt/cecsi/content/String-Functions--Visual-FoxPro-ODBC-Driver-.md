---
title: String Functions (Visual FoxPro ODBC Driver)
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1974fd26-ef0d-45d5-860b-298917c8e9c3
manager:jhubbard
---
# String Functions (Visual FoxPro ODBC Driver)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The following table lists ODBC string manipulation functions supported by the Visual FoxPro ODBC Driver; when the Visual FoxPro grammar for the same function differs from the ODBC syntax, the Visual FoxPro equivalent is listed.</para>
  </introduction>
  <section>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>ODBC grammar</para>
            </TD>
            <TD>
              <para>Visual FoxPro grammar</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <code>ASCII <legacyItalic>(string_exp)</legacyItalic></code>
            </TD>
            <TD>
              <code>ASC <legacyItalic>(string_exp)</legacyItalic></code>
            </TD>
          </tr>
          <tr>
            <TD>
              <code>CHAR <legacyItalic>(code)</legacyItalic></code>
            </TD>
            <TD>
              <code>CHR <legacyItalic>(string_exp)</legacyItalic></code>
            </TD>
          </tr>
          <tr>
            <TD>
              <code>CONCAT <legacyItalic>(string_exp1, string_exp2)</legacyItalic></code>
            </TD>
            <TD><code><legacyItalic>string_exp1 + string_exp2</legacyItalic>            </code>
            </TD>
          </tr>
          <tr>
            <TD>
              <code>DIFFERENCE <legacyItalic>(string_exp1, string_exp2)</legacyItalic></code>
            </TD>
            <TD>
              <code> </code>
            </TD>
          </tr>
          <tr>
            <TD>
              <code>INSERT <legacyItalic>(string_exp1, start, length, string_exp2)</legacyItalic></code>
            </TD>
            <TD>
              <code>STUFF <legacyItalic>(string_exp1, start, length, string_exp2)</legacyItalic></code>
            </TD>
          </tr>
          <tr>
            <TD>
              <code>LCASE <legacyItalic>(string_exp)</legacyItalic></code>
            </TD>
            <TD>
              <code>LOWER <legacyItalic>(string_exp)</legacyItalic></code>
            </TD>
          </tr>
          <tr>
            <TD>
              <code>LEFT <legacyItalic>(string_exp, count)</legacyItalic></code>
            </TD>
            <TD>
              <code> </code>
            </TD>
          </tr>
          <tr>
            <TD>
              <code>LENGTH <legacyItalic>(string_exp)</legacyItalic></code>
            </TD>
            <TD>
              <code>LEN <legacyItalic>(string_exp)</legacyItalic></code>
            </TD>
          </tr>
          <tr>
            <TD>
              <code>LTRIM <legacyItalic>(string_exp)</legacyItalic></code>
            </TD>
            <TD>
              <code> </code>
            </TD>
          </tr>
          <tr>
            <TD>
              <code>REPEAT <legacyItalic>(string_exp, count)</legacyItalic></code>
            </TD>
            <TD>
              <code>REPLICATE <legacyItalic>(string_exp, count)</legacyItalic></code>
            </TD>
          </tr>
          <tr>
            <TD>
              <code>REPLACE <legacyItalic>(string_exp1, string_exp2, string_exp3)</legacyItalic></code>
            </TD>
            <TD>
              <code>STRTRAN <legacyItalic>(string_exp1, string_exp2, string_exp3)</legacyItalic></code>
            </TD>
          </tr>
          <tr>
            <TD>
              <code>RIGHT <legacyItalic>(string_exp, count)</legacyItalic></code>
            </TD>
            <TD>
              <code> </code>
            </TD>
          </tr>
          <tr>
            <TD>
              <code>RTRIM <legacyItalic>(string_exp)</legacyItalic></code>
            </TD>
            <TD>
              <code> </code>
            </TD>
          </tr>
          <tr>
            <TD>
              <code>SOUNDEX <legacyItalic>(string_exp)</legacyItalic></code>
            </TD>
            <TD>
              <code> </code>
            </TD>
          </tr>
          <tr>
            <TD>
              <code>SPACE <legacyItalic>(count)</legacyItalic></code>
            </TD>
            <TD>
              <code> </code>
            </TD>
          </tr>
          <tr>
            <TD>
              <code>SUBSTRING <legacyItalic>(string_exp, start, length)</legacyItalic></code>
            </TD>
            <TD>
              <code>SUBSTR <legacyItalic>(string_exp, start, length)</legacyItalic></code>
            </TD>
          </tr>
          <tr>
            <TD>
              <code>UCASE <legacyItalic>(string_exp)</legacyItalic></code>
            </TD>
            <TD>
              <code>UPPER <legacyItalic>(string_exp)</legacyItalic></code>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <relatedTopics/>
</developerReferenceWithoutSyntaxDocument>
