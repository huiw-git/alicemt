---
title: SELECT - SQL Command
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2149c3ca-3a71-446d-8d53-3d056e2f301a
translation.priority.ht: 
  - en-gb
---
# SELECT - SQL Command
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Retrieves data from one or more tables.</para>
    <para>The Visual FoxPro ODBC Driver supports the native Visual FoxPro language syntax for this command. For driver-specific information, see <legacyBold>Driver Remarks</legacyBold>.</para>
  </introduction>
  <syntaxSection>
    <legacySyntax>
SELECT [ALL | DISTINCT]
   [<parameterReference>Alias</parameterReference>.] <parameterReference>Select_Item</parameterReference> [AS <parameterReference>Column_Name</parameterReference>]
   [, [<parameterReference>Alias</parameterReference>.] <parameterReference>Select_Item</parameterReference> [AS <parameterReference>Column_Name</parameterReference>] ...] 
FROM [<parameterReference>DatabaseName</parameterReference>!]<parameterReference>Table</parameterReference> [<parameterReference>Local_Alias</parameterReference>]
   [, [<parameterReference>DatabaseName</parameterReference>!]<parameterReference>Table</parameterReference> [<parameterReference>Local_Alias</parameterReference>] ...] 
[WHERE <parameterReference>JoinCondition</parameterReference> [AND <parameterReference>JoinCondition</parameterReference>
…]
   [AND | OR <parameterReference>FilterCondition</parameterReference> [AND | OR <parameterReference>FilterCondition</parameterReference> ...]]]
