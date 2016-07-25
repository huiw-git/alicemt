---
title: "CREATE TABLE - SQL Command"
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: be2143ba-fc16-42c9-84f7-8985cd924860
caps.latest.revision: 4
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# CREATE TABLE - SQL Command
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Creates a table having the specified fields.</para>
    <para>The Visual FoxPro ODBC Driver supports the native Visual FoxPro language syntax for this command. For driver-specific information, see <legacyBold>Driver Remarks</legacyBold>.</para>
  </introduction>
  <syntaxSection>
    <legacySyntax>
CREATE TABLE | DBF <parameterReference>TableName1</parameterReference> [NAME <parameterReference>LongTableName</parameterReference>] [FREE]
   (<parameterReference>FieldName1FieldType </parameterReference>[(<parameterReference>nFieldWidth </parameterReference>[, <parameterReference>nPrecision</parameterReference>])]
      [NULL | NOT NULL] 
      [CHECK <parameterReference>lExpression1</parameterReference> [ERROR <parameterReference>cMessageText1</parameterReference>]]
      [DEFAULT <parameterReference>eExpression1</parameterReference>]
      [PRIMARY KEY | UNIQUE]
      [REFERENCES <parameterReference>TableName2</parameterReference> [TAG <parameterReference>TagName1</parameterReference>]]
      [NOCPTRANS]
   [, <parameterReference>FieldName2</parameterReference> ...]
      [, PRIMARY KEY <parameterReference>eExpression2</parameterReference> TAG <parameterReference>TagName2</parameterReference>
      |, UNIQUE <parameterReference>eExpression3</parameterReference> TAG <parameterReference>TagName3</parameterReference>]
      [, FOREIGN KEY <parameterReference>eExpression4</parameterReference> TAG <parameterReference>TagName4</parameterReference> [NODUP]
            REFERENCES <parameterReference>TableName3</parameterReference> [TAG <parameterReference>TagName5</parameterReference>]]
      [, CHECK <parameterReference>lExpression2</parameterReference> [ERROR <parameterReference>cMessageText2</parameterReference>]])
