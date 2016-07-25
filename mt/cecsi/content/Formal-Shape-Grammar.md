---
title: "Formal Shape Grammar"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ea691475-0f03-4abe-a785-b77e77712d1d
caps.latest.revision: 9
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
# Formal Shape Grammar
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This is the formal grammar for creating any shape command:  </para>
    <list class="bullet">
      <listItem>
        <para>Required grammatical terms are text strings delimited by angle brackets ("&lt;&gt;").</para>
      </listItem>
      <listItem>
        <para>Optional terms are delimited by square brackets ("[ ]").</para>
      </listItem>
      <listItem>
        <para>Alternatives are indicated by a virgule ("|").</para>
      </listItem>
      <listItem>
        <para>Repeating alternatives are indicated by an ellipsis ("...").</para>
      </listItem>
      <listItem>
        <para>             <legacyItalic>Alpha</legacyItalic> indicates a string of alphabetical letters.</para>
      </listItem>
      <listItem>
        <para>             <legacyItalic>Digit</legacyItalic> indicates a string of numbers.</para>
      </listItem>
      <listItem>
        <para>             <legacyItalic>Unicode-digit</legacyItalic> indicates a string of unicode digits.</para>
      </listItem>
    </list>
    <para>All other terms are literals.</para>
    <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
      <thead>
        <tr>
          <TD>
            <para>Term</para>
          </TD>
          <TD>
            <para>Definition</para>
          </TD>
        </tr>
      </thead>
      <tbody>
        <tr>
          <TD>
            <para>&lt;shape-command&gt;</para>
          </TD>
          <TD>
            <para>SHAPE [&lt;table-exp&gt; [[AS] &lt;alias&gt;]][&lt;shape-action&gt;]</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>&lt;table-exp&gt;</para>
          </TD>
          <TD>
            <para>{&lt;provider-command-text&gt;} |</para>
            <para>(&lt;shape-command&gt;) |</para>
            <para>TABLE &lt;quoted-name&gt; |</para>
            <para>&lt;quoted-name&gt;</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>&lt;shape-action&gt;</para>
          </TD>
          <TD>
            <para>APPEND &lt;aliased-field-list&gt; | </para>
            <para>COMPUTE &lt;aliased-field-list&gt; [BY &lt;field-list&gt;]</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>&lt;aliased-field-list&gt;</para>
          </TD>
          <TD>
            <para>&lt;aliased-field&gt; [, &lt;aliased-field...&gt;]</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>&lt;aliased-field&gt;</para>
          </TD>
          <TD>
            <para>&lt;field-exp&gt; [[AS] &lt;alias&gt;]</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>&lt;field-exp&gt;</para>
          </TD>
          <TD>
            <para>(&lt;relation-exp&gt;) |</para>
            <para>&lt;calculated-exp&gt; |</para>
            <para>&lt;aggregate-exp&gt; |</para>
            <para>&lt;new-exp&gt;</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>&lt;relation_exp&gt;</para>
          </TD>
          <TD>
            <para>&lt;table-exp&gt; [[AS] &lt;alias&gt;] </para>
            <para>   RELATE &lt;relation-cond-list&gt;</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>&lt;relation-cond-list&gt;</para>
          </TD>
          <TD>
            <para>&lt;relation-cond&gt; [, &lt;relation-cond&gt;...]</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>&lt;relation-cond&gt;</para>
          </TD>
          <TD>
            <para>&lt;field-name&gt; TO &lt;child-ref&gt;</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>&lt;child-ref&gt;</para>
          </TD>
          <TD>
            <para>&lt;field-name&gt; | </para>
            <para>PARAMETER &lt;param-ref&gt;</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>&lt;param-ref&gt;</para>
          </TD>
          <TD>
            <para>&lt;number&gt;</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>&lt;field-list&gt;</para>
          </TD>
          <TD>
            <para>&lt;field-name&gt; [, &lt;field-name&gt;]</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>&lt;aggregate-exp&gt;</para>
          </TD>
          <TD>
            <para>SUM(&lt;qualified-field-name&gt;) |</para>
            <para>AVG(&lt;qualified-field-name&gt;) |</para>
            <para>MIN(&lt;qualified-field-name&gt;) |</para>
            <para>MAX(&lt;qualified-field-name&gt;) |</para>
            <para>COUNT(&lt;qualified-alias&gt; | &lt;qualified-name&gt;) |</para>
            <para>STDEV(&lt;qualified-field-name&gt;) |</para>
            <para>ANY(&lt;qualified-field-name&gt;) </para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>&lt;calculated-exp&gt;</para>
          </TD>
          <TD>
            <para>CALC(&lt;expression&gt;)</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>&lt;qualified-field-name&gt;</para>
          </TD>
          <TD>
            <para>&lt;alias&gt;.[&lt;alias&gt;...]&lt;field-name&gt;</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>&lt;alias&gt;</para>
          </TD>
          <TD>
            <para>&lt;quoted-name&gt;</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>&lt;field-name&gt;</para>
          </TD>
          <TD>
            <para>&lt;quoted-name&gt; [[AS] &lt;alias&gt;]</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>&lt;quoted-name&gt;</para>
          </TD>
          <TD>
            <para>"&lt;string&gt;" |</para>
            <para>'&lt;string&gt;' |</para>
            <para>[&lt;string&gt;] |</para>
            <para>&lt;name&gt;</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>&lt;qualified-name&gt;</para>
          </TD>
          <TD>
            <para>alias[.alias...]</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>&lt;name&gt;</para>
          </TD>
          <TD>
            <para>alpha [ alpha | digit | _ | # | : | ...]</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>&lt;number&gt;</para>
          </TD>
          <TD>
            <para>digit [digit...]</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>&lt;new-exp&gt;</para>
          </TD>
          <TD>
            <para>NEW &lt;field-type&gt; [(&lt;number&gt; [, &lt;number&gt;])]</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>&lt;field-type&gt;</para>
          </TD>
          <TD>
            <para>An OLE DB or ADO data type.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>&lt;string&gt;</para>
          </TD>
          <TD>
            <para>unicode-char [unicode-char...]</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>&lt;expression&gt;</para>
          </TD>
          <TD>
            <para>A Visual Basic for Applications expression whose operands are other non-CALC columns in the same row.</para>
          </TD>
        </tr>
      </tbody>
    </table>
  </introduction>
  <relatedTopics>
<link xlink:href="25f1d2a1-6d5e-4457-aa07-5db5c75dee18">Accessing Rows in a Hierarchical Recordset</link>
<link xlink:href="4cb5fd29-4e56-46ac-ae48-a6771c321c0c">Data Shaping Summary</link>
<link xlink:href="d49d48d2-ac2d-4c11-895c-5a149b444620">Required Providers for Data Shaping</link>
<link xlink:href="f90fcf55-6b24-401d-94e1-d65bd24bd342">Shape APPEND Clause</link>
<link xlink:href="1fac7831-a187-4b15-9b43-aad380c5556c">Shape Commands in General</link>
<link xlink:href="3fdfead2-b5ab-4163-9b1d-3d2143a5db8c">Shape COMPUTE Clause</link>
<link xlink:href="ccbdea9d-f9cf-4b0c-ade2-2d65311e12dc">Visual Basic for Applications Functions</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>