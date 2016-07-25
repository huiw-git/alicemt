---
title: "Numeric Functions (Visual FoxPro ODBC Driver)"
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7caab48e-cbb5-4bbc-a09b-5cf902e5bc45
caps.latest.revision: 4
manager: jhubbard
---
# Numeric Functions (Visual FoxPro ODBC Driver)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The following table describes ODBC numeric functions supported by the Visual FoxPro ODBC Driver; when the Visual FoxPro grammar for the same function differs from the ODBC syntax, the Visual FoxPro equivalent is listed.</para>
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
              <code>ABS <legacyItalic>(numeric_exp)</legacyItalic></code>
            </TD>
            <TD>
              <code> </code>
            </TD>
          </tr>
          <tr>
            <TD>
              <code>ACOS <legacyItalic>(float_exp)</legacyItalic></code>
            </TD>
            <TD>
              <code> </code>
            </TD>
          </tr>
          <tr>
            <TD>
              <code>ASIN <legacyItalic>(float_exp)</legacyItalic></code>
            </TD>
            <TD>
              <code> </code>
            </TD>
          </tr>
          <tr>
            <TD>
              <code>ATAN <legacyItalic>(float_exp)</legacyItalic></code>
            </TD>
            <TD>
              <code> </code>
            </TD>
          </tr>
          <tr>
            <TD>
              <code>ATAN2 <legacyItalic>(float_exp1, float_exp2)</legacyItalic></code>
            </TD>
            <TD>
              <code>ATN2 (<legacyItalic>float_exp1, float_exp2</legacyItalic>)</code>
            </TD>
          </tr>
          <tr>
            <TD>
              <code>CEILING <legacyItalic>(numeric_exp)</legacyItalic></code>
            </TD>
            <TD>
              <code> </code>
            </TD>
          </tr>
          <tr>
            <TD>
              <code>COS <legacyItalic>(float_exp)</legacyItalic></code>
            </TD>
            <TD>
              <code> </code>
            </TD>
          </tr>
          <tr>
            <TD>
              <code>COT <legacyItalic>(float_exp)</legacyItalic></code>
            </TD>
            <TD>
              <code> </code>
            </TD>
          </tr>
          <tr>
            <TD>
              <code>DEGREES <legacyItalic>(numeric_exp)</legacyItalic></code>
            </TD>
            <TD>
              <code>RTOD <legacyItalic>(numeric_exp)</legacyItalic></code>
            </TD>
          </tr>
          <tr>
            <TD>
              <code>EXP <legacyItalic>(float_exp)</legacyItalic></code>
            </TD>
            <TD>
              <code> </code>
            </TD>
          </tr>
          <tr>
            <TD>
              <code>FLOOR <legacyItalic>(numeric_exp)</legacyItalic></code>
            </TD>
            <TD>
              <code> </code>
            </TD>
          </tr>
          <tr>
            <TD>
              <code>LOG <legacyItalic>(float_exp)</legacyItalic></code>
            </TD>
            <TD>
              <code> </code>
            </TD>
          </tr>
          <tr>
            <TD>
              <code>LOG10 <legacyItalic>(float_exp)</legacyItalic></code>
            </TD>
            <TD>
              <code> </code>
            </TD>
          </tr>
          <tr>
            <TD>
              <code>MOD <legacyItalic>(integer_exp1, integer_exp2)</legacyItalic></code>
            </TD>
            <TD>
              <code> </code>
            </TD>
          </tr>
          <tr>
            <TD>
              <code>PI <legacyItalic>( )</legacyItalic></code>
            </TD>
            <TD>
              <code> </code>
            </TD>
          </tr>
          <tr>
            <TD>
              <code>RADIANS <legacyItalic>(numeric_exp)</legacyItalic></code>
            </TD>
            <TD>
              <code>DTOR <legacyItalic>(numeric_exp)</legacyItalic></code>
            </TD>
          </tr>
          <tr>
            <TD>
              <code>RAND <legacyItalic>([integer_exp])</legacyItalic></code>
            </TD>
            <TD>
              <code> </code>
            </TD>
          </tr>
          <tr>
            <TD>
              <code>ROUND <legacyItalic>(numeric_exp, integer_exp)</legacyItalic></code>
            </TD>
            <TD>
              <code> </code>
            </TD>
          </tr>
          <tr>
            <TD>
              <code>SIGN <legacyItalic>(numeric_exp)</legacyItalic></code>
            </TD>
            <TD>
              <code> </code>
            </TD>
          </tr>
          <tr>
            <TD>
              <code>SIN <legacyItalic>(float_exp)</legacyItalic></code>
            </TD>
            <TD>
              <code> </code>
            </TD>
          </tr>
          <tr>
            <TD>
              <code>SQRT <legacyItalic>(float_exp)</legacyItalic></code>
            </TD>
            <TD>
              <code> </code>
            </TD>
          </tr>
          <tr>
            <TD>
              <code>TAN <legacyItalic>(float_exp)</legacyItalic></code>
            </TD>
            <TD>
              <code> </code>
            </TD>
          </tr>
        </tbody>
      </table>
      <para>The following numeric functions are not supported:</para>
      <para>
POWER <legacyItalic>(numeric_exp, integer_exp)</legacyItalic></para>
      <para>
TRUNCATE <legacyItalic>(numeric_exp, integer_exp)</legacyItalic></para>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>