| FROM ARRAY <parameterReference>ArrayName</parameterReference></legacySyntax>
  </syntaxSection>
  <section>
    <title>Arguments</title>
    <content>
      <definitionTable>
        <definedTerm>CREATE TABLE | DBF <legacyItalic>TableName1</legacyItalic></definedTerm>
        <definition>
          <para>Specifies the name of the table to create. The TABLE and DBF options are identical.</para>
        </definition>
        <definedTerm>NAME <legacyItalic>LongTableName</legacyItalic></definedTerm>
        <definition>
          <para>Specifies a long name for the table. A long table name can be specified only when a database is open, because long table names are stored in databases.</para>
          <para>Long names can contain up to 128 characters and can be used in place of short file names in the database. </para>
        </definition>
        <definedTerm>FREE </definedTerm>
        <definition>
          <para>Specifies that the table will not be added to an open database. FREE isn't required if a database isn't open.</para>
        </definition>
        <definedTerm> <legacyItalic>(FieldName1 FieldType </legacyItalic>[( <legacyItalic>nFieldWidth </legacyItalic>[, <legacyItalic>nPrecision</legacyItalic>])] </definedTerm>
        <definition>
          <para>Specifies the field name, field type, field width, and field precision (number of decimal places), respectively.</para>
          <para>             <legacyItalic>FieldType</legacyItalic> is a single letter indicating the field's <legacyLink xlink:href="50b733dc-679a-4b10-bc5d-98bb474dead2">data type</legacyLink>. Some field data types require that you specify <legacyItalic>nFieldWidth </legacyItalic>or <legacyItalic>nPrecision</legacyItalic> or both.   </para>
          <para>             <legacyItalic>nFieldWidth </legacyItalic>and <legacyItalic>nPrecision</legacyItalic> are ignored for D, G, I, L, M, P, T, and Y types. <legacyItalic>nPrecision</legacyItalic> defaults to zero (no decimal places) if <legacyItalic>nPrecision</legacyItalic> isn't included for the B, F, or N types. </para>
        </definition>
        <definedTerm>NULL </definedTerm>
        <definition>
          <para>Allows null values in the field.</para>
        </definition>
        <definedTerm>NOT NULL </definedTerm>
        <definition>
          <para>Prevents null values in the field.</para>
          <para>If you omit NULL and NOT NULL, the current setting of SET NULL determines whether null values are allowed in the field. However, if you omit NULL and NOT NULL and include the PRIMARY KEY or UNIQUE clause, the current setting of SET NULL is ignored and the field defaults to NOT NULL. </para>
        </definition>
        <definedTerm>CHECK <legacyItalic>lExpression1</legacyItalic></definedTerm>
        <definition>
          <para>Specifies a validation rule for the field. <legacyItalic>lExpression1</legacyItalic> can be a user-defined function. Whenever a blank record is appended, the validation rule is checked. An error is generated if the validation rule doesn't allow for a blank field value in an appended record.</para>
        </definition>
        <definedTerm>ERROR <legacyItalic>cMessageText1</legacyItalic></definedTerm>
        <definition>
          <para>Specifies the error message Visual FoxPro displays when the field rule generates an error. The message is displayed only when data is changed within a Browse window or an Edit window.</para>
        </definition>
        <definedTerm>DEFAULT <legacyItalic>eExpression1</legacyItalic></definedTerm>
        <definition>
          <para>Specifies a default value for the field. The data type of <legacyItalic>eExpression1 </legacyItalic>must be the same as the field's data type.</para>
        </definition>
        <definedTerm>PRIMARY KEY </definedTerm>
        <definition>
          <para>Creates a primary index for the field. The primary index tag has the same name as the field.</para>
        </definition>
        <definedTerm>UNIQUE </definedTerm>
        <definition>
          <para>Creates a candidate index for the field. The candidate index tag has the same name as the field.</para>
          <alert class="note">
            <para>Candidate indexes (created by including the UNIQUE option in CREATE TABLE or ALTER TABLE - SQL) are not the same as indexes created with the UNIQUE option in the INDEX command. An index created with the UNIQUE option in the INDEX command allows duplicate index keys; candidate indexes do not allow duplicate index keys. See <legacyLink xlink:href="694e8cf5-2f69-4001-9c1e-b735a4da3aff">INDEX</legacyLink> for additional information on its UNIQUE option.</para>
          </alert>
          <para>Null values and duplicate records are not permitted in a field used for a primary or candidate index. However, Visual FoxPro will not generate an error if you create a primary or candidate index for a field that supports null values. Visual FoxPro will generate an error if you attempt to enter a null or duplicate value into a field used for a primary or candidate index. </para>
        </definition>
        <definedTerm>REFERENCES <legacyItalic>TableName2</legacyItalic>[TAG <legacyItalic>TagName1</legacyItalic>] </definedTerm>
        <definition>
          <para>Specifies the parent table to which a persistent relationship is established. If you omit TAG <legacyItalic>TagName1</legacyItalic>, the relationship is established using the primary index key of the parent table. If the parent table does not have a primary index, Visual FoxPro generates an error.</para>
          <para>Include TAG <legacyItalic>TagName1</legacyItalic> to establish a relation based on an existing index tag for the parent table. Index tag names can contain up to 10 characters.   </para>
          <para>The parent table cannot be a free table. </para>
        </definition>
        <definedTerm>NOCPTRANS </definedTerm>
        <definition>
          <para>Prevents translation to a different code page for character and memo fields. If the table is converted to another code page, the fields for which NOCPTRANS has been specified are not translated. NOCPTRANS can be specified only for character and memo fields.</para>
          <para>The following example creates a table named mytable containing two character fields and two memo fields. The second character field, char2, and the second memo field, memo2, include NOCPTRANS to prevent translation.   </para>
          <code>   CREATE TABLE mytable (char1 C(10), char2 C(10) NOCPTRANS,;
      memo1 M, memo2 M NOCPTRANS)</code>
        </definition>
        <definedTerm>PRIMARY KEY <legacyItalic>eExpression2 </legacyItalic>TAG <legacyItalic>TagName2</legacyItalic></definedTerm>
        <definition>
          <para>Specifies a primary index to create. <legacyItalic>eExpression2</legacyItalic> specifies any field or combination of fields in the table. TAG <legacyItalic>TagName2 s</legacyItalic>pecifies the name for the primary index tag that is created. Index tag names can contain up to 10 characters.</para>
          <para>Because a table can have only one primary index, you cannot include this clause if you have already created a primary index for a field. Visual FoxPro generates an error if you include more than one PRIMARY KEY clause in CREATE TABLE. </para>
        </definition>
        <definedTerm>UNIQUE <legacyItalic>eExpression3</legacyItalic>TAG <legacyItalic>TagName3</legacyItalic></definedTerm>
        <definition>
          <para>Creates a candidate index. <legacyItalic>eExpression3</legacyItalic> specifies any field or combination of fields in the table. However, if you have created a primary index with one of the PRIMARY KEY options, you cannot include the field that was specified for the primary index. TAG <legacyItalic>TagName3 s</legacyItalic>pecifies a tag name for the candidate index tag that is created. Index tag names can contain up to 10 characters.</para>
          <para>A table can have multiple candidate indexes. </para>
        </definition>
        <definedTerm>FOREIGN KEY <legacyItalic>eExpression4</legacyItalic>TAG <legacyItalic>TagName4</legacyItalic>[NODUP] </definedTerm>
        <definition>
          <para>Creates a foreign (nonprimary) index and establishes a relationship to a parent table. <legacyItalic>eExpression4</legacyItalic> specifies the foreign index key expression, and <legacyItalic>TagName4</legacyItalic> specifies the name of the foreign index key tag that is created<legacyItalic>.</legacyItalic> Index tag names can contain up to 10 characters. Include NODUP to create a candidate foreign index.</para>
          <para>You can create multiple foreign indexes for the table, but the foreign index expressions must specify different fields in the table. </para>
        </definition>
        <definedTerm>REFERENCES <legacyItalic>TableName3</legacyItalic>[TAG <legacyItalic>TagName5</legacyItalic>] </definedTerm>
        <definition>
          <para>Specifies the parent table to which a persistent relationship is established. Include TAG <legacyItalic>TagName5</legacyItalic> to establish a relation based on an index tag for the parent table. Index tag names can contain up to 10 characters. By default, if you omit TAG <legacyItalic>TagName5,</legacyItalic> the relationship is established using the parent table's primary index key.</para>
        </definition>
        <definedTerm>CHECK <legacyItalic>eExpression2</legacyItalic>[ERROR <legacyItalic>cMessageText2</legacyItalic>] </definedTerm>
        <definition>
          <para>Specifies the table validation rule. ERROR <legacyItalic>cMessageText2</legacyItalic> specifies the error message Visual FoxPro displays when the table validation rule is executed. The message is displayed only when data is changed within a Browse window or Edit window.</para>
        </definition>
        <definedTerm>FROM ARRAY <legacyItalic>ArrayName</legacyItalic></definedTerm>
        <definition>
          <para>Specifies the name of an existing array whose contents are the name, type, precision, and scale for each field in the table. The contents of the array can be defined with the <legacyBold>AFIELDS</legacyBold>( ) function.</para>
        </definition>
      </definitionTable>
    </content>
  </section>
  <languageReferenceRemarks>
    <content>
      <para>The new table is opened in the lowest available work area and can be accessed by its alias. The new table is opened exclusively, regardless of the current setting of SET EXCLUSIVE.</para>
      <para>If a database is open and you don't include the FREE clause, the new table is added to the database. You cannot create a new table with the same name as a table in the database.</para>
      <para>If a database is open, CREATE TABLE - SQL requires exclusive use of the database. To open a database for exclusive use, include EXCLUSIVE in OPEN DATABASE.</para>
      <para>If a database isn't open when you create the new table, including the NAME, CHECK, DEFAULT, FOREIGN KEY, PRIMARY KEY, or REFERENCES clauses generates an error.</para>
      <alert class="note">
        <para>CREATE TABLE syntax uses commas to separate certain CREATE TABLE options. Also, the NULL, NOT NULL, CHECK, DEFAULT, PRIMARY KEY, and UNIQUE clause must be placed within the parentheses containing the column definitions.</para>
      </alert>
    </content>
  </languageReferenceRemarks>
  <section>
    <title>Driver Remarks</title>
    <content>
      <para>When your application sends the ODBC SQL statement CREATE TABLE to the data source, the Visual FoxPro ODBC Driver translates the command into the Visual FoxProCREATE TABLE command using the syntax shown in the following table.</para>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>ODBC syntax</para>
            </TD>
            <TD>
              <para>Visual FoxPro syntax</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>CREATE TABLE <legacyItalic>base-table-name</legacyItalic> </para>
              <para>(<legacyItalic>column-identifier data type</legacyItalic> </para>
              <para>   [NOT NULL] </para>
              <para>[,<legacyItalic>column-identifier data type</legacyItalic> </para>
              <para>   [NOT NULL] ...)</para>
            </TD>
            <TD>
              <para>CREATE TABLE <legacyItalic>TableName1</legacyItalic> [NAME <legacyItalic>LongTableName</legacyItalic>] </para>
              <para>(<legacyItalic>FieldName1</legacyItalic> <legacyItalic>FieldType</legacyItalic>  </para>
              <para>   [(<legacyItalic>nFieldWidth</legacyItalic> [, <legacyItalic>nPrecision</legacyItalic>])] </para>
              <para>   [NOT NULL])</para>
            </TD>
          </tr>
        </tbody>
      </table>
      <para>When you create a table using the driver, the driver closes the table immediately after creation to allow access to the table by other users. This differs from Visual FoxPro, which leaves the table open exclusively upon creation. However, if a stored procedure on your data source containing a CREATE TABLE statement executes, the table is left open.</para>
      <para>If the data source is a database (.dbc file), the Visual FoxPro ODBC Driver creates a table named <legacyItalic>LongTableName</legacyItalic> with the same name as the <legacyItalic>base-table-name</legacyItalic>.</para>
    </content>
    <sections>
      <section>
        <title>Using Data Definition Language (DDL)</title>
        <content>
          <para>You cannot include DDL in the following places:  </para>
          <list class="bullet">
            <listItem>
              <para>In a batch SQL statement that requires a transaction</para>
            </listItem>
            <listItem>
              <para>In manual-commit mode, after a statement that required a transaction, unless your application first calls <legacyBold>SQLTransact</legacyBold>.</para>
            </listItem>
          </list>
          <para>For example, if you want to create a temporary table, you should create the table before you begin the statement requiring a transaction. If you include the CREATE TABLE statement in a batch SQL statement that requires a transaction, the driver returns an error message.</para>
        </content>
      </section>
    </sections>
  </section>
  <relatedTopics>
<link xlink:href="3a01a291-f4d9-43bc-a725-5a95546ff364">ALTER TABLE - SQL</link>
<link xlink:href="ab529cc6-d157-4b35-b6f9-6ffd09af098c">Supported Data Types</link>
<link xlink:href="9b648198-349f-46f6-b869-13d129945971">INSERT - SQL</link>
<link xlink:href="2149c3ca-3a71-446d-8d53-3d056e2f301a">SELECT - SQL</link>
</relatedTopics>
</developerReferenceWithSyntaxDocument>