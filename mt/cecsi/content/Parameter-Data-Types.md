---
title: Parameter Data Types
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: fd7e99d8-d26a-408c-9733-6ffccde99f75
manager:jhubbard
translation.priority.ht: 
  - en-gb
---
# Parameter Data Types
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Even though each parameter specified with <legacyBold>SQLBindParameter</legacyBold> is defined using an SQL data type, the parameters in an SQL statement have no intrinsic data type. Therefore, parameter markers can be included in an SQL statement only if their data types can be inferred from another operand in the statement. For example, in an arithmetic expression such as ? + COLUMN1, the data type of the parameter can be inferred from the data type of the named column represented by COLUMN1. An application cannot use a parameter marker if the data type cannot be determined.</para>
  </introduction>
  <section>
    <content>
      <para>The following table describes how a data type is determined for several types of parameters, in accordance with SQL-92. For a more comprehensive specification on inferring the parameter type when other SQL clauses are used, see the SQL-92 specification.</para>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>Location of parameter</para>
            </TD>
            <TD>
              <para>Assumed data type</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>One operand of a binary arithmetic or comparison operator</para>
            </TD>
            <TD>
              <para>Same as the other operand</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>The first operand in a <legacyBold>BETWEEN</legacyBold> clause</para>
            </TD>
            <TD>
              <para>Same as the second operand</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>The second or third operand in a <legacyBold>BETWEEN</legacyBold> clause</para>
            </TD>
            <TD>
              <para>Same as the first operand</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>An expression used with <legacyBold>IN</legacyBold></para>
            </TD>
            <TD>
              <para>Same as the first value or the result column of the subquery</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>A value used with <legacyBold>IN</legacyBold></para>
            </TD>
            <TD>
              <para>Same as the expression or the first value if there is a parameter marker in the expression</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>A pattern value used with <legacyBold>LIKE</legacyBold></para>
            </TD>
            <TD>
              <para>VARCHAR</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>An update value used with <legacyBold>UPDATE</legacyBold></para>
            </TD>
            <TD>
              <para>Same as the update column</para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>