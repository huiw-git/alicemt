---
title: "Shape Commands in General"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1fac7831-a187-4b15-9b43-aad380c5556c
caps.latest.revision: 15
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
# Shape Commands in General
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Data shaping defines the columns of a shaped <legacyBold>Recordset</legacyBold>, the relationships between the entities represented by the columns, and the manner in which the <legacyBold>Recordset</legacyBold> is populated with data.</para>
    <para>A shaped <legacyBold>Recordset</legacyBold> can consist of the following types of columns.</para>
    <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
      <thead>
        <tr>
          <TD>
            <para>Column type</para>
          </TD>
          <TD>
            <para>Description</para>
          </TD>
        </tr>
      </thead>
      <tbody>
        <tr>
          <TD>
            <para>data</para>
          </TD>
          <TD>
            <para>Fields from a <legacyBold>Recordset</legacyBold> returned by a query command to a data provider, table, or previously shaped <legacyBold>Recordset</legacyBold>.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>chapter</para>
          </TD>
          <TD>
            <para>A reference to another <legacyBold>Recordset</legacyBold>, called a <legacyItalic>chapter</legacyItalic>. Chapter columns make it possible to define a <legacyItalic>parent-child</legacyItalic> relationship where the <legacyItalic>parent</legacyItalic> is the <legacyBold>Recordset</legacyBold> that contains the chapter column and the <legacyItalic>child</legacyItalic> is the <legacyBold>Recordset</legacyBold> represented by the chapter.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>aggregate</para>
          </TD>
          <TD>
            <para>The value of the column is derived by executing an <legacyItalic>aggregate function</legacyItalic> on all the rows or a column of all the rows of a child <legacyBold>Recordset</legacyBold>. (See Aggregate Functions in the following topic, <legacyLink xlink:href="0590b466-2a36-49a2-868e-028ef5e49394">Aggregate Functions, the CALC Function, and the NEW Keyword</legacyLink>.)</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>calculated expression</para>
          </TD>
          <TD>
            <para>The value of the column is derived by calculating a Visual Basic for Applications expression on columns in the same row of the <legacyBold>Recordset</legacyBold>. The expression is the argument to the CALC function. (See Calculated Expression in the following topic, <legacyLink xlink:href="0590b466-2a36-49a2-868e-028ef5e49394">Aggregate Functions, the CALC Function, and the NEW Keyword</legacyLink> and in <legacyLink xlink:href="ccbdea9d-f9cf-4b0c-ade2-2d65311e12dc">Visual Basic for Applications Functions</legacyLink>.)</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>new</para>
          </TD>
          <TD>
            <para>Empty, fabricated fields, which can be populated with data at a later time. The column is defined with the NEW keyword. (See NEW keyword in the following topic, <legacyLink xlink:href="0590b466-2a36-49a2-868e-028ef5e49394">Aggregate Functions, the CALC Function, and the NEW Keyword</legacyLink>.)</para>
          </TD>
        </tr>
      </tbody>
    </table>
    <para>A shape command can contain a clause that specifies a query command to an underlying data provider that will return a <legacyBold>Recordset</legacyBold> object. The query's syntax depends on the requirements of the underlying data provider. This will usually be SQL, although ADO does not require the use of any particular query language.</para>
    <para>Shape commands can be issued by <legacyBold>Recordset</legacyBold> objects or by setting the <legacyLink xlink:href="4dd7e82a-8da5-4a4e-b439-11a29286fa0e">CommandText</legacyLink> property of the <legacyLink xlink:href="a02c22fb-542d-465e-a629-30fd59dcbebf">Command</legacyLink> object and then calling the <legacyLink xlink:href="f84a5ff3-0528-4ad7-9bea-9a15103378dd">Execute</legacyLink> method.</para>
    <para>You could use a SQL JOIN clause to relate two tables; however, a hierarchical <legacyBold>Recordset</legacyBold> can represent the information more efficiently. Each row of a <legacyBold>Recordset</legacyBold> created by a JOIN repeats information redundantly from one of the tables. A hierarchical <legacyBold>Recordset</legacyBold> has only one parent <legacyBold>Recordset</legacyBold> for each of multiple child <legacyBold>Recordset</legacyBold> objects.</para>
    <para>Shape commands can be nested. That is, the <legacyItalic>parent-command</legacyItalic> or<legacyItalic> child-command </legacyItalic>may itself be another shape command.</para>
    <para>The shape provider always returns a client cursor, even when the user specifies a cursor location of <legacyBold>adUseServer</legacyBold>.</para>
    <para>You can access the <legacyBold>Recordset</legacyBold> components of the shaped <legacyBold>Recordset</legacyBold> programmatically or through an appropriate visual control.</para>
    <para>Microsoft provides a visual tool that generates shape commands (see the <externalLink><linkText>Data Environment Designer</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=5689</linkUri></externalLink> in the Visual Basic 6 documentation) and another that displays hierarchical cursors (see "Using the Microsoft Hierarchical Flexgrid Control" in the Visual Basic 6 documentation).</para>
    <para>For information about navigating a hierarchical <legacyBold>Recordset</legacyBold>, see <legacyLink xlink:href="25f1d2a1-6d5e-4457-aa07-5db5c75dee18">Accessing Rows in a Hierarchical Recordset</legacyLink>.</para>
    <para>For precise information about syntactically correct shape commands, see <legacyLink xlink:href="ea691475-0f03-4abe-a785-b77e77712d1d">Formal Shape Grammar</legacyLink>.</para>
    <para>This section contains the following topics.</para>
    <list class="bullet">
      <listItem>
        <para>
          <legacyLink xlink:href="0590b466-2a36-49a2-868e-028ef5e49394">Aggregate Functions, the CALC Function, and the NEW Keyword</legacyLink>
        </para>
      </listItem>
      <listItem>
        <para>
          <legacyLink xlink:href="d6001863-7733-4c32-817f-081e48587fa1">Issuing Commands to the Underlying Data Provider</legacyLink>
        </para>
      </listItem>
    </list>
  </introduction>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>