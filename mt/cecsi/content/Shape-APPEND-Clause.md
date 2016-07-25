---
title: "Shape APPEND Clause"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f90fcf55-6b24-401d-94e1-d65bd24bd342
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
# Shape APPEND Clause
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The shape command APPEND clause appends a column or columns to a <legacyBold>Recordset</legacyBold>. Frequently, these columns are chapter columns, which refer to a child <legacyBold>Recordset</legacyBold>.</para>
  </introduction>
  <section>
    <title>Syntax</title>
    <content>
      <code>SHAPE [<legacyItalic>parent-command</legacyItalic> [[AS] <legacyItalic>parent-alias</legacyItalic>]] APPEND <legacyItalic>column-list</legacyItalic></code>
    </content>
  </section>
  <section>
    <title>Description</title>
    <content>
      <para>The parts of this clause are as follows:  </para>
      <definitionTable>
        <definedTerm> <legacyItalic>parent-command</legacyItalic> </definedTerm>
        <definition>
          <para>Zero or one of the following (you can omit the <legacyItalic>parent-command</legacyItalic> completely):</para>
          <list class="bullet">
            <listItem>
              <para>A provider command enclosed in braces ("{}") that returns a <legacyBold>Recordset</legacyBold> object. The command is issued to the underlying data provider, and its syntax depends on the requirements of that provider. This will typically be the SQL language, although ADO does not require any particular query language.</para>
            </listItem>
            <listItem>
              <para>Another shape command embedded in parentheses.</para>
            </listItem>
            <listItem>
              <para>The TABLE keyword, followed by the name of a table in the data provider.</para>
            </listItem>
          </list>
        </definition>
        <definedTerm> <legacyItalic>parent-alias</legacyItalic> </definedTerm>
        <definition>
          <para>An optional alias that refers to the parent <legacyBold>Recordset</legacyBold>.</para>
        </definition>
        <definedTerm> <legacyItalic>column-list</legacyItalic> </definedTerm>
        <definition>
          <para>One or more of the following:</para>
          <list class="bullet">
            <listItem>
              <para>An aggregate column.</para>
            </listItem>
            <listItem>
              <para>A calculated column.</para>
            </listItem>
            <listItem>
              <para>A new column created by using the NEW clause.</para>
            </listItem>
            <listItem>
              <para>A chapter column. A chapter column definition is enclosed in parentheses ("()"). See the following syntax.</para>
            </listItem>
          </list>
        </definition>
      </definitionTable>
      <code>SHAPE [<legacyItalic>parent-command</legacyItalic> [[AS] <legacyItalic>parent-alias</legacyItalic>]]
   APPEND (<legacyItalic>child-recordset</legacyItalic> [ [[AS] <legacyItalic>child-alias</legacyItalic>] 
      RELATE <legacyItalic>parent-column</legacyItalic> TO <legacyItalic>child-column</legacyItalic> | PARAMETER <legacyItalic>param-number</legacyItalic>, <codeFeaturedElement>...</codeFeaturedElement> ])
   [[AS] <legacyItalic>chapter-alias</legacyItalic>] 
   [, <codeFeaturedElement>...</codeFeaturedElement> ]</code>
    </content>
  </section>
  <languageReferenceRemarks>
    <content>
      <definitionTable>
        <definedTerm> <legacyItalic>child-recordset</legacyItalic> </definedTerm>
        <definition>
          <list class="bullet">
            <listItem>
              <para>A provider command enclosed in braces ("{}") that returns a <legacyBold>Recordset</legacyBold> object. The command is issued to the underlying data provider, and its syntax depends on the requirements of that provider. This will typically be the SQL language, although ADO does not require any particular query language.</para>
            </listItem>
            <listItem>
              <para>Another shape command embedded in parentheses.</para>
            </listItem>
            <listItem>
              <para>The name of an existing shaped <legacyBold>Recordset</legacyBold>.</para>
            </listItem>
            <listItem>
              <para>The TABLE keyword, followed by the name of a table in the data provider.</para>
            </listItem>
          </list>
        </definition>
        <definedTerm> <legacyItalic>child-alias</legacyItalic> </definedTerm>
        <definition>
          <para>An alias that refers to the child <legacyBold>Recordset</legacyBold>.</para>
        </definition>
        <definedTerm> <legacyItalic>parent-column</legacyItalic> </definedTerm>
        <definition>
          <para>A column in the <legacyBold>Recordset</legacyBold> returned by the <legacyItalic>parent-command.</legacyItalic></para>
        </definition>
        <definedTerm> <legacyItalic>child-column</legacyItalic> </definedTerm>
        <definition>
          <para>A column in the <legacyBold>Recordset</legacyBold> returned by the <legacyItalic>child-command</legacyItalic>.</para>
        </definition>
        <definedTerm> <legacyItalic>param-number</legacyItalic> </definedTerm>
        <definition>
          <para>See <legacyLink xlink:href="4fae0d54-83b6-4ead-99cc-bcf532daa121">Operation of Parameterized Commands</legacyLink>.</para>
        </definition>
        <definedTerm> <legacyItalic>chapter-alias</legacyItalic> </definedTerm>
        <definition>
          <para>An alias that refers to the chapter column appended to the parent.</para>
        </definition>
      </definitionTable>
      <alert class="note">
        <para>The <legacyItalic>"parent-column </legacyItalic>TO <legacyItalic>child-column" </legacyItalic>clause is actually a list, where each relation defined is separated by a comma</para>
      </alert>
      <alert class="note">
        <para>The clause after the APPEND keyword is actually a list, where each clause is separated by a comma and defines another column to be appended to the parent.</para>
      </alert>
    </content>
  </languageReferenceRemarks>
  <languageReferenceRemarks>
    <content>
      <para>When you construct provider commands from user input as part of a SHAPE command, SHAPE will treat the user-supplied a provider command as an opaque string and pass them faithfully to the provider. For example, in the following SHAPE command,</para>
      <code>SHAPE {select * from t1} APPEND ({select * from t2} RELATE k1 TO k2)</code>
      <para>SHAPE will execute two commands: <codeInline>select * from t1</codeInline> and (<codeInline>select * from t2 RELATE k1 TO k2)</codeInline>. If the user supplies a compound command that consists of multiple provider commands separated by semicolons, SHAPE is not able to distinguish the difference. So in the following SHAPE command,</para>
      <code>SHAPE {select * from t1; drop table t1} APPEND ({select * from t2} RELATE k1 TO k2)</code>
      <para>SHAPE executes <codeInline>select * from t1; drop table t1</codeInline> and (<codeInline>select * from t2 RELATE k1 TO k2), </codeInline>not realizing that <codeInline>drop table t1</codeInline> is a separate and in this case, dangerous, provider command. Applications must always validate the user input to prevent such potential hacker attacks from occurring.</para>
      <para>This section contains the following topics.  </para>
      <list class="bullet">
        <listItem>
          <para>
            <legacyLink xlink:href="9700e50a-9f17-4ba3-8afb-f750741dc6ca">Operation of Non-Parameterized Commands</legacyLink>           </para>
        </listItem>
        <listItem>
          <para>
            <legacyLink xlink:href="4fae0d54-83b6-4ead-99cc-bcf532daa121">Operation of Parameterized Commands</legacyLink>           </para>
        </listItem>
        <listItem>
          <para>
            <legacyLink xlink:href="e8ca40e8-459c-40e2-8dd3-3ec6d5ee7b51">Hybrid Commands</legacyLink>           </para>
        </listItem>
        <listItem>
          <para>
            <legacyLink xlink:href="a576bf81-8f3c-4ba1-817b-87e89a8da684">Intervening Shape COMPUTE Clauses</legacyLink>           </para>
        </listItem>
      </list>
    </content>
  </languageReferenceRemarks>
  <relatedTopics>
<link xlink:href="1bfdcad4-52e1-45bc-ad21-783657ef0a44">Data Shaping</link>
<link xlink:href="ea691475-0f03-4abe-a785-b77e77712d1d">Formal Shape Grammar</link>
<link xlink:href="1fac7831-a187-4b15-9b43-aad380c5556c">Shape Commands in General</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>