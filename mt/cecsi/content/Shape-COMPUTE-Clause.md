---
title: "Shape COMPUTE Clause"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3fdfead2-b5ab-4163-9b1d-3d2143a5db8c
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
# Shape COMPUTE Clause
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>A shape COMPUTE clause generates a parent <legacyBold>Recordset</legacyBold>, whose columns consist of a reference to the child <legacyBold>Recordset</legacyBold>; optional columns whose contents are chapter, new, or calculated columns, or the result of executing aggregate functions on the child <legacyBold>Recordset</legacyBold> or a previously shaped <legacyBold>Recordset</legacyBold>; and any columns from the child <legacyBold>Recordset</legacyBold> listed in the optional BY clause.</para>
  </introduction>
  <section>
    <title>Syntax</title>
    <content>
      <code>SHAPE <legacyItalic>child-command</legacyItalic> [AS] <legacyItalic>child-alias</legacyItalic>
   COMPUTE <legacyItalic>child-alias</legacyItalic> [[AS] <legacyItalic>name</legacyItalic>], [<legacyItalic>appended-column-list</legacyItalic>]
   [BY <legacyItalic>grp-field-list</legacyItalic>]</code>
    </content>
  </section>
  <section>
    <title>Description</title>
    <content>
      <para>The parts of this clause are as follows:  </para>
      <definitionTable>
        <definedTerm> <legacyItalic>child-command</legacyItalic> </definedTerm>
        <definition>
          <para>Consists of one of the following:</para>
          <list class="bullet">
            <listItem>
              <para>A query command within curly braces ("{}") that returns a child <legacyBold>Recordset</legacyBold> object. The command is issued to the underlying data provider, and its syntax depends on the requirements of that provider. This will typically be the SQL language, although ADO does not require any particular query language.</para>
            </listItem>
            <listItem>
              <para>The name of an existing shaped <legacyBold>Recordset</legacyBold>.</para>
            </listItem>
            <listItem>
              <para>Another shape command.</para>
            </listItem>
            <listItem>
              <para>The TABLE keyword, followed by the name of a table in the data provider.</para>
            </listItem>
          </list>
        </definition>
        <definedTerm> <legacyItalic>child-alias</legacyItalic> </definedTerm>
        <definition>
          <para>An alias used to refer to the <legacyBold>Recordset</legacyBold> returned by the <legacyItalic>child-command.</legacyItalic> The <legacyItalic>child-alias</legacyItalic> is required in the list of columns in the COMPUTE clause and defines the relation between the parent and child <legacyBold>Recordset</legacyBold> objects.</para>
        </definition>
        <definedTerm> <legacyItalic>appended-column-list</legacyItalic> </definedTerm>
        <definition>
          <para>A list in which each element defines a column in the generated parent. Each element contains either a chapter column, a new column, a calculated column, or a value resulting from an aggregate function on the child <legacyBold>Recordset</legacyBold>.</para>
        </definition>
        <definedTerm> <legacyItalic>grp-field-list</legacyItalic> </definedTerm>
        <definition>
          <para>A list of columns in the parent and child <legacyBold>Recordset</legacyBold> objects that specifies how rows should be grouped in the child.</para>
          <para>For each column in the <legacyItalic>grp-field-list,</legacyItalic> there is a corresponding column in the child and parent <legacyBold>Recordset</legacyBold> objects. For each row in the parent <legacyBold>Recordset</legacyBold>, the <legacyItalic>grp-field-list</legacyItalic> columns have unique values, and the child <legacyBold>Recordset</legacyBold> referenced by the parent row consists solely of child rows whose <legacyItalic>grp-field-list</legacyItalic> columns have the same values as the parent row. </para>
        </definition>
      </definitionTable>
      <para>If the BY clause is included, the child <legacyBold>Recordset</legacyBold>'s rows will be grouped based on the columns in the COMPUTE clause. The parent <legacyBold>Recordset</legacyBold> will contain one row for each group of rows in the child <legacyBold>Recordset</legacyBold>.</para>
      <para>If the BY clause is omitted, the entire child <legacyBold>Recordset</legacyBold> is treated as a single group and the parent <legacyBold>Recordset</legacyBold> will contain exactly one row. That row will reference the entire child <legacyBold>Recordset</legacyBold>. Omitting the BY clause allows you to compute "grand total" aggregates over the entire child <legacyBold>Recordset</legacyBold>.</para>
      <para>For example:</para>
      <code>         SHAPE {select * from Orders} AS orders             COMPUTE orders, SUM(orders.OrderAmount) as TotalSales       </code>
      <para>Regardless of which way the parent <legacyBold>Recordset</legacyBold> is formed (using COMPUTE or using APPEND), it will contain a chapter column that is used to relate it to a child <legacyBold>Recordset</legacyBold>. If you wish, the parent <legacyBold>Recordset</legacyBold> may also contain columns that contain aggregates (SUM, MIN, MAX, and so on) over the child rows. Both the parent and the child <legacyBold>Recordset</legacyBold> may contain columns that contain an expression on the row in the <legacyBold>Recordset</legacyBold>, as well as columns that are new and initially empty.</para>
    </content>
  </section>
  <section>
    <title>Operation</title>
    <content>
      <para>The <legacyItalic>child-command</legacyItalic> is issued to the provider, which returns a child <legacyBold>Recordset</legacyBold>.</para>
      <para>The COMPUTE clause specifies the columns of the parent <legacyBold>Recordset</legacyBold>, which may be a reference to the child <legacyBold>Recordset</legacyBold>, one or more aggregates, a calculated expression, or new columns. If there is a BY clause, the columns it defines are also appended to the parent <legacyBold>Recordset</legacyBold>. The BY clause specifies how the rows of the child <legacyBold>Recordset</legacyBold> are grouped.</para>
      <para>For example, assume you have a table, named Demographics, which consists of State, City, and Population fields. (The population figures in the table are provided solely as an example).</para>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>State</para>
            </TD>
            <TD>
              <para>City</para>
            </TD>
            <TD>
              <para>Population</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>WA</para>
            </TD>
            <TD>
              <para>Seattle</para>
            </TD>
            <TD>
              <para>700,000</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>OR</para>
            </TD>
            <TD>
              <para>Medford</para>
            </TD>
            <TD>
              <para>200,000</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>OR</para>
            </TD>
            <TD>
              <para>Portland</para>
            </TD>
            <TD>
              <para>400,000</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>CA</para>
            </TD>
            <TD>
              <para>Los Angeles</para>
            </TD>
            <TD>
              <para>800,000</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>CA</para>
            </TD>
            <TD>
              <para>San Diego</para>
            </TD>
            <TD>
              <para>600,000</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>WA</para>
            </TD>
            <TD>
              <para>Tacoma</para>
            </TD>
            <TD>
              <para>500,000</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>OR</para>
            </TD>
            <TD>
              <para>Corvallis</para>
            </TD>
            <TD>
              <para>300,000</para>
            </TD>
          </tr>
        </tbody>
      </table>
      <para>Now, issue this shape command:</para>
      <code>rst.Open  "SHAPE {select * from demographics} AS rs "  &amp; _
          "COMPUTE rs, SUM(rs.population) BY state", _
           objConnection</code>
      <para>This command opens a shaped <legacyBold>Recordset</legacyBold> with two levels. The parent level is a generated <legacyBold>Recordset</legacyBold> with an aggregate column (<codeInline>SUM(rs.population)</codeInline>), a column referencing the child <legacyBold>Recordset</legacyBold> (<codeInline>rs</codeInline>), and a column for grouping the child <legacyBold>Recordset</legacyBold> (<codeInline>state</codeInline>). The child level is the <legacyBold>Recordset</legacyBold> returned by the query command (<codeInline>select * from demographics</codeInline>).</para>
      <para>The child <legacyBold>Recordset</legacyBold> detail rows will be grouped by state, but otherwise in no particular order. That is, the groups will not be in alphabetical or numerical order. If you want the parent <legacyBold>Recordset</legacyBold> to be ordered, you can use the <legacyBold>Recordset</legacyBold> <legacyBold>Sort</legacyBold> method to order the parent <legacyBold>Recordset</legacyBold>.</para>
      <para>You can now navigate the opened parent <legacyBold>Recordset</legacyBold> and access the child detail <legacyBold>Recordset</legacyBold> objects. For more information, see <legacyLink xlink:href="25f1d2a1-6d5e-4457-aa07-5db5c75dee18">Accessing Rows in a Hierarchical Recordset</legacyLink>.</para>
    </content>
  </section>
  <section>
    <title>Resultant Parent and Child Detail Recordsets</title>
    <content />
    <sections>
      <section>
        <title>Parent</title>
        <content>
          <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
            <thead>
              <tr>
                <TD>
                  <para>SUM (rs.Population)</para>
                </TD>
                <TD>
                  <para>rs</para>
                </TD>
                <TD>
                  <para>State</para>
                </TD>
              </tr>
            </thead>
            <tbody>
              <tr>
                <TD>
                  <para>1,300,000</para>
                </TD>
                <TD>
                  <para>Reference to child1</para>
                </TD>
                <TD>
                  <para>CA</para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>1,200,000</para>
                </TD>
                <TD>
                  <para>Reference to child2</para>
                </TD>
                <TD>
                  <para>WA</para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>1,100,000</para>
                </TD>
                <TD>
                  <para>Reference to child3</para>
                </TD>
                <TD>
                  <para>OR</para>
                </TD>
              </tr>
            </tbody>
          </table>
        </content>
      </section>
    </sections>
  </section>
  <section>
    <title>Child1</title>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>State</para>
            </TD>
            <TD>
              <para>City</para>
            </TD>
            <TD>
              <para>Population</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>CA</para>
            </TD>
            <TD>
              <para>Los Angeles</para>
            </TD>
            <TD>
              <para>800,000</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>CA</para>
            </TD>
            <TD>
              <para>San Diego</para>
            </TD>
            <TD>
              <para>600,000</para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <section>
    <title>Child2</title>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>State</para>
            </TD>
            <TD>
              <para>City</para>
            </TD>
            <TD>
              <para>Population</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>WA</para>
            </TD>
            <TD>
              <para>Seattle</para>
            </TD>
            <TD>
              <para>700,000</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>WA</para>
            </TD>
            <TD>
              <para>Tacoma</para>
            </TD>
            <TD>
              <para>500,000</para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <section>
    <title>Child3</title>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>State</para>
            </TD>
            <TD>
              <para>City</para>
            </TD>
            <TD>
              <para>Population</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>OR</para>
            </TD>
            <TD>
              <para>Medford</para>
            </TD>
            <TD>
              <para>200,000</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>OR</para>
            </TD>
            <TD>
              <para>Portland</para>
            </TD>
            <TD>
              <para>400,000</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>OR</para>
            </TD>
            <TD>
              <para>Corvallis</para>
            </TD>
            <TD>
              <para>300,000</para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="25f1d2a1-6d5e-4457-aa07-5db5c75dee18">Accessing Rows in a Hierarchical Recordset</link>
<link xlink:href="4cb5fd29-4e56-46ac-ae48-a6771c321c0c">Data Shaping Summary</link>
<link xlink:href="b10a72fc-3c4b-4186-a70b-993dc9f7a092">Field Object</link>
<link xlink:href="ea691475-0f03-4abe-a785-b77e77712d1d">Formal Shape Grammar</link>
<link xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset Object</link>
<link xlink:href="d49d48d2-ac2d-4c11-895c-5a149b444620">Required Providers for Data Shaping</link>
<link xlink:href="f90fcf55-6b24-401d-94e1-d65bd24bd342">Shape APPEND Clause</link>
<link xlink:href="1fac7831-a187-4b15-9b43-aad380c5556c">Shape Commands in General</link>
<link xlink:href="48919c74-86d4-462e-99b9-8854ceb8d683">Value Property</link>
<link xlink:href="ccbdea9d-f9cf-4b0c-ade2-2d65311e12dc">Visual Basic for Applications Functions</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>