[GROUP BY <parameterReference>GroupColumn</parameterReference> [, <parameterReference>GroupColumn</parameterReference> ...]]
[HAVING <parameterReference>FilterCondition</parameterReference>]
[UNION [ALL] <parameterReference>SELECTCommand</parameterReference>]
[ORDER BY <parameterReference>Order_Item</parameterReference> [ASC | DESC] [, <parameterReference>Order_Item</parameterReference> [ASC | DESC] ...]]</legacySyntax>
  </syntaxSection>
  <section>
    <title>Arguments</title>
    <content>
      <alert class="note">
        <para>A <legacyItalic>subquery</legacyItalic>, referred to in the following arguments, is a SELECT within a SELECT and must be enclosed in parentheses. You can have up to two subqueries at the same level (not nested) in the WHERE clause. (See that section of the arguments.) Subqueries can contain multiple join conditions.</para>
      </alert>
      <definitionTable>
        <definedTerm>[ALL | DISTINCT]   [<parameterReference>Alias</parameterReference>.] <parameterReference>Select_Item</parameterReference> [AS <parameterReference>Column_Name</parameterReference>]    [, [<parameterReference>Alias</parameterReference>.] <parameterReference>Select_Item</parameterReference> [AS <parameterReference>Column_Name</parameterReference>] ...] </definedTerm>
        <definition>
          <para>The SELECT clause specifies the fields, constants, and expressions that are displayed in the query results. </para>
          <para>By default, ALL displays all the rows in the query results. </para>
          <para>DISTINCT excludes duplicates of any rows from the query results. </para>
          <alert class="note">
            <para>You can use DISTINCT only once per SELECT clause.</para>
          </alert>
          <para>
            <parameterReference>Alias</parameterReference>. qualifies matching item names. Each item you specify with <parameterReference>Select_Item</parameterReference> generates one column of the query results. If two or more items have the same name, include the table alias and a period before the item name to prevent columns from being duplicated. </para>
          <para>
            <parameterReference>Select_Item</parameterReference> specifies an item to be included in the query results. An item can be one of the following: </para>
          <list class="bullet">
            <listItem>
              <para>The name of a field from a table in the FROM clause. </para>
            </listItem>
            <listItem>
              <para>A constant specifying that the same constant value is to appear in every row of the query results. </para>
            </listItem>
            <listItem>
              <para>An expression that can be the name of a user-defined function. </para>
            </listItem>
          </list>
          <para>
            <legacyBold>User-Defined Functions with SELECT </legacyBold>
          </para>
          <para>Although using user-defined functions in the SELECT clause has obvious benefits, you should also consider the following restrictions: </para>
          <list class="bullet">
            <listItem>
              <para>The speed of operations performed with SELECT might be limited by the speed at which such user-defined functions are executed. High-volume manipulations involving user-defined functions might be better accomplished by using API and user-defined functions written in C or assembly language. </para>
            </listItem>
            <listItem>
              <para>The only reliable way to pass values to user-defined functions invoked from SELECT is by the argument list passed to the function when it is invoked. </para>
            </listItem>
            <listItem>
              <para>Even if you experiment and discover a supposedly forbidden manipulation that works correctly in a certain version of FoxPro, there is no guarantee it will continue to work in later versions. </para>
            </listItem>
          </list>
          <para>Apart from these restrictions, user-defined functions are acceptable in the SELECT clause. However, remember that using SELECT might slow performance. </para>
          <para>The following field functions are available for use with a select item that is a field or an expression involving a field: </para>
          <list class="bullet">
            <listItem>
              <para>AVG(<parameterReference>Select_Item</parameterReference>)—Averages a column of numeric data. </para>
            </listItem>
            <listItem>
              <para>COUNT(<parameterReference>Select_Item</parameterReference>)—Counts the number of select items in a column. COUNT(*) counts the number of rows in the query output. </para>
            </listItem>
            <listItem>
              <para>MIN(<parameterReference>Select_Item</parameterReference>)—Determines the smallest value of <parameterReference>Select_Item</parameterReference> in a column. </para>
            </listItem>
            <listItem>
              <para>MAX(<parameterReference>Select_Item</parameterReference>)—Determines the largest value of <parameterReference>Select_Item</parameterReference> in a column. </para>
            </listItem>
            <listItem>
              <para>SUM(<parameterReference>Select_Item</parameterReference>)—Totals a column of numeric data. </para>
            </listItem>
          </list>
          <para>You cannot nest field functions. </para>
        </definition>
        <definedTerm>AS <parameterReference>Column_Name</parameterReference></definedTerm>
        <definition>
          <para>Specifies the heading for a column in the query output. This is useful when <parameterReference>Select_Item</parameterReference> is an expression or contains a field function and you want to give the column a meaningful name. <parameterReference>Column_Name</parameterReference> can be an expression but cannot contain characters (for example, spaces) that are not permitted in table field names. </para>
        </definition>
        <definedTerm>FROM [<parameterReference>DatabaseName</parameterReference>!]<parameterReference>Table</parameterReference> [<parameterReference>Local_Alias</parameterReference>]   [, [<parameterReference>DatabaseName</parameterReference>!]<parameterReference>Table</parameterReference> [<parameterReference>Local_Alias</parameterReference>] ...] </definedTerm>
        <definition>
          <para>Lists the tables that contain the data that the query retrieves. If no table is open, Visual FoxPro displays the <legacyBold>Open</legacyBold> dialog box so that you can specify the file location. After it has been opened, the table remains open after the query is complete. </para>
          <para>
            <parameterReference>DatabaseName</parameterReference>! specifies the name of a database other than the one specified with the data source. You must include the name of the database that contains the table if the database is not specified with the data source. Include the exclamation point (!) delimiter after the database name and before the table name. </para>
          <para>
            <parameterReference>Local_Alias</parameterReference> specifies a temporary name for the table named in <parameterReference>Table</parameterReference>. If you specify a local alias, you must use the local alias instead of the table name throughout the SELECT statement. The local alias does not affect the Visual FoxPro environment. </para>
        </definition>
        <definedTerm>WHERE <parameterReference>JoinCondition</parameterReference> [AND <parameterReference>JoinCondition</parameterReference> ...]    [AND | OR <parameterReference>FilterCondition</parameterReference> [AND | OR <parameterReference>FilterCondition</parameterReference> ...]] </definedTerm>
        <definition>
          <para>Tells Visual FoxPro to include only certain records in the query results. WHERE is required to retrieve data from multiple tables. </para>
          <para>
            <parameterReference>JoinCondition</parameterReference> specifies fields that link the tables in the FROM clause. If you include more than one table in a query, you should specify a join condition for every table after the first. </para>
          <alert class="important">
            <para>Consider the following information when you create join conditions:</para>
          </alert>
          <list class="bullet">
            <listItem>
              <para>If you include two tables in a query and do not specify a join condition, every record in the first table is joined to every record in the second table as long as the filter conditions are met. Such a query can produce lengthy results. </para>
            </listItem>
            <listItem>
              <para>Use caution when joining tables with empty fields because Visual FoxPro matches empty fields. For example, if you join on CUSTOMER.ZIP and INVOICE.ZIP and if CUSTOMER contains 100 empty zip codes and INVOICE contains 400 empty zip codes, the query output contains 40,000 extra records resulting from the empty fields. Use the <legacyBold>EMPTY( )</legacyBold> function to eliminate empty records from the query output. </para>
            </listItem>
            <listItem>
              <para>You must use the AND operator to connect multiple join conditions. Each join condition has the following form: </para>
              <para>
                <parameterReference>FieldName1 Comparison FieldName2 </parameterReference>
              </para>
              <para>
                <parameterReference>FieldName1</parameterReference> is the name of a field from one table, <parameterReference>FieldName2</parameterReference> is the name of a field from another table, and <parameterReference>Comparison</parameterReference> is one of the operators described in the following table. </para>
            </listItem>
          </list>
          <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
            <thead>
              <tr>
                <TD>
                  <para>Operator</para>
                </TD>
                <TD>
                  <para>Comparison</para>
                </TD>
              </tr>
            </thead>
            <tbody>
              <tr>
                <TD>
                  <para>=</para>
                </TD>
                <TD>
                  <para>Equal</para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>==</para>
                </TD>
                <TD>
                  <para>Exactly equal</para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>LIKE</para>
                </TD>
                <TD>
                  <para>SQL LIKE</para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>&lt;&gt;, !=, #</para>
                </TD>
                <TD>
                  <para>Not equal</para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>&gt;</para>
                </TD>
                <TD>
                  <para>More than</para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>&gt;=</para>
                </TD>
                <TD>
                  <para>More than or equal to</para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>&lt;</para>
                </TD>
                <TD>
                  <para>Less than</para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>&lt;=</para>
                </TD>
                <TD>
                  <para>Less than or equal to</para>
                </TD>
              </tr>
            </tbody>
          </table>
          <para>When you use the = operator with strings, it acts differently, depending on the setting of SET ANSI. When SET ANSI is set to OFF, Visual FoxPro treats string comparisons in a manner familiar to Xbase users. When SET ANSI is set to ON, Visual FoxPro follows ANSI standards for string comparisons. See <legacyLink xlink:href="cf9a01b2-14bf-458c-a73c-2a58ddef32d8">SET ANSI</legacyLink> and <legacyLink xlink:href="9533d3e0-e7c1-49de-a3a3-0cc4373a91cb">SET EXACT</legacyLink> for more information about how Visual FoxPro performs string comparisons. </para>
          <para>
            <parameterReference>FilterCondition</parameterReference> specifies the criteria that records must meet to be included in the query results. You can include as many filter conditions in a query as you want, connecting them with the AND or OR operator. You can also use the NOT operator to reverse the value of a logical expression, or you can use <legacyBold>EMPTY( )</legacyBold> to check for an empty field. <parameterReference>FilterCondition</parameterReference> can take any of the forms in the following examples: </para>
          <para>
            <legacyBold>Example 1</legacyBold>   <parameterReference>FieldName1 Comparison FieldName2</parameterReference> </para>
          <para>
            <codeInline>customer.cust_id = orders.cust_id</codeInline>
          </para>
          <para>
            <legacyBold>Example 2</legacyBold>   <parameterReference>FieldName Comparison Expression</parameterReference> </para>
          <para>
            <codeInline>payments.amount &gt;= 1000</codeInline>
          </para>
          <para>
            <legacyBold>Example 3</legacyBold>   <parameterReference>FieldName Comparison</parameterReference> ALL (<parameterReference>Subquery</parameterReference>) </para>
          <para>
            <codeInline>company &lt; ALL ;</codeInline>
          </para>
          <para>
            <codeInline>(SELECT company FROM customer WHERE country = "USA")</codeInline>
          </para>
          <para>When the filter condition includes ALL, the field must meet the comparison condition for all values generated by the subquery before its record is included in the query results. </para>
          <para>
            <legacyBold>Example 4</legacyBold>   <parameterReference>FieldName Comparison</parameterReference> ANY | SOME (<parameterReference>Subquery</parameterReference>) </para>
          <para>
            <codeInline>company &lt; ANY ;</codeInline>
          </para>
          <para>
            <codeInline>(SELECT company FROM customer WHERE country = "USA")</codeInline>
          </para>
          <para>When the filter condition includes ANY or SOME, the field must meet the comparison condition for at least one of the values generated by the subquery. </para>
          <para>The following example checks to see whether the values in the field are within a specified range of values: </para>
          <para>
            <legacyBold>Example 5</legacyBold>   <parameterReference>FieldName</parameterReference> [NOT] BETWEEN <parameterReference>Start_Range</parameterReference> AND <parameterReference>End_Range</parameterReference> </para>
          <para>
            <codeInline>customer.postalcode BETWEEN 90000 AND 99999</codeInline>
          </para>
          <para>The following example checks to see whether at least one row meets the criteria in the subquery. When the filter condition includes EXISTS, the filter condition evaluates to True (.T.) unless the subquery evaluates to the empty set. </para>
          <para>
            <legacyBold>Example 6</legacyBold>   [NOT] EXISTS (<parameterReference>Subquery</parameterReference>) </para>
          <para>
            <codeInline>EXISTS ;</codeInline>
          </para>
          <para>
            <codeInline>(SELECT * FROM orders WHERE customer.postalcode =</codeInline>
          </para>
          <para>
            <codeInline>orders.postalcode)</codeInline>
          </para>
          <para>
            <legacyBold>Example 7</legacyBold>   <parameterReference>FieldName</parameterReference> [NOT] IN <parameterReference>Value_Set</parameterReference> </para>
          <para>
            <codeInline>customer.postalcode NOT IN ("98052","98072","98034")</codeInline>
          </para>
          <para>When the filter condition includes IN, the field must contain one of the values before its record is included in the query results. </para>
          <para>
            <legacyBold>Example 8</legacyBold>   <parameterReference>FieldName</parameterReference> [NOT] IN (<parameterReference>Subquery</parameterReference>) </para>
          <para>
            <codeInline>customer.cust_id IN ;</codeInline>
          </para>
          <para>
            <codeInline>(SELECT orders.cust_id FROM orders WHERE orders.city="Seattle")</codeInline>
          </para>
          <para>Here the field must contain one of the values returned by the subquery before its record is included in the query results. </para>
          <para>
            <legacyBold>Example 9</legacyBold>   <parameterReference>FieldName</parameterReference> [NOT] LIKE <parameterReference>cExpression</parameterReference> </para>
          <para>
            <codeInline>customer.country NOT LIKE "USA"</codeInline>
          </para>
          <para>This filter condition searches for each field that matches <parameterReference>cExpression</parameterReference>. You can use the percent sign (%) and underscore ( _ ) wildcard characters as part of <parameterReference>cExpression</parameterReference>. The underscore represents a single unknown character in the string. </para>
        </definition>
        <definedTerm>GROUP BY <parameterReference>GroupColumn</parameterReference> [, <parameterReference>GroupColumn</parameterReference> ...]</definedTerm>
        <definition>
          <para>Groups rows in the query based on values in one or more columns. <parameterReference>GroupColumn</parameterReference> can be one of the following: </para>
          <list class="bullet">
            <listItem>
              <para>The name of a regular table field. </para>
            </listItem>
            <listItem>
              <para>A field that includes an SQL field function. </para>
            </listItem>
            <listItem>
              <para>A numeric expression that indicates the location of the column in the result table. (The leftmost column number is 1.)</para>
            </listItem>
          </list>
        </definition>
        <definedTerm>HAVING <parameterReference>FilterCondition</parameterReference> </definedTerm>
        <definition>
          <para>Specifies a filter condition that groups must meet to be included in the query results. HAVING should be used with GROUP BY and can include as many filter conditions as you want, connected by the AND or OR operator. You can also use NOT to reverse the value of a logical expression. </para>
          <para>
            <parameterReference>FilterCondition</parameterReference> cannot contain a subquery. </para>
          <para>A HAVING clause without a GROUP BY clause behaves like a WHERE clause. You can use local aliases and field functions in the HAVING clause. Use a WHERE clause for faster performance if your HAVING clause contains no field functions. </para>
        </definition>
        <definedTerm>[UNION [ALL] <parameterReference>SELECTCommand</parameterReference>]</definedTerm>
        <definition>
          <para>Combines the final results of one SELECT with the final results of another SELECT. By default, UNION checks the combined results and eliminates duplicate rows. Use parentheses to combine multiple UNION clauses. </para>
          <para>ALL prevents UNION from eliminating duplicate rows from the combined results. </para>
          <para>UNION clauses follow these rules: </para>
          <list class="bullet">
            <listItem>
              <para>You cannot use UNION to combine subqueries. </para>
            </listItem>
            <listItem>
              <para>Both SELECT commands must have the same number of columns in their query output. </para>
            </listItem>
            <listItem>
              <para>Each column in the query results of one SELECT must have the same data type and width as the corresponding column in the other SELECT. </para>
            </listItem>
            <listItem>
              <para>Only the final SELECT can have an ORDER BY clause, which must refer to output columns by number. If an ORDER BY clause is included, it affects the complete result. </para>
            </listItem>
          </list>
          <para>You can also use the UNION clause to simulate an outer join. </para>
          <para>When you join two tables in a query, only records with matching values in the joining fields are included in the output. If a record in the parent table does not have a corresponding record in the child table, the record in the parent table is not included in the output. An outer join lets you include all the records in the parent table in the output, together with the matching records in the child table. To create an outer join in Visual FoxPro, you must use a nested SELECT command, as in the following example: </para>
          <code>SELECT customer.company, orders.order_id, orders.emp_id ;
