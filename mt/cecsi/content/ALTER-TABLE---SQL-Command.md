---
title: ALTER TABLE - SQL Command
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3a01a291-f4d9-43bc-a725-5a95546ff364
manager:jhubbard
translation.priority.ht: 
  - en-gb
---
# ALTER TABLE - SQL Command
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Programmatically modifies the structure of a table.</para>
  </introduction>
  <syntaxSection>
    <legacySyntax>
ALTER TABLE <parameterReference>TableName1</parameterReference>
   ADD | ALTER [COLUMN] <parameterReference>FieldName1</parameterReference>
      <parameterReference>FieldType </parameterReference>[(<parameterReference>nFieldWidth </parameterReference>[, <parameterReference>nPrecision</parameterReference>])]
      [NULL | NOT NULL]
      [CHECK <parameterReference>lExpression1</parameterReference> [ERROR <parameterReference>cMessageText1</parameterReference>]]
      [DEFAULT <parameterReference>eExpression1</parameterReference>]
      [PRIMARY KEY | UNIQUE]
      [REFERENCES <parameterReference>TableName2</parameterReference> [TAG <parameterReference>TagName1</parameterReference>]]
      [NOCPTRANS]
 - Or -
ALTER TABLE <parameterReference>TableName1</parameterReference>
   ALTER [COLUMN] <parameterReference>FieldName2</parameterReference>
      [NULL | NOT NULL]
      [SET DEFAULT <parameterReference>eExpression2</parameterReference>]
      [SET CHECK <parameterReference>lExpression2 </parameterReference>[ERROR <parameterReference>cMessageText2</parameterReference>]]
      [DROP DEFAULT]
      [DROP CHECK]
 - Or -
