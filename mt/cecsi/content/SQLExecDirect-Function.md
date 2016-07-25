---
title: "SQLExecDirect Function"
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
apiname: 
  - SQLExecDirect
apilocation: 
  - sqlsrv32.dll
apitype: dllExport
ms.assetid: 985fcee1-f204-425c-bdd1-deb0e7d7bbd9
caps.latest.revision: 25
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# SQLExecDirect Function
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <definitionTable>
      <definedTerm>
        <legacyBold>Conformance</legacyBold>
      </definedTerm>
      <definition>
        <para>Version Introduced: ODBC 1.0 Standards Compliance: ISO 92</para>
      </definition>
      <definedTerm>
        <legacyBold>Summary</legacyBold>
      </definedTerm>
      <definition>
        <para>
          <legacyBold>SQLExecDirect</legacyBold> executes a preparable statement, using the current values of the parameter marker variables if any parameters exist in the statement. <legacyBold>SQLExecDirect</legacyBold> is the fastest way to submit an SQL statement for one-time execution.</para>
      </definition>
    </definitionTable>
  </introduction>
  <syntaxSection>
    <legacySyntax>
SQLRETURN <legacyBold>SQLExecDirect</legacyBold>(
     SQLHSTMT     <parameterReference>StatementHandle</parameterReference>,
     SQLCHAR *    <parameterReference>StatementText</parameterReference>,
     SQLINTEGER   <parameterReference>TextLength</parameterReference>);</legacySyntax>
  </syntaxSection>
  <section>
    <title>Arguments</title>
    <content>
      <definitionTable>
        <definedTerm>
          <legacyItalic>StatementHandle</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] Statement handle.</para>
        </definition>
        <definedTerm>
          <legacyItalic>StatementText</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] SQL statement to be executed.</para>
        </definition>
        <definedTerm>
          <legacyItalic>TextLength</legacyItalic>
        </definedTerm>
        <definition>
          <para>[Input] Length of *<legacyItalic>StatementText</legacyItalic> in characters.</para>
        </definition>
      </definitionTable>
    </content>
  </section>
  <section>
    <title>Returns</title>
    <content>
      <para>SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_NEED_DATA, SQL_STILL_EXECUTING, SQL_ERROR, SQL_NO_DATA, SQL_INVALID_HANDLE, or SQL_PARAM_DATA_AVAILABLE.</para>
    </content>
  </section>
  <section>
    <title>Diagnostics</title>
    <content>
      <para>When <legacyBold>SQLExecDirect</legacyBold> returns either SQL_ERROR or SQL_SUCCESS_WITH_INFO, an associated SQLSTATE value can be obtained by calling <legacyBold>SQLGetDiagRec</legacyBold> with a <legacyItalic>HandleType</legacyItalic> of SQL_HANDLE_STMT and a <legacyItalic>Handle</legacyItalic> of <legacyItalic>StatementHandle</legacyItalic>. The following table lists the SQLSTATE values commonly returned by <legacyBold>SQLExecDirect</legacyBold> and explains each one in the context of this function; the notation "(DM)" precedes the descriptions of SQLSTATEs returned by the Driver Manager. The return code associated with each SQLSTATE value is SQL_ERROR, unless noted otherwise.</para>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>SQLSTATE</para>
            </TD>
            <TD>
              <para>Error</para>
            </TD>
            <TD>
              <para>Description</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>01000</para>
            </TD>
            <TD>
              <para>General warning</para>
            </TD>
            <TD>
              <para>Driver-specific informational message. (Function returns SQL_SUCCESS_WITH_INFO.)</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>01001</para>
            </TD>
            <TD>
              <para>Cursor operation conflict</para>
            </TD>
            <TD>
              <para>*<legacyItalic>StatementText</legacyItalic> contained a positioned update or delete statement, and no rows or more than one row were updated or deleted. (For more information about updates to more than one row, see the description of the SQL_ATTR_SIMULATE_CURSOR <legacyItalic>Attribute</legacyItalic> in <legacyBold>SQLSetStmtAttr</legacyBold>.) </para>
              <para>(Function returns SQL_SUCCESS_WITH_INFO.)</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>01003</para>
            </TD>
            <TD>
              <para>NULL value eliminated in set function</para>
            </TD>
            <TD>
              <para>The argument <legacyItalic>StatementText</legacyItalic> contained a set function (such as <legacyBold>AVG</legacyBold>, <legacyBold>MAX</legacyBold>, <legacyBold>MIN</legacyBold>, and so on), but not the <legacyBold>COUNT</legacyBold> set function, and NULL argument values were eliminated before the function was applied. (Function returns SQL_SUCCESS_WITH_INFO.)</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>01004</para>
            </TD>
            <TD>
              <para>String data, right truncated</para>
            </TD>
            <TD>
              <para>String or binary data returned for an input/output or output parameter resulted in the truncation of nonblank character or non-NULL binary data. If it was a string value, it was right-truncated. (Function returns SQL_SUCCESS_WITH_INFO.)</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>01006</para>
            </TD>
            <TD>
              <para>Privilege not revoked</para>
            </TD>
            <TD>
              <para>*<legacyItalic>StatementText</legacyItalic> contained a <legacyBold>REVOKE</legacyBold> statement, and the user did not have the specified privilege. (Function returns SQL_SUCCESS_WITH_INFO.)</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>01007</para>
            </TD>
            <TD>
              <para>Privilege not granted</para>
            </TD>
            <TD>
              <para>
                <legacyItalic>*StatementText</legacyItalic> was a <legacyBold>GRANT </legacyBold>statement, and the user could not be granted the specified privilege.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>01S02</para>
            </TD>
            <TD>
              <para>Option value changed</para>
            </TD>
            <TD>
              <para>A specified statement attribute was invalid because of implementation working conditions, so a similar value was temporarily substituted. (<legacyBold>SQLGetStmtAttr</legacyBold> can be called to determine what the temporarily substituted value is.) The substitute value is valid for the <legacyItalic>StatementHandle</legacyItalic> until the cursor is closed, at which point the statement attribute reverts to its previous value. The statement attributes that can be changed are: </para>
              <para>SQL_ ATTR_CONCURRENCY SQL_ ATTR_CURSOR_TYPE SQL_ ATTR_KEYSET_SIZE SQL_ ATTR_MAX_LENGTH SQL_ ATTR_MAX_ROWS SQL_ ATTR_QUERY_TIMEOUT  SQL_ ATTR_SIMULATE_CURSOR </para>
              <para>(Function returns SQL_SUCCESS_WITH_INFO.)</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>01S07</para>
            </TD>
            <TD>
              <para>Fractional truncation</para>
            </TD>
            <TD>
              <para>The data returned for an input/output or output parameter was truncated such that the fractional part of a numeric data type was truncated or the fractional portion of the time component of a time, timestamp, or interval data type was truncated. </para>
              <para>(Function returns SQL_SUCCESS_WITH_INFO.)</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>07002</para>
            </TD>
            <TD>
              <para>COUNT field incorrect</para>
            </TD>
            <TD>
              <para>The number of parameters specified in <legacyBold>SQLBindParameter</legacyBold> was less than the number of parameters in the SQL statement contained in *<legacyItalic>StatementText</legacyItalic>.</para>
              <para>
                <legacyBold>SQLBindParameter</legacyBold> was called with <legacyItalic>ParameterValuePtr</legacyItalic> set to a null pointer, <legacyItalic>StrLen_or_IndPtr</legacyItalic> not set to SQL_NULL_DATA or SQL_DATA_AT_EXEC, and <legacyItalic>InputOutputType</legacyItalic> not set to SQL_PARAM_OUTPUT, so that the number of parameters specified in <legacyBold>SQLBindParameter</legacyBold> was greater than the number of parameters in the SQL statement contained in *<legacyItalic>StatementText</legacyItalic>.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>07006</para>
            </TD>
            <TD>
              <para>Restricted data type attribute violation</para>
            </TD>
            <TD>
              <para>The data value identified by the <legacyItalic>ValueType</legacyItalic> argument in <legacyBold>SQLBindParameter</legacyBold> for the bound parameter could not be converted to the data type identified by the <legacyItalic>ParameterType</legacyItalic> argument in <legacyBold>SQLBindParameter</legacyBold>.</para>
              <para>The data value returned for a parameter bound as SQL_PARAM_INPUT_OUTPUT or SQL_PARAM_OUTPUT could not be converted to the data type identified by the <legacyItalic>ValueType</legacyItalic> argument in <legacyBold>SQLBindParameter</legacyBold>.</para>
              <para>(If the data values for one or more rows could not be converted but one or more rows were successfully returned, this function returns SQL_SUCCESS_WITH_INFO.)</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>07007</para>
            </TD>
            <TD>
              <para>Restricted parameter value violation</para>
            </TD>
            <TD>
              <para>The parameter type SQL_PARAM_INPUT_OUTPUT_STREAM is only used for a parameter that sends and receives data in parts. An input bound buffer is not allowed for this parameter type.</para>
              <para>This error will occur when the parameter type is SQL_PARAM_INPUT_OUTPUT, and when the *<parameterReference>StrLen_or_IndPtr</parameterReference> specified in <unmanagedCodeEntityReference>SQLBindParameter</unmanagedCodeEntityReference> is not equal to SQL_NULL_DATA, SQL_DEFAULT_PARAM, SQL_LEN_DATA_AT_EXEC(len), or SQL_DATA_AT_EXEC.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>07S01</para>
            </TD>
            <TD>
              <para>Invalid use of default parameter</para>
            </TD>
            <TD>
              <para>A parameter value, set with <legacyBold>SQLBindParameter</legacyBold>, was SQL_DEFAULT_PARAM, and the corresponding parameter did not have a default value.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>08S01</para>
            </TD>
            <TD>
              <para>Communication link failure</para>
            </TD>
            <TD>
              <para>The communication link between the driver and the data source to which the driver was connected failed before the function completed processing.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>21S01</para>
            </TD>
            <TD>
              <para>Insert value list does not match column list</para>
            </TD>
            <TD>
              <para>*<legacyItalic>StatementText</legacyItalic> contained an <legacyBold>INSERT</legacyBold> statement, and the number of values to be inserted did not match the degree of the derived table.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>21S02</para>
            </TD>
            <TD>
              <para>Degree of derived table does not match column list</para>
            </TD>
            <TD>
              <para>*<legacyItalic>StatementText</legacyItalic> contained a <legacyBold>CREATE VIEW</legacyBold> statement, and the unqualified column list (the number of columns specified for the view in the <legacyItalic>column-identifier</legacyItalic> arguments of the SQL statement) contained more names than the number of columns in the derived table defined by the <legacyItalic>query-specification</legacyItalic> argument of the SQL statement.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>22001</para>
            </TD>
            <TD>
              <para>String data, right truncation</para>
            </TD>
            <TD>
              <para>The assignment of a character or binary value to a column resulted in the truncation of nonblank character data or non-null binary data.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>22002</para>
            </TD>
            <TD>
              <para>Indicator variable required but not supplied</para>
            </TD>
            <TD>
              <para>NULL data was bound to an output parameter whose <legacyItalic>StrLen_or_IndPtr</legacyItalic> set by <legacyBold>SQLBindParameter</legacyBold> was a null pointer.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>22003</para>
            </TD>
            <TD>
              <para>Numeric value out of range</para>
            </TD>
            <TD>
              <para>*<legacyItalic>StatementText</legacyItalic> contained an SQL statement that contained a bound numeric parameter or literal, and the value caused the whole (as opposed to fractional) part of the number to be truncated when assigned to the associated table column.</para>
              <para>Returning a numeric value (as numeric or string) for one or more input/output or output parameters would have caused the whole (as opposed to fractional) part of the number to be truncated.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>22007</para>
            </TD>
            <TD>
              <para>Invalid datetime format</para>
            </TD>
            <TD>
              <para>*<legacyItalic>StatementText</legacyItalic> contained an SQL statement that contained a date, time, or timestamp structure as a bound parameter, and the parameter was, respectively, an invalid date, time, or timestamp.</para>
              <para>An input/output or output parameter was bound to a date, time, or timestamp C structure, and a value in the returned parameter was, respectively, an invalid date, time, or timestamp. (Function returns SQL_SUCCESS_WITH_INFO.)</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>22008</para>
            </TD>
            <TD>
              <para>Datetime field overflow</para>
            </TD>
            <TD>
              <para>*<legacyItalic>StatementText</legacyItalic> contained an SQL statement that contained a datetime expression that, when computed, resulted in a date, time, or timestamp structure that was invalid. </para>
              <para>A datetime expression computed for an input/output or output parameter resulted in a date, time, or timestamp C structure that was invalid.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>22012</para>
            </TD>
            <TD>
              <para>Division by zero</para>
            </TD>
            <TD>
              <para>*<legacyItalic>StatementText</legacyItalic> contained an SQL statement that contained an arithmetic expression that caused division by zero.</para>
              <para>An arithmetic expression calculated for an input/output or output parameter resulted in division by zero.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>22015</para>
            </TD>
            <TD>
              <para>Interval field overflow</para>
            </TD>
            <TD>
              <para>
                <legacyItalic>*StatementText</legacyItalic> contained an exact numeric or interval parameter that, when converted to an interval SQL data type, caused a loss of significant digits.</para>
              <para>
                <legacyItalic>*StatementText</legacyItalic> contained an interval parameter with more than one field that, when converted to a numeric data type in a column, had no representation in the numeric data type.</para>
              <para>
                <legacyItalic>*StatementText</legacyItalic> contained parameter data that was assigned to an interval SQL type, and there was no representation of the value of the C type in the interval SQL type.</para>
              <para>Assigning an input/output or output parameter that was an exact numeric or interval SQL type to an interval C type caused a loss of significant digits.</para>
              <para>When an input/output or output parameter was assigned to an interval C structure, there was no representation of the data in the interval data structure.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>22018</para>
            </TD>
            <TD>
              <para>Invalid character value for cast specification</para>
            </TD>
            <TD>
              <para>
                <legacyItalic>*StatementText</legacyItalic> contained a C type that was an exact or approximate numeric, a datetime, or an interval data type; the SQL type of the column was a character data type; and the value in the column was not a valid literal of the bound C type.</para>
              <para>When an input/output or output parameter was returned, the SQL type was an exact or approximate numeric, a datetime, or an interval data type; the C type was SQL_C_CHAR; and the value in the column was not a valid literal of the bound SQL type.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>22019</para>
            </TD>
            <TD>
              <para>Invalid escape character</para>
            </TD>
            <TD>
              <para>*<legacyItalic>StatementText</legacyItalic> contained an SQL statement that contained a <legacyBold>LIKE</legacyBold> predicate with an <legacyBold>ESCAPE</legacyBold> in the <legacyBold>WHERE</legacyBold> clause, and the length of the escape character following <legacyBold>ESCAPE</legacyBold> was not equal to 1.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>22025</para>
            </TD>
            <TD>
              <para>Invalid escape sequence</para>
            </TD>
            <TD>
              <para>*<legacyItalic>StatementText</legacyItalic> contained an SQL statement that contained "<legacyBold>LIKE</legacyBold> <legacyItalic>pattern value</legacyItalic> <legacyBold>ESCAPE</legacyBold> <legacyItalic>escape character</legacyItalic>" in the <legacyBold>WHERE</legacyBold> clause, and the character following the escape character in the pattern value was not one of "%" or "_".</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>23000</para>
            </TD>
            <TD>
              <para>Integrity constraint violation</para>
            </TD>
            <TD>
              <para>*<legacyItalic>StatementText</legacyItalic> contained an SQL statement that contained a parameter or literal. The parameter value was NULL for a column defined as NOT NULL in the associated table column, a duplicate value was supplied for a column constrained to contain only unique values, or some other integrity constraint was violated.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>24000</para>
            </TD>
            <TD>
              <para>Invalid cursor state</para>
            </TD>
            <TD>
              <para>A cursor was positioned on the <legacyItalic>StatementHandle</legacyItalic> by <legacyBold>SQLFetch</legacyBold> or <legacyBold>SQLFetchScroll</legacyBold>. This error is returned by the Driver Manager if <legacyBold>SQLFetch</legacyBold> or <legacyBold>SQLFetchScroll</legacyBold> has not returned SQL_NO_DATA, and is returned by the driver if <legacyBold>SQLFetch</legacyBold> or <legacyBold>SQLFetchScroll</legacyBold> has returned SQL_NO_DATA.</para>
              <para>A cursor was open but not positioned on the <legacyItalic>StatementHandle</legacyItalic>.</para>
              <para>*<legacyItalic>StatementText</legacyItalic> contained a positioned update or delete statement, and the cursor was positioned before the start of the result set or after the end of the result set.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>34000</para>
            </TD>
            <TD>
              <para>Invalid cursor name</para>
            </TD>
            <TD>
              <para>*<legacyItalic>StatementText</legacyItalic> contained a positioned update or delete statement, and the cursor referenced by the statement being executed was not open.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>3D000</para>
            </TD>
            <TD>
              <para>Invalid catalog name</para>
            </TD>
            <TD>
              <para>The catalog name specified in <legacyItalic>StatementText</legacyItalic> was invalid.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>3F000</para>
            </TD>
            <TD>
              <para>Invalid schema name</para>
            </TD>
            <TD>
              <para>The schema name specified in <legacyItalic>StatementText</legacyItalic> was invalid.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>40001</para>
            </TD>
            <TD>
              <para>Serialization failure</para>
            </TD>
            <TD>
              <para>The transaction was rolled back due to a resource deadlock with another transaction.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>40003</para>
            </TD>
            <TD>
              <para>Statement completion unknown</para>
            </TD>
            <TD>
              <para>The associated connection failed during the execution of this function, and the state of the transaction cannot be determined.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>42000</para>
            </TD>
            <TD>
              <para>Syntax error or access violation</para>
            </TD>
            <TD>
              <para>*<legacyItalic>StatementText</legacyItalic> contained an SQL statement that was not preparable or contained a syntax error.</para>
              <para>The user did not have permission to execute the SQL statement contained in *<legacyItalic>StatementText</legacyItalic>.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>42S01</para>
            </TD>
            <TD>
              <para>Base table or view already exists</para>
            </TD>
            <TD>
              <para>*<legacyItalic>StatementText</legacyItalic> contained a <legacyBold>CREATE TABLE</legacyBold> or <legacyBold>CREATE VIEW</legacyBold> statement, and the table name or view name specified already exists.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>42S02</para>
            </TD>
            <TD>
              <para>Base table or view not found</para>
            </TD>
            <TD>
              <para>*<legacyItalic>StatementText</legacyItalic> contained a <legacyBold>DROP TABLE</legacyBold> or a <legacyBold>DROP VIEW</legacyBold> statement, and the specified table name or view name did not exist.</para>
              <para>*<legacyItalic>StatementText</legacyItalic> contained an <legacyBold>ALTER TABLE</legacyBold> statement, and the specified table name did not exist.</para>
              <para>*<legacyItalic>StatementText</legacyItalic> contained a <legacyBold>CREATE VIEW</legacyBold> statement, and a table name or view name defined by the query specification did not exist.</para>
              <para>*<legacyItalic>StatementText</legacyItalic> contained a <legacyBold>CREATE INDEX</legacyBold> statement, and the specified table name did not exist.</para>
              <para>*<legacyItalic>StatementText</legacyItalic> contained a <legacyBold>GRANT</legacyBold> or <legacyBold>REVOKE</legacyBold> statement, and the specified table name or view name did not exist.</para>
              <para>*<legacyItalic>StatementText</legacyItalic> contained a <legacyBold>SELECT</legacyBold> statement, and a specified table name or view name did not exist.</para>
              <para>*<legacyItalic>StatementText</legacyItalic> contained a <legacyBold>DELETE</legacyBold>, <legacyBold>INSERT</legacyBold>, or <legacyBold>UPDATE</legacyBold> statement, and the specified table name did not exist.</para>
              <para>*<legacyItalic>StatementText</legacyItalic> contained a <legacyBold>CREATE TABLE</legacyBold> statement, and a table specified in a constraint (referencing a table other than the one being created) did not exist.</para>
              <para>*<legacyItalic>StatementText</legacyItalic> contained a <legacyBold>CREATE SCHEMA</legacyBold> statement, and a specified table name or view name did not exist.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>42S11</para>
            </TD>
            <TD>
              <para>Index already exists</para>
            </TD>
            <TD>
              <para>*<legacyItalic>StatementText</legacyItalic> contained a <legacyBold>CREATE INDEX</legacyBold> statement, and the specified index name already existed.</para>
              <para>*<legacyItalic>StatementText</legacyItalic> contained a <legacyBold>CREATE SCHEMA</legacyBold> statement, and the specified index name already existed.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>42S12</para>
            </TD>
            <TD>
              <para>Index not found</para>
            </TD>
            <TD>
              <para>*<legacyItalic>StatementText</legacyItalic> contained a <legacyBold>DROP INDEX</legacyBold> statement, and the specified index name did not exist.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>42S21</para>
            </TD>
            <TD>
              <para>Column already exists</para>
            </TD>
            <TD>
              <para>*<legacyItalic>StatementText</legacyItalic> contained an <legacyBold>ALTER TABLE</legacyBold> statement, and the column specified in the <legacyBold>ADD</legacyBold> clause is not unique or identifies an existing column in the base table.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>42S22</para>
            </TD>
            <TD>
              <para>Column not found</para>
            </TD>
            <TD>
              <para>*<legacyItalic>StatementText</legacyItalic> contained a <legacyBold>CREATE INDEX</legacyBold> statement, and one or more of the column names specified in the column list did not exist.</para>
              <para>*<legacyItalic>StatementText</legacyItalic> contained a <legacyBold>GRANT</legacyBold> or <legacyBold>REVOKE</legacyBold> statement, and a specified column name did not exist.</para>
              <para>*<legacyItalic>StatementText</legacyItalic> contained a <legacyBold>SELECT</legacyBold>, <legacyBold>DELETE</legacyBold>, <legacyBold>INSERT</legacyBold>, or <legacyBold>UPDATE</legacyBold> statement, and a specified column name did not exist.</para>
              <para>*<legacyItalic>StatementText</legacyItalic> contained a <legacyBold>CREATE TABLE</legacyBold> statement, and a column specified in a constraint (referencing a table other than the one being created) did not exist.</para>
              <para>*<legacyItalic>StatementText</legacyItalic> contained a <legacyBold>CREATE SCHEMA</legacyBold> statement, and a specified column name did not exist.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>44000</para>
            </TD>
            <TD>
              <para>WITH CHECK OPTION violation</para>
            </TD>
            <TD>
              <para>The argument <legacyItalic>StatementText</legacyItalic> contained an <legacyBold>INSERT</legacyBold> statement performed on a viewed table or a table derived from the viewed table that was created by specifying <legacyBold>WITH CHECK OPTION</legacyBold>, such that one or more rows affected by the <legacyBold>INSERT</legacyBold> statement will no longer be present in the viewed table.</para>
              <para>The argument <legacyItalic>StatementText</legacyItalic> contained an <legacyBold>UPDATE</legacyBold> statement performed on a viewed table or a table derived from the viewed table that was created by specifying <legacyBold>WITH CHECK OPTION</legacyBold>, such that one or more rows affected by the <legacyBold>UPDATE</legacyBold> statement will no longer be present in the viewed table.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>HY000</para>
            </TD>
            <TD>
              <para>General error</para>
            </TD>
            <TD>
              <para>An error occurred for which there was no specific SQLSTATE and for which no implementation-specific SQLSTATE was defined. The error message returned by <legacyBold>SQLGetDiagRec</legacyBold> in the <legacyItalic>*MessageText</legacyItalic> buffer describes the error and its cause.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>HY001</para>
            </TD>
            <TD>
              <para>Memory allocation error</para>
            </TD>
            <TD>
              <para>The driver was unable to allocate memory required to support execution or completion of the function.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>HY008</para>
            </TD>
            <TD>
              <para>Operation canceled</para>
            </TD>
            <TD>
              <para>Asynchronous processing was enabled for the <legacyItalic>StatementHandle</legacyItalic>. The function was called, and before it completed execution, <legacyBold>SQLCancel</legacyBold> or <legacyBold>SQLCancelHandle</legacyBold> was called on the <legacyItalic>StatementHandle</legacyItalic>. Then the function was called again on the <legacyItalic>StatementHandle</legacyItalic>.</para>
              <para>The function was called, and before it completed execution, <legacyBold>SQLCancel</legacyBold> or <legacyBold>SQLCancelHandle</legacyBold> was called on the <legacyItalic>StatementHandle</legacyItalic> from a different thread in a multithread application.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>HY009</para>
            </TD>
            <TD>
              <para>Invalid use of null pointer</para>
            </TD>
            <TD>
              <para>(DM) *<legacyItalic>StatementText</legacyItalic> was a null pointer.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>HY010</para>
            </TD>
            <TD>
              <para>Function sequence error</para>
            </TD>
            <TD>
              <para>(DM) An asynchronously executing function was called for the connection handle that is associated with the <legacyItalic>StatementHandle</legacyItalic>. This asynchronous function was still executing when the <unmanagedCodeEntityReference>SQLExecDirect</unmanagedCodeEntityReference> function was called.</para>
              <para>(DM) <unmanagedCodeEntityReference>SQLExecute</unmanagedCodeEntityReference>, <unmanagedCodeEntityReference>SQLExecDirect</unmanagedCodeEntityReference>, or <unmanagedCodeEntityReference>SQLMoreResults</unmanagedCodeEntityReference> was called for the <parameterReference>StatementHandle</parameterReference> and returned SQL_PARAM_DATA_AVAILABLE. This function was called before data was retrieved for all streamed parameters.</para>
              <para>(DM) An asynchronously executing function (not this one) was called for the <legacyItalic>StatementHandle</legacyItalic> and was still executing when this function was called.</para>
              <para>(DM) <legacyBold>SQLExecute</legacyBold>, <legacyBold>SQLExecDirect</legacyBold>, <legacyBold>SQLBulkOperations</legacyBold>, or <legacyBold>SQLSetPos</legacyBold> was called for the <legacyItalic>StatementHandle</legacyItalic> and returned SQL_NEED_DATA. This function was called before data was sent for all data-at-execution parameters or columns.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>HY013</para>
            </TD>
            <TD>
              <para>Memory management error</para>
            </TD>
            <TD>
              <para>The function call could not be processed because the underlying memory objects could not be accessed, possibly because of low memory conditions.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>HY090</para>
            </TD>
            <TD>
              <para>Invalid string or buffer length</para>
            </TD>
            <TD>
              <para>(DM) The argument <legacyItalic>TextLength</legacyItalic> was less than or equal to 0 but not equal to SQL_NTS.</para>
              <para>A parameter value, set with <legacyBold>SQLBindParameter</legacyBold>, was a null pointer, and the parameter length value was not 0, SQL_NULL_DATA, SQL_DATA_AT_EXEC, SQL_DEFAULT_PARAM, or less than or equal to SQL_LEN_DATA_AT_EXEC_OFFSET.</para>
              <para>A parameter value, set with <legacyBold>SQLBindParameter</legacyBold>, was not a null pointer; the C data type was SQL_C_BINARY or SQL_C_CHAR; and the parameter length value was less than 0 but was not SQL_NTS, SQL_NULL_DATA, SQL_DATA_AT_EXEC, SQL_DEFAULT_PARAM, or less than or equal to SQL_LEN_DATA_AT_EXEC_OFFSET.</para>
              <para>A parameter length value bound by <legacyBold>SQLBindParameter</legacyBold> was set to SQL_DATA_AT_EXEC; the SQL type was either SQL_LONGVARCHAR, SQL_LONGVARBINARY, or a long data source–specific data type; and the SQL_NEED_LONG_DATA_LEN information type in <legacyBold>SQLGetInfo</legacyBold> was "Y".</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>HY105</para>
            </TD>
            <TD>
              <para>Invalid parameter type</para>
            </TD>
            <TD>
              <para>The value specified for the argument <legacyItalic>InputOutputType</legacyItalic> in <legacyBold>SQLBindParameter</legacyBold> was SQL_PARAM_OUTPUT, and the parameter was an input parameter.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>HY109</para>
            </TD>
            <TD>
              <para>Invalid cursor position</para>
            </TD>
            <TD>
              <para>*<legacyItalic>StatementText</legacyItalic> contained a positioned update or delete statement, and the cursor was positioned (by <legacyBold>SQLSetPos</legacyBold> or <legacyBold>SQLFetchScroll</legacyBold>) on a row that had been deleted or could not be fetched.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>HY117</para>
            </TD>
            <TD>
              <para>Connection is suspended due to unknown transaction state. Only disconnect and read-only functions are allowed.</para>
            </TD>
            <TD>
              <para>(DM) For more information about suspended state, see <link xlink:href="ff375ce1-eb50-4693-b1e6-70181a6dbf9f">SQLEndTran</link>.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>HYC00</para>
            </TD>
            <TD>
              <para>Optional feature not implemented</para>
            </TD>
            <TD>
              <para>The combination of the current settings of the SQL_ATTR_CONCURRENCY and SQL_ATTR_CURSOR_TYPE statement attributes was not supported by the driver or data source.</para>
              <para>The SQL_ATTR_USE_BOOKMARKS statement attribute was set to SQL_UB_VARIABLE, and the SQL_ATTR_CURSOR_TYPE statement attribute was set to a cursor type for which the driver does not support bookmarks.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>HYT00</para>
            </TD>
            <TD>
              <para>Timeout expired</para>
            </TD>
            <TD>
              <para>The query timeout period expired before the data source returned the result set. The timeout period is set through <legacyBold>SQLSetStmtAttr</legacyBold>, SQL_ATTR_QUERY_TIMEOUT.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>HYT01</para>
            </TD>
            <TD>
              <para>Connection timeout expired</para>
            </TD>
            <TD>
              <para>The connection timeout period expired before the data source responded to the request. The connection timeout period is set through <legacyBold>SQLSetConnectAttr</legacyBold>, SQL_ATTR_CONNECTION_TIMEOUT.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>IM001</para>
            </TD>
            <TD>
              <para>Driver does not support this function</para>
            </TD>
            <TD>
              <para>(DM) The driver associated with the <legacyItalic>StatementHandle</legacyItalic> does not support the function.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>IM017</para>
            </TD>
            <TD>
              <para>Polling is disabled in asynchronous notification mode</para>
            </TD>
            <TD>
              <para>Whenever the notification model is used, polling is disabled.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>IM018</para>
            </TD>
            <TD>
              <para>
                <languageKeyword>SQLCompleteAsync</languageKeyword> has not been called to complete the previous asynchronous operation on this handle.</para>
            </TD>
            <TD>
              <para>If the previous function call on the handle returns SQL_STILL_EXECUTING and if notification mode is enabled, <languageKeyword>SQLCompleteAsync</languageKeyword> must be called on the handle to do post-processing and complete the operation.</para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <section>
    <title>Comments</title>
    <content>
      <para>The application calls <legacyBold>SQLExecDirect</legacyBold> to send an SQL statement to the data source. For more information about direct execution, see <legacyLink xlink:href="dd00a535-b136-494f-913b-410838e3de7e">Direct Execution</legacyLink>. The driver modifies the statement to use the form of SQL used by the data source and then submits it to the data source. In particular, the driver modifies the escape sequences used to define certain features in SQL. For the syntax of escape sequences, see <legacyLink xlink:href="cf229f21-6c38-4b5b-aca8-f1be0dfeb3d0">Escape Sequences in ODBC</legacyLink>.</para>
      <para>The application can include one or more parameter markers in the SQL statement. To include a parameter marker, the application embeds a question mark (?) into the SQL statement at the appropriate position. For information about parameters, see <legacyLink xlink:href="58d5b166-2578-4699-a560-1f1e6d86c49a">Statement Parameters</legacyLink>.</para>
      <para>If the SQL statement is a <legacyBold>SELECT</legacyBold> statement and if the application called <legacyBold>SQLSetCursorName</legacyBold> to associate a cursor with a statement, then the driver uses the specified cursor. Otherwise, the driver generates a cursor name.</para>
      <para>If the data source is in manual-commit mode (requiring explicit transaction initiation) and a transaction has not already been initiated, the driver initiates a transaction before it sends the SQL statement. For more information, see <legacyLink xlink:href="9c4b3931-e48b-4960-89a2-5697537e9f51">Manual-Commit Mode</legacyLink>.</para>
      <para>If an application uses <legacyBold>SQLExecDirect</legacyBold> to submit a <legacyBold>COMMIT</legacyBold> or <legacyBold>ROLLBACK</legacyBold> statement, it will not be interoperable between DBMS products. To commit or roll back a transaction, an application calls <legacyBold>SQLEndTran</legacyBold>.</para>
      <para>If <legacyBold>SQLExecDirect</legacyBold> encounters a data-at-execution parameter, it returns SQL_NEED_DATA. The application sends the data using <legacyBold>SQLParamData</legacyBold> and <legacyBold>SQLPutData</legacyBold>. See <legacyLink xlink:href="38349d4b-be03-46f9-9d6a-e50dd144e225">SQLBindParameter</legacyLink>, <legacyLink xlink:href="68fe010d-9539-4e5b-a260-c8d32423b1db">SQLParamData</legacyLink>, <legacyLink xlink:href="9a60f004-1477-4c54-a20c-7378e1116713">SQLPutData</legacyLink>, and <legacyLink xlink:href="ea989084-a8e6-4737-892e-9ec99dd49caf">Sending Long Data</legacyLink>.</para>
      <para>If <legacyBold>SQLExecDirect</legacyBold> executes a searched update, insert, or delete statement that does not affect any rows at the data source, the call to <legacyBold>SQLExecDirect</legacyBold> returns SQL_NO_DATA.</para>
      <para>If the value of the SQL_ATTR_PARAMSET_SIZE statement attribute is greater than 1 and the SQL statement contains at least one parameter marker, <legacyBold>SQLExecDirect</legacyBold> will execute the SQL statement once for each set of parameter values from the arrays pointed to by the <legacyItalic>ParameterValuePointer</legacyItalic> argument in the call to <legacyBold>SQLBindParameter</legacyBold>. For more information, see <legacyLink xlink:href="9b572c5b-1dfe-40af-bebd-051548ab6d90">Arrays of Parameter Values</legacyLink>.</para>
      <para>If bookmarks are turned on and a query is executed that cannot support bookmarks, the driver should attempt to coerce the environment to one that supports bookmarks by changing an attribute value and returning SQLSTATE 01S02 (Option value changed). If the attribute cannot be changed, the driver should return SQLSTATE HY024 (Invalid attribute value).</para>
      <alert class="note">
        <para>When using connection pooling, an application must not execute SQL statements that change the database or the context of the database, such as the <legacyBold>USE</legacyBold> <legacyItalic>database</legacyItalic> statement in SQL Server, which changes the catalog used by a data source.</para>
      </alert>
    </content>
  </section>
  <section>
    <title>Code Example</title>
    <content>
      <para>See <legacyLink xlink:href="41a37655-84cd-423f-9daa-e0b47b88dc54">SQLBindCol</legacyLink>, <legacyLink xlink:href="e3c1356a-5db7-4186-85fd-8b74633317e8">SQLGetData</legacyLink>, and <link xlink:href="38ae6b7f-f53b-48a7-8fe5-4bbd6e0e414b">Sample ODBC Program</link>.</para>
    </content>
  </section>
  <section>
    <title>Related Functions</title>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>For information about</para>
            </TD>
            <TD>
              <para>See</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>Binding a buffer to a column in a result set</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="41a37655-84cd-423f-9daa-e0b47b88dc54">SQLBindCol Function</legacyLink>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Canceling statement processing</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="ac0b5972-627f-4440-8c5a-0e8da728726d">SQLCancel Function</legacyLink>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Executing a commit or rollback operation</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="ff375ce1-eb50-4693-b1e6-70181a6dbf9f">SQLEndTran Function</legacyLink>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Executing a prepared SQL statement</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="9286a01d-cde2-4b90-af94-9fd7f8da48bf">SQLExecute Function</legacyLink>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Fetching multiple rows of data</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="6c6611d2-bc6a-4390-87c9-1c5dd9cfe07c">SQLFetch Function</legacyLink>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Fetching a block of data or scrolling through a result set</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="c0243667-428c-4dda-ae91-3c307616a1ac">SQLFetchScroll Function</legacyLink>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Returning a cursor name</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="e6e92199-7bb6-447c-8987-049a4c6ce05d">SQLGetCursorName Function</legacyLink>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Fetching part or all of a column of data</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="e3c1356a-5db7-4186-85fd-8b74633317e8">SQLGetData Function</legacyLink>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Returning the next parameter to send data for</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="68fe010d-9539-4e5b-a260-c8d32423b1db">SQLParamData Function</legacyLink>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Preparing a statement for execution</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="332e1b4b-b0ed-4e7a-aa4d-4f35f4f4476b">SQLPrepare Function</legacyLink>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Sending parameter data at execution time</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="9a60f004-1477-4c54-a20c-7378e1116713">SQLPutData Function</legacyLink>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Setting a cursor name</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="4e055946-12d4-4589-9891-41617a50f34e">SQLSetCursorName Function</legacyLink>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Setting a statement attribute</para>
            </TD>
            <TD>
              <para>
                <legacyLink xlink:href="7abc5260-733a-48d4-9974-2d1a6a9ea5f6">SQLSetStmtAttr Function</legacyLink>
              </para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="b7a49774-f458-44ce-9a04-a0457501405b">ODBC API Reference</link>
<link xlink:href="96f97ba3-7e73-4196-abfb-036c5f6d1903">ODBC Header Files</link>
</relatedTopics>
</developerReferenceWithSyntaxDocument>