FROM customer, orders ;
WHERE customer.cust_id = orders.cust_id ;
UNION ;
SELECT customer.company, 0, 0 ;
FROM customer ;
WHERE customer.cust_id NOT IN ;
(SELECT orders.cust_id FROM orders)</code>
          <alert class="note">
            <para>Make sure that you include the space that immediately precedes each semicolon. Otherwise, you will receive an error.</para>
          </alert>
          <para>The section of the command before the UNION clause selects records from both tables that have matching values. The customer companies that do not have associated invoices are not included. The section of the command after the UNION clause selects records in the customer table that do not have matching records in the orders table. </para>
          <para>Regarding the second section of the command, note the following: </para>
          <list class="bullet">
            <listItem>
              <para>The SELECT statement within the parentheses is processed first. This statement creates a selection of all customer numbers in the orders table. </para>
            </listItem>
            <listItem>
              <para>The WHERE clause finds all customer numbers in the customer table that are not in the orders table. Because the first section of the command provided all companies that had a customer number in the orders table, all companies in the customer table are now included in the query results. </para>
            </listItem>
            <listItem>
              <para>Because the structures of tables included in a UNION must be identical, there are two placeholders in the second SELECT statement to represent <legacyItalic>orders.order_id</legacyItalic> and <legacyItalic>orders.emp_id</legacyItalic> from the first SELECT statement. </para>
              <alert class="note">
                <para>The placeholders must be the same type as the fields that they represent. If the field is a date type, the placeholder should be { / / }. If the field is a character field, the placeholder should be the empty string ("").</para>
              </alert>
            </listItem>
          </list>
        </definition>
        <definedTerm>ORDER BY <parameterReference>Order_Item</parameterReference> [ASC | DESC] [, <parameterReference>Order_Item</parameterReference> [ASC | DESC] ...] </definedTerm>
        <definition>
          <para>Sorts the query results based on the data in one or more columns. Each <parameterReference>Order_Item</parameterReference> must correspond to a column in the query results and can be one of the following: </para>
          <list class="bullet">
            <listItem>
              <para>A field in a FROM table that is also a select item in the main SELECT clause (not in a subquery). </para>
            </listItem>
            <listItem>
              <para>A numeric expression that indicates the location of the column in the result table. (The leftmost column is number 1.) </para>
            </listItem>
          </list>
          <para>ASC specifies an ascending order for query results, according to the order item or items, and is the default for ORDER BY. </para>
          <para>DESC specifies a descending order for query results. </para>
          <para>Query results appear unordered if you do not specify an order with ORDER BY. </para>
        </definition>
      </definitionTable>
    </content>
  </section>
  <languageReferenceRemarks>
    <content>
      <para>SELECT is an SQL command that is built into Visual FoxPro like any other Visual FoxPro command. When you use SELECT to pose a query, Visual FoxPro interprets the query and retrieves the specified data from the tables. You can create a SELECT query from within either the Command Prompt window or a Visual FoxPro program (as with any other Visual FoxPro command).</para>
      <alert class="note">
        <para>SELECT does not respect the current filter condition specified with SET FILTER.</para>
      </alert>
    </content>
  </languageReferenceRemarks>
  <section>
    <title>Driver Remarks</title>
    <content>
      <para>When your application sends the ODBC SQL statement SELECT to the data source, the Visual FoxPro ODBC Driver converts the command into the Visual FoxPro SELECT command without translation unless the command contains an ODBC escape sequence. Items enclosed in an ODBC escape sequence are converted to Visual FoxPro syntax. For more information about using ODBC escape sequences, see <legacyLink xlink:href="c1fb63b7-af50-45d6-8dec-ae6ea7119527">Time and Date Functions</legacyLink> and in the <legacyItalic>Microsoft ODBC Programmer's Reference</legacyItalic>, see <legacyLink xlink:href="cf229f21-6c38-4b5b-aca8-f1be0dfeb3d0">Escape Sequences in ODBC</legacyLink>.</para>
    </content>
  </section>
  <relatedTopics>
<legacyLink xlink:href="be2143ba-fc16-42c9-84f7-8985cd924860">CREATE TABLE - SQL</legacyLink>
<legacyLink xlink:href="9b648198-349f-46f6-b869-13d129945971">INSERT - SQL</legacyLink>
<legacyLink xlink:href="cf9a01b2-14bf-458c-a73c-2a58ddef32d8">SET ANSI</legacyLink>
<legacyLink xlink:href="9533d3e0-e7c1-49de-a3a3-0cc4373a91cb">SET EXACT</legacyLink>
</relatedTopics>
</developerReferenceWithSyntaxDocument>