ALTER TABLE <parameterReference>TableName1</parameterReference>
   [DROP [COLUMN] <parameterReference>FieldName3</parameterReference>]
   [SET CHECK <parameterReference>lExpression3 </parameterReference>[ERROR <parameterReference>cMessageText3</parameterReference>]]
   [DROP CHECK]
   [ADD PRIMARY KEY <parameterReference>eExpression3</parameterReference> TAG <parameterReference>TagName2</parameterReference>]
   [DROP PRIMARY KEY]
   [ADD UNIQUE <parameterReference>eExpression4</parameterReference> [TAG <parameterReference>TagName3</parameterReference>]]
   [DROP UNIQUE TAG <parameterReference>TagName4</parameterReference>]
   [ADD FOREIGN KEY [<parameterReference>eExpression5</parameterReference>] TAG <parameterReference>TagName4</parameterReference>
      REFERENCES <parameterReference>TableName2</parameterReference> [TAG <parameterReference>TagName5</parameterReference>]]
   [DROP FOREIGN KEY TAG <parameterReference>TagName6</parameterReference> [SAVE]]
   [RENAME COLUMN <parameterReference>FieldName4</parameterReference> TO <parameterReference>FieldName5</parameterReference>]
   [NOVALIDATE]</legacySyntax>
  </syntaxSection>
  <section>
    <title>Arguments</title>
    <content>
      <definitionTable>
        <definedTerm> <legacyItalic>TableName1</legacyItalic> </definedTerm>
        <definition>
          <para>Specifies the name of the table whose structure is modified.</para>
        </definition>
        <definedTerm>ADD [COLUMN] <legacyItalic>FieldName1</legacyItalic></definedTerm>
        <definition>
          <para>Specifies the name of the field to add.</para>
        </definition>
        <definedTerm>ALTER [COLUMN] <legacyItalic>FieldName1</legacyItalic></definedTerm>
        <definition>
          <para>Specifies the name of an existing field to modify.</para>
        </definition>
        <definedTerm> <legacyItalic>FieldType </legacyItalic>[( <legacyItalic>nFieldWidth </legacyItalic>[, <legacyItalic>nPrecision</legacyItalic>]]) </definedTerm>
        <definition>
          <para>Specifies the field type, field width, and field precision (number of decimal places) for a new or modified field.</para>
          <para>
            <legacyItalic>FieldType</legacyItalic> is a single letter that indicates the field's <legacyLink xlink:href="50b733dc-679a-4b10-bc5d-98bb474dead2">data type</legacyLink>. Some field data types require that you specify <legacyItalic>nFieldWidth </legacyItalic>or <legacyItalic>nPrecision</legacyItalic> or both.   </para>
          <para>
            <legacyItalic>nFieldWidth </legacyItalic>and <legacyItalic>nPrecision</legacyItalic> are ignored for D, G, I, L, M, P, T, and Y types. By default, <legacyItalic>nPrecision</legacyItalic> is zero (no decimal places) if <legacyItalic>nPrecision</legacyItalic> is not included for the B, F, or N types. </para>
        </definition>
        <definedTerm>NULL | NOT NULL </definedTerm>
        <definition>
          <para>Allows or prevents null values in the field.</para>
          <para>If you omit NULL and NOT NULL, the current setting of SET NULL determines whether null values are allowed in the field. However, if you omit NULL and NOT NULL and include the PRIMARY KEY or UNIQUE clause, the current setting of SET NULL is ignored and the field is NOT NULL by default. </para>
        </definition>
        <definedTerm>CHECK <legacyItalic>lExpression1</legacyItalic></definedTerm>
        <definition>
          <para>Specifies a validation rule for the field. <legacyItalic>lExpression1 </legacyItalic>must evaluate to a logical expression and can be a user-defined function or a stored procedure. Whenever a blank record is appended, the validation rule is checked. An error is generated if the validation rule does not allow for a blank field value in an appended record.</para>
        </definition>
        <definedTerm>ERROR <legacyItalic>cMessageText1</legacyItalic></definedTerm>
        <definition>
          <para>Specifies the error message displayed when the field validation rule generates an error.</para>
        </definition>
        <definedTerm>DEFAULT <legacyItalic>eExpression1</legacyItalic></definedTerm>
        <definition>
          <para>Specifies a default value for the field. The data type of <legacyItalic>eExpression1</legacyItalic> must be the same as the data type for the field.</para>
        </definition>
        <definedTerm>PRIMARY KEY </definedTerm>
        <definition>
          <para>Creates a primary index tag. The index tag has the same name as the field.</para>
        </definition>
        <definedTerm>UNIQUE </definedTerm>
        <definition>
          <para>Creates a candidate index tag with the same name as the field.</para>
          <alert class="note">
            <para>Candidate indexes (created by including the UNIQUE option, provided for ANSI compatibility in ALTER TABLE or CREATE TABLE) differ from indexes created by using the UNIQUE option in the INDEX command. An index created by using UNIQUE in the INDEX command allows duplicate index keys; candidate indexes do not allow duplicate index keys.</para>
          </alert>
          <para>Null values and duplicate records are not permitted in a field that is used for a primary or candidate index.   </para>
          <para>If you are creating a new field by using ADD COLUMN, Visual FoxPro will not generate an error if you create a primary or candidate index for a field that supports null values. However, Visual FoxPro will generate an error if you try to enter a null or duplicate value into a field that is used for a primary or candidate index.   </para>
          <para>If you are modifying an existing field and the primary or candidate index expression consists of fields in the table, Visual FoxPro checks the fields to see whether they contain null values or duplicate records. If they do, Visual FoxPro generates an error and the table is not altered. </para>
        </definition>
        <definedTerm>REFERENCES <legacyItalic>TableName2 </legacyItalic>TAG <legacyItalic>TagName1</legacyItalic></definedTerm>
        <definition>
          <para>Specifies the parent table to which a persistent relationship is established. TAG <legacyItalic>TagName1</legacyItalic> specifies the parent table's index tag on which the relationship is based. Index tag names can contain up to 10 characters.</para>
        </definition>
        <definedTerm>NOCPTRANS </definedTerm>
        <definition>
          <para>Prevents translation to a different code page for character and memo fields. If the table is converted to another code page, the fields for which NOCPTRANS has been specified are not translated. NOCPTRANS can be specified only for character and memo fields.</para>
          <para>The following example creates a table named mytable that contains two character fields and two memo fields. The second character field, char2, and the second memo field, memo2, include NOCPTRANS to prevent translation.   </para>
          <code>CREATE TABLE mytable (char1 C(10), char2 C(10) NOCPTRANS,;
   memo1 M, memo2 M NOCPTRANS)</code>
        </definition>
        <definedTerm>ALTER [COLUMN] <legacyItalic>FieldName2</legacyItalic></definedTerm>
        <definition>
          <para>Specifies the name of an existing field to modify.</para>
        </definition>
        <definedTerm>SET DEFAULT <legacyItalic>eExpression2</legacyItalic></definedTerm>
        <definition>
          <para>Specifies a new default value for an existing field. The data type of <legacyItalic>eExpression2 </legacyItalic>must be the same as the data type for the field.</para>
        </definition>
        <definedTerm>SET CHECK <legacyItalic>lExpression2</legacyItalic></definedTerm>
        <definition>
          <para>Specifies a new validation rule for an existing field. <legacyItalic>lExpression2 </legacyItalic>must evaluate to a logical expression and may be a user-defined function or a stored procedure.</para>
        </definition>
        <definedTerm>ERROR <legacyItalic>cMessageText2</legacyItalic></definedTerm>
        <definition>
          <para>Specifies the error message displayed when the field validation rule generates an error. The message is displayed only when data is changed within a Browse or Edit window.</para>
        </definition>
        <definedTerm>DROP DEFAULT </definedTerm>
        <definition>
          <para>Removes the default value for an existing field.</para>
        </definition>
        <definedTerm>DROP CHECK </definedTerm>
        <definition>
          <para>Removes the validation rule for an existing field.</para>
        </definition>
        <definedTerm>DROP [COLUMN] <legacyItalic>FieldName3</legacyItalic></definedTerm>
        <definition>
          <para>Specifies a field to remove from the table. Removing a field from the table also removes the field's default value setting and field validation rule.</para>
          <para>If index key or trigger expressions reference the field, the expressions become invalid when the field is removed. In this case, an error is not generated when the field is removed but the invalid index key or trigger expressions will generate errors at run time. </para>
        </definition>
        <definedTerm>SET CHECK <legacyItalic>lExpression3</legacyItalic></definedTerm>
        <definition>
          <para>Specifies the table validation rule. <legacyItalic>lExpression3 </legacyItalic>must evaluate to a logical expression and may be a user-defined function or a stored procedure.</para>
        </definition>
        <definedTerm>ERROR <legacyItalic>cMessageText3</legacyItalic></definedTerm>
        <definition>
          <para>Specifies the error message displayed when the table validation rule generates an error. The message is displayed only when data is changed within a Browse or Edit window.</para>
        </definition>
        <definedTerm>DROP CHECK </definedTerm>
        <definition>
          <para>Removes the table's validation rule.</para>
        </definition>
        <definedTerm>ADD PRIMARY KEY <legacyItalic>eExpression3</legacyItalic>TAG <legacyItalic>TagName2</legacyItalic></definedTerm>
        <definition>
          <para>Adds a primary index to the table. <legacyItalic>eExpression3</legacyItalic> specifies the primary index key expression, and <legacyItalic>TagName2</legacyItalic> specifies the name of the primary index tag. Index tag names can contain up to 10 characters. If TAG <legacyItalic>TagName2</legacyItalic> is omitted and <legacyItalic>eExpression3</legacyItalic> is a single field, the primary index tag has the same name as the field specified in <legacyItalic>eExpression3</legacyItalic>.</para>
        </definition>
        <definedTerm>DROP PRIMARY KEY </definedTerm>
        <definition>
          <para>Removes the primary index and its index tag. Because a table can have only one primary key, it is not necessary to specify the name of the primary key. Removing the primary index also deletes any persistent relations based on the primary key.</para>
        </definition>
        <definedTerm>ADD UNIQUE <legacyItalic>eExpression4</legacyItalic>[TAG <legacyItalic>TagName3</legacyItalic>] </definedTerm>
        <definition>
          <para>Adds a candidate index to the table. <legacyItalic>eExpression4</legacyItalic> specifies the candidate index key expression, and <legacyItalic>TagName3</legacyItalic> specifies the name of the candidate index tag. Index tag names can contain up to 10 characters. If you omit TAG <legacyItalic>TagName3</legacyItalic> and if <legacyItalic>eExpression4</legacyItalic> is a single field, the candidate index tag has the same name as the field specified in <legacyItalic>eExpression4</legacyItalic>.</para>
        </definition>
        <definedTerm>DROP UNIQUE TAG <legacyItalic>TagName4</legacyItalic></definedTerm>
        <definition>
          <para>Removes the candidate index and its index tag. Because a table can have multiple candidate keys, you must specify the name of the candidate index tag.</para>
        </definition>
        <definedTerm>ADD FOREIGN KEY [ <legacyItalic>eExpression5</legacyItalic>]TAG <legacyItalic>TagName4</legacyItalic></definedTerm>
        <definition>
          <para>Adds a foreign (nonprimary) index to the table. <legacyItalic>eExpression5 </legacyItalic>specifies the foreign index key expression, and <legacyItalic>TagName4</legacyItalic> specifies the name of the foreign index tag. Index tag names can contain up to 10 characters.</para>
        </definition>
        <definedTerm>REFERENCES <legacyItalic>TableName2</legacyItalic>[TAG <legacyItalic>TagName5</legacyItalic>] </definedTerm>
        <definition>
          <para>Specifies the parent table to which a persistent relationship is established. Include TAG <legacyItalic>TagName5</legacyItalic> to establish a relation based on an existing index tag for the parent table. Index tag names can contain up to 10 characters. If you omit TAG <legacyItalic>TagName5</legacyItalic>, the relationship is established using the parent table's primary index tag.</para>
        </definition>
        <definedTerm>DROP FOREIGN KEY TAG <legacyItalic>TagName6</legacyItalic>[SAVE] </definedTerm>
        <definition>
          <para>Deletes a foreign key whose index tag is <legacyItalic>TagName6</legacyItalic>. If you omit SAVE, the index tag is deleted from the structural index. Include SAVE to prevent deletion of the index tag from the structural index.</para>
        </definition>
        <definedTerm>RENAME COLUMN <legacyItalic>FieldName4</legacyItalic>TO <legacyItalic>FieldName5</legacyItalic></definedTerm>
        <definition>
          <para>Allows you to change the name of a field in the table. <legacyItalic>FieldName4</legacyItalic> specifies the name of the field that is renamed. <legacyItalic>FieldName5</legacyItalic> specifies the new name of the field.</para>
          <alert class="caution">
            <para>Exercise care when renaming table fields because index expressions, field and table validation rules, commands, and functions may reference the original field names.</para>
          </alert>
        </definition>
        <definedTerm>NOVALIDATE </definedTerm>
        <definition>
          <para>Specifies that Visual FoxPro allows changes to be made to the structure of the table; these changes might violate the integrity of the data in the table. By default, Visual FoxPro prevents ALTER TABLE from making changes that violate the integrity of the data in the table. Include NOVALIDATE to override this default behavior.</para>
        </definition>
      </definitionTable>
    </content>
  </section>
  <languageReferenceRemarks>
    <content>
      <para>ALTER TABLE can be used to modify the structure of a table that has not been added to a database. However, Visual FoxPro generates an error if you include the DEFAULT, FOREIGN KEY, PRIMARY KEY, REFERENCES, or SET clauses when modifying a free table.</para>
      <para>ALTER TABLE may rebuild the table by creating a new table header and appending records to the table header. For example, changing a field's type or width might cause the table to be rebuilt.</para>
      <para>After a table is rebuilt, field validation rules are executed for any fields whose type or width is changed. If you change the type or width of any field in the table, the table rule is executed.</para>
      <para>If you modify field or table validation rules for a table that has records, Visual FoxPro tests the new field or table validation rules against the existing data and issues a warning on the first occurrence of a field or table validation rule or of a trigger violation.</para>
      <para>If the table you modify is in a database, ALTER TABLE - SQL requires exclusive use of the database. To open a database for exclusive use, include EXCLUSIVE in OPEN DATABASE.</para>
    </content>
  </languageReferenceRemarks>
  <relatedTopics>
<link xlink:href="be2143ba-fc16-42c9-84f7-8985cd924860">CREATE TABLE - SQL</link>
<link xlink:href="694e8cf5-2f69-4001-9c1e-b735a4da3aff">INDEX</link>
</relatedTopics>
</developerReferenceWithSyntaxDocument>