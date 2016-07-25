---
title: "Operation of Parameterized Commands"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4fae0d54-83b6-4ead-99cc-bcf532daa121
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
# Operation of Parameterized Commands
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>If you are working with a large child <legacyBold>Recordset</legacyBold>, especially compared to the size of the parent <legacyBold>Recordset</legacyBold>, but need to access only a few child chapters, you might find it more efficient to use a parameterized command.</para>
    <para>A <legacyItalic>non-parameterized command</legacyItalic> retrieves both the entire parent and child <legacyBold>Recordsets</legacyBold>, appends a chapter column to the parent, and then assigns a reference to the related child chapter for each parent row.</para>
    <para>A <legacyItalic>parameterized command</legacyItalic> retrieves the entire parent <legacyBold>Recordset</legacyBold>, but retrieves only the chapter <legacyBold>Recordset</legacyBold> when the chapter column is accessed. This difference in retrieval strategy can yield significant performance benefits.</para>
    <para>For example, you can specify the following:</para>
    <code>SHAPE {SELECT * FROM customer} 
   APPEND ({SELECT * FROM orders WHERE cust_id = ?} 
   RELATE cust_id TO PARAMETER 0)</code>
    <para>The parent and child tables have a column name in common, cust_id<legacyItalic>. </legacyItalic>The <legacyItalic>child-command</legacyItalic> has a "?" placeholder, to which the RELATE clause refers (that is, "...PARAMETER 0").</para>
    <alert class="note">
      <para>The PARAMETER clause pertains solely to the shape command syntax. It is not associated with either the ADO <legacyLink xlink:href="e010e794-7f0f-4026-8b5b-37328e437d63">Parameter</legacyLink> object or the <legacyLink xlink:href="497cae10-3913-422a-9753-dcbb0a639b1b">Parameters</legacyLink> collection.</para>
    </alert>
    <para>When the parameterized shape command is executed, the following occurs:  </para>
    <list class="ordered">
      <listItem>
        <para>The <legacyItalic>parent-command</legacyItalic> is executed and returns a parent <legacyBold>Recordset</legacyBold> from the Customers table.</para>
      </listItem>
      <listItem>
        <para>A chapter column is appended to the parent <legacyBold>Recordset</legacyBold>.</para>
      </listItem>
      <listItem>
        <para>When the chapter column of a parent row is accessed, the <legacyItalic>child-command</legacyItalic> is executed using the value of the customer.cust_id as the value of the parameter.</para>
      </listItem>
      <listItem>
        <para>All rows in the data provider rowset created in step 3 are used to populate the child <legacyBold>Recordset</legacyBold>. In this example, that is all the rows in the Orders table in which the cust_id equals the value of customer.cust_id. By default, the child <legacyBold>Recordset</legacyBold>s will be cached on the client until all references to the parent <legacyBold>Recordset</legacyBold> are released. To change this behavior, set the <legacyBold>Recordset</legacyBold> <legacyLink xlink:href="80d389dd-46ef-459f-b0d4-6f712fc4f32d">dynamic property</legacyLink> <legacyBold>Cache Child Rows</legacyBold> to <legacyBold>False</legacyBold>.</para>
      </listItem>
      <listItem>
        <para>A reference to the retrieved child rows (that is, the chapter of the child <legacyBold>Recordset</legacyBold>) is placed in the chapter column of the current row of the parent <legacyBold>Recordset</legacyBold>.</para>
      </listItem>
      <listItem>
        <para>Steps 3–5 are repeated when the chapter column of another row is accessed.</para>
      </listItem>
    </list>
    <para>The <legacyBold>Cache Child Rows</legacyBold> dynamic property is set to <legacyBold>True</legacyBold> by default. The caching behavior varies depending upon the parameter values of the query. In a query with a single parameter, the child <legacyBold>Recordset</legacyBold> for a given parameter value will be cached between requests for a child with that value. The following code demonstrates this:</para>
    <code>SCmd = "SHAPE {select * from customer} " &amp; _
         "APPEND({select * from orders where cust_id = ?} " &amp; _
         "RELATE cust_id TO PARAMETER 0) AS chpCustOrder"
Rst1.Open sCmd, Cnn1
Set RstChild = Rst1("chpCustOrder").Value
Rst1.MoveNext      ' Next cust_id passed to Param 0, &amp; new rs fetched 
                   ' into RstChild.
Rst1.MovePrevious  ' RstChild now holds cached rs, saving round trip.</code>
    <para>In a query with two or more parameters, a cached child is used only if all the parameter values match the cached values.</para>
  </introduction>
  <section>
    <title>Parameterized Commands and Complex Parent Child Relations</title>
    <content>
      <para>In addition to using parameterized commands to improve performance of an equi-join type hierarchy, parameterized commands can be used to support more complex parent-child relationships. For example, consider a Little League database with two tables: one consisting of the teams (team_id, team_name) and the other of games (date, home_team, visiting_team).</para>
      <para>Using a non-parameterized hierarchy, there is no way to relate the teams and games tables in such a way that the child <legacyBold>Recordset</legacyBold> for each team contains its complete schedule. You can create chapters that contain the home schedule or the road schedule, but not both. This is because the RELATE clause limits you to parent-child relationships of the form (pc1=cc1) AND (pc2=pc2). So, if your command included "RELATE team_id TO home_team, team_id TO visiting_team", you would get only games where a team was playing itself. What you want is "(team_id=home_team) OR (team_id=visiting_team)", but the Shape provider does not support the OR clause.</para>
      <para>To obtain the desired result, you can use a parameterized command. For example:</para>
      <code>SHAPE {SELECT * FROM teams} 
APPEND ({SELECT * FROM games WHERE home_team = ? OR visiting_team = ?} 
        RELATE team_id TO PARAMETER 0, 
               team_id TO PARAMETER 1) </code>
      <para>This example exploits the greater flexibility of the SQL WHERE clause to get the result you need.</para>
      <alert class="note">
        <para>When using WHERE clauses, parameters can not use the SQL data types for text, ntext and image or an error will result that contains the following description: <codeInline>Invalid operator for data type</codeInline>.</para>
      </alert>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="1bfdcad4-52e1-45bc-ad21-783657ef0a44">Data Shaping</link>
<link xlink:href="ea691475-0f03-4abe-a785-b77e77712d1d">Formal Shape Grammar</link>
<link xlink:href="1fac7831-a187-4b15-9b43-aad380c5556c">Shape Commands in General</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>