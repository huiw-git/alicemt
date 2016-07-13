---
title: Microsoft OLE DB Provider for ODBC
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2dc0372d-e74d-4d0f-9c8c-04e5a168c148
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
# Microsoft OLE DB Provider for ODBC
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>To an ADO or RDS programmer, an ideal world would be one in which every data source exposes an OLE DB interface, so that ADO could call directly into the data source. Although increasingly more database vendors are implementing OLE DB interfaces, some data sources are not yet exposed this way. However, most DBMS systems in use today can be accessed through ODBC.</para>
    <para>ODBC drivers are available for every major DBMS in use today, including Microsoft SQL Server, Microsoft Access (Microsoft Jet database engine), and Microsoft FoxPro, in addition to non-Microsoft database products such as Oracle.</para>
    <para>The Microsoft ODBC Provider, however, allows ADO to connect to any ODBC data source. The provider is free-threaded and Unicode enabled.</para>
    <para>The provider supports transactions, although different DBMS engines offer different types of transaction support. For example, Microsoft Access supports nested transactions up to five levels deep.</para>
    <para>This is the default provider for ADO, and all provider-dependent ADO properties and methods are supported.</para>
  </introduction>
  <section>
    <title>Connection String Parameters</title>
    <content>
      <para>To connect to this provider, set the <legacyBold>Provider=</legacyBold> argument of the <legacyLink xlink:href="3be75b75-4d36-4479-ab64-9a456869252a">ConnectionString</legacyLink> property to:</para>
      <code>MSDASQL</code>
      <para>Reading the <legacyLink xlink:href="0ff70e72-0061-4ffc-90fb-e3ea23129bb2">Provider</legacyLink> property will return this string as well.</para>
    </content>
  </section>
  <section>
    <title>Typical Connection String</title>
    <content>
      <para>A typical connection string for this provider is:</para>
      <code>"Provider=MSDASQL;DSN=<legacyItalic>dsnName</legacyItalic>;UID=<legacyItalic>MyUserID</legacyItalic>;PWD=<legacyItalic>MyPassword</legacyItalic>;"</code>
      <para>The string consists of these keywords:</para>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>Keyword</para>
            </TD>
            <TD>
              <para>Description</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>
                <legacyBold>Provider</legacyBold>
              </para>
            </TD>
            <TD>
              <para>Specifies the OLE DB provider for ODBC.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyBold>DSN</legacyBold>
              </para>
            </TD>
            <TD>
              <para>Specifies the data source name.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyBold>UID</legacyBold>
              </para>
            </TD>
            <TD>
              <para>Specifies the user name.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyBold>PWD</legacyBold>
              </para>
            </TD>
            <TD>
              <para>Specifies the user password.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyBold>URL</legacyBold>
              </para>
            </TD>
            <TD>
              <para>Specifies the URL of a file or directory published in a Web folder.</para>
            </TD>
          </tr>
        </tbody>
      </table>
      <para>Because this is the default provider for ADO, if you omit the <legacyBold>Provider=</legacyBold> parameter from the connection string, ADO will try to establish a connection to this provider.</para>
      <alert class="note">
        <para>If you are connecting to a data source provider that supports Windows authentication, you should specify <system>Trusted_Connection=yes</system> or <system>Integrated Security = SSPI</system> instead of user ID and password information in the connection string.</para>
      </alert>
      <para>The provider does not support any specific connection parameters in addition to those defined by ADO. However, the provider will pass any non-ADO connection parameters to the ODBC driver manager.</para>
      <para>Because you can omit the <legacyBold>Provider</legacyBold> parameter, you can therefore compose an ADO connection string that is identical to an ODBC connection string for the same data source. Use the same parameter names (<legacyBold>DRIVER=</legacyBold>, <legacyBold>DATABASE=</legacyBold>, <legacyBold>DSN=</legacyBold>, and so on), values, and syntax as you would when composing an ODBC connection string. You can connect with or without a predefined data source name (DSN) or FileDSN.</para>
    </content>
  </section>
  <section>
    <title>Syntax with a DSN or FileDSN:</title>
    <content>
      <code>"[Provider=MSDASQL;] { DSN=name | FileDSN=filename } ; 
[DATABASE=database;] UID=user; PWD=password"</code>
    </content>
  </section>
  <section>
    <title>Syntax without a DSN (DSN-less connection):</title>
    <content>
      <code>"[Provider=MSDASQL;] DRIVER=driver; SERVER=server; 
DATABASE=database; UID=MyUserID; PWD=MyPassword"</code>
    </content>
  </section>
  <languageReferenceRemarks>
    <content>
      <para>If you use a <legacyBold>DSN</legacyBold> or <legacyBold>FileDSN</legacyBold>, it must be defined through the ODBC Data Source Administrator in the Windows Control Panel. In Microsoft Windows 2000, the ODBC Administrator is located under Administrative Tools. In earlier versions of Windows, the ODBC Administrator icon is named <legacyBold>32-bit ODBC</legacyBold> or just <legacyBold>ODBC</legacyBold>.</para>
      <para>As an alternative to setting a <legacyBold>DSN</legacyBold>, you can specify the ODBC driver (<legacyBold>DRIVER=</legacyBold>), such as "SQL Server;" the server name (<legacyBold>SERVER=</legacyBold>); and the database name (<legacyBold>DATABASE=</legacyBold>).</para>
      <para>You can also specify a user account name (<legacyBold>UID=</legacyBold>), and the password for the user account (<legacyBold>PWD=</legacyBold>) in the ODBC-specific parameters or in the standard ADO-defined <legacyItalic>user</legacyItalic> and <legacyItalic>password</legacyItalic> parameters.</para>
      <para>Although a <legacyBold>DSN</legacyBold> definition already specifies a database, you can specify <legacyItalic>a</legacyItalic> <legacyItalic>database</legacyItalic> parameter in addition to a <legacyBold>DSN</legacyBold> to connect to a different database. It is a good idea to always include <legacyItalic>the</legacyItalic> <legacyItalic>database</legacyItalic> parameter when you use a <legacyBold>DSN</legacyBold>. This will ensure that you connect to the correct database if another user changed the default database parameter since you last checked the <legacyBold>DSN</legacyBold> definition.</para>
    </content>
  </languageReferenceRemarks>
  <section>
    <title>Provider-Specific Connection Properties</title>
    <content>
      <para>The OLE DB provider for ODBC adds several properties to the <legacyLink xlink:href="1d539aa8-ce0d-4418-ab03-8d0a3c1e9d82">Properties</legacyLink> collection of the <legacyBold>Connection</legacyBold> object. The following table lists these properties with the corresponding OLE DB property name in parentheses.</para>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>Property Name</para>
            </TD>
            <TD>
              <para>Description</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>Accessible Procedures (KAGPROP_ACCESSIBLEPROCEDURES)</para>
            </TD>
            <TD>
              <para>Indicates whether the user has access to stored procedures.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Accessible Tables (KAGPROP_ACCESSIBLETABLES)</para>
            </TD>
            <TD>
              <para>Indicates whether the user has permission to execute SELECT statements against the database tables.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Active Statements (KAGPROP_ACTIVESTATEMENTS)</para>
            </TD>
            <TD>
              <para>Indicates the number of handles an ODBC driver can support on a connection.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Driver Name (KAGPROP_DRIVERNAME)</para>
            </TD>
            <TD>
              <para>Indicates the file name of the ODBC driver.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Driver ODBC Version (KAGPROP_DRIVERODBCVER)</para>
            </TD>
            <TD>
              <para>Indicates the version of ODBC that this driver supports.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>File Usage (KAGPROP_FILEUSAGE)</para>
            </TD>
            <TD>
              <para>Indicates how the driver treats a file in a data source; as a table or as a catalog.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Like Escape Clause (KAGPROP_LIKEESCAPECLAUSE)</para>
            </TD>
            <TD>
              <para>Indicates whether the driver supports the definition and use of an escape character for the percent character (%) and underline character (_) in the LIKE predicate of a WHERE clause.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Max Columns in Group By (KAGPROP_MAXCOLUMNSINGROUPBY)</para>
            </TD>
            <TD>
              <para>Indicates the maximum number of columns that can be listed in the GROUP BY clause of a SELECT statement.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Max Columns in Index (KAGPROP_MAXCOLUMNSININDEX)</para>
            </TD>
            <TD>
              <para>Indicates the maximum number of columns that can be included in an index.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Max Columns in Order By (KAGPROP_MAXCOLUMNSINORDERBY)</para>
            </TD>
            <TD>
              <para>Indicates the maximum number of columns that can be listed in the ORDER BY clause of a SELECT statement.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Max Columns in Select (KAGPROP_MAXCOLUMNSINSELECT)</para>
            </TD>
            <TD>
              <para>Indicates the maximum number of columns that can be listed in the SELECT portion of a SELECT statement.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Max Columns in Table (KAGPROP_MAXCOLUMNSINTABLE)</para>
            </TD>
            <TD>
              <para>Indicates the maximum number of columns allowed in a table.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Numeric Functions (KAGPROP_NUMERICFUNCTIONS)</para>
            </TD>
            <TD>
              <para>Indicates which numeric functions are supported by the ODBC driver. For a listing of function names and the associated values used in this bitmask, see <legacyLink xlink:href="59c7cd5e-32d6-43ab-bac3-7010322d105a">Appendix E: Scalar Functions</legacyLink>, in the ODBC documentation.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Outer Join Capabilities (KAGPROP_OJCAPABILITY)</para>
            </TD>
            <TD>
              <para>Indicates the types of OUTER JOINs supported by the provider.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Outer Joins (KAGPROP_OUTERJOINS)</para>
            </TD>
            <TD>
              <para>Indicates whether the provider supports OUTER JOINs.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Special Characters (KAGPROP_SPECIALCHARACTERS)</para>
            </TD>
            <TD>
              <para>Indicates which characters have special meaning for the ODBC driver.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Stored Procedures (KAGPROP_PROCEDURES)</para>
            </TD>
            <TD>
              <para>Indicates whether stored procedures are available for use with this ODBC driver.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>String Functions (KAGPROP_STRINGFUNCTIONS)</para>
            </TD>
            <TD>
              <para>Indicates which string functions are supported by the ODBC driver. For a listing of function names and the associated values used in this bitmask, see <legacyLink xlink:href="59c7cd5e-32d6-43ab-bac3-7010322d105a">Appendix E: Scalar Functions</legacyLink>, in the ODBC documentation.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>System Functions (KAGPROP_SYSTEMFUNCTIONS)</para>
            </TD>
            <TD>
              <para>Indicates which system functions are supported by the ODBC driver. For a listing of function names and the associated values used in this bitmask, see <legacyLink xlink:href="59c7cd5e-32d6-43ab-bac3-7010322d105a">Appendix E: Scalar Functions</legacyLink>, in the ODBC documentation.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Time/Date Functions (KAGPROP_TIMEDATEFUNCTIONS)</para>
            </TD>
            <TD>
              <para>Indicates which time and date functions are supported by the ODBC driver. For a listing of function names and the associated values used in this bitmask, see <legacyLink xlink:href="59c7cd5e-32d6-43ab-bac3-7010322d105a">Appendix E: Scalar Functions</legacyLink>, in the ODBC documentation.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL Grammar Support (KAGPROP_ODBCSQLCONFORMANCE)</para>
            </TD>
            <TD>
              <para>Indicates the SQL grammar that the ODBC driver supports.</para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <section>
    <title>Provider-Specific Recordset and Command Properties</title>
    <content>
      <para>The OLE DB provider for ODBC adds several properties to the <legacyBold>Properties</legacyBold> collection of the <legacyBold>Recordset</legacyBold> and <legacyBold>Command</legacyBold> objects. The following table lists these properties with the corresponding OLE DB property name in parentheses.</para>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>Property Name</para>
            </TD>
            <TD>
              <para>Description</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>Query Based Updates/Deletes/Inserts (KAGPROP_QUERYBASEDUPDATES)</para>
            </TD>
            <TD>
              <para>Indicates whether updates, deletions, and insertions can be performed by using SQL queries.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>ODBC Concurrency Type (KAGPROP_CONCURRENCY)</para>
            </TD>
            <TD>
              <para>Indicates the method used to reduce potential problems caused by two users trying to access the same data from the data source simultaneously.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>BLOB accessibility on Forward-Only cursor (KAGPROP_BLOBSONFOCURSOR)</para>
            </TD>
            <TD>
              <para>Indicates whether BLOB <legacyBold>Fields</legacyBold> can be accessed when using a forward-only cursor.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Include SQL_FLOAT, SQL_DOUBLE, and SQL_REAL in QBU WHERE clauses (KAGPROP_INCLUDENONEXACT)</para>
            </TD>
            <TD>
              <para>Indicates whether SQL_FLOAT, SQL_DOUBLE, and SQL_REAL values can be included in a QBU WHERE clause.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Position on the last row after insert (KAGPROP_POSITIONONNEWROW)</para>
            </TD>
            <TD>
              <para>Indicates that after a new record has been inserted in a table, the last row in the table will be come the current row.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>IRowsetChangeExtInfo (KAGPROP_IROWSETCHANGEEXTINFO)</para>
            </TD>
            <TD>
              <para>Indicates whether the <legacyBold>IRowsetChange</legacyBold> interface provides extended information support.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>ODBC Cursor Type (KAGPROP_CURSOR)</para>
            </TD>
            <TD>
              <para>Indicates the type of cursor used by the <legacyBold>Recordset</legacyBold>.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Generate a Rowset that can be marshaled (KAGPROP_MARSHALLABLE)</para>
            </TD>
            <TD>
              <para>Indicates that the ODBC driver generates a recordset that can be marshaled</para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <section>
    <title>Command Text</title>
    <content>
      <para>How you use the <legacyLink xlink:href="a02c22fb-542d-465e-a629-30fd59dcbebf">Command</legacyLink> object largely depends on the data source, and what type of query or command statement it will accept.</para>
      <para>ODBC provides a specific syntax for calling stored procedures. For the <legacyLink xlink:href="4dd7e82a-8da5-4a4e-b439-11a29286fa0e">CommandText</legacyLink> property of a <legacyBold>Command</legacyBold> object, the <legacyItalic>CommandText </legacyItalic>argument to the <legacyBold>Execute</legacyBold> method on a <legacyLink xlink:href="ef6b1824-5b12-43db-89d7-8f3d13896d4d">Connection</legacyLink> object, or the <legacyItalic>Source</legacyItalic> argument to the <legacyBold>Open</legacyBold> method on a <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink> object, passes in a string with this syntax:</para>
      <code>"{ [ ? = ] call procedure [ ( ? [, ? [ , … ]] ) ] }"</code>
      <para>Each <legacyBold>?</legacyBold> references an object in the <legacyLink xlink:href="497cae10-3913-422a-9753-dcbb0a639b1b">Parameters</legacyLink> collection. The first <legacyBold>?</legacyBold> references <legacyBold>Parameters</legacyBold>(0), the next <legacyBold>?</legacyBold> references <legacyBold>Parameters</legacyBold>(1), and so on.</para>
      <para>The parameter references are optional and depend on the structure of the stored procedure. If you want to call a stored procedure that defines no parameters, your string would look like the following:</para>
      <code>"{ call procedure }"</code>
      <para>If you have two query parameters, your string would resemble the following:</para>
      <code>"{ call procedure ( ?, ? ) }"</code>
      <para>If the stored procedure will return a value, the return value is treated as another parameter. If you have no query parameters but you do have a return value, your string would resemble the following:</para>
      <code>"{ ? = call procedure }"</code>
      <para>Finally, if you have a return value and two query parameters, your string would resemble the following:</para>
      <code>"{ ? = call procedure ( ?, ? ) }"</code>
    </content>
  </section>
  <section>
    <title>Recordset Behavior</title>
    <content>
      <para>The following tables list the standard ADO methods and properties available on a <legacyBold>Recordset</legacyBold> object opened with this provider.</para>
      <para>For more detailed information about <legacyBold>Recordset</legacyBold> behavior for your provider configuration, run the <legacyLink xlink:href="298fc41c-0b55-42fc-b373-c5133b4da6a5">Supports</legacyLink> method and enumerate the <legacyBold>Properties</legacyBold> collection of the <legacyBold>Recordset</legacyBold> to determine whether provider-specific dynamic properties are present.</para>
      <para>Availability of standard ADO <legacyBold>Recordset</legacyBold> properties:</para>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>Property</para>
            </TD>
            <TD>
              <para>ForwardOnly</para>
            </TD>
            <TD>
              <para>Dynamic</para>
            </TD>
            <TD>
              <para>Keyset</para>
            </TD>
            <TD>
              <para>Static</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>
                <legacyLink xlink:href="ddb58a35-ec3a-423c-a504-3c65e62c23d4">AbsolutePage</legacyLink>
              </para>
            </TD>
            <TD>
              <para>not available</para>
            </TD>
            <TD>
              <para>not available</para>
            </TD>
            <TD>
              <para>read/write</para>
            </TD>
            <TD>
              <para>read/write</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyLink xlink:href="79f8ee5e-fc70-46d8-8c29-ebf943c66592">AbsolutePosition</legacyLink>
              </para>
            </TD>
            <TD>
              <para>not available</para>
            </TD>
            <TD>
              <para>not available</para>
            </TD>
            <TD>
              <para>read/write</para>
            </TD>
            <TD>
              <para>read/write</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyLink xlink:href="52d0a96c-14fb-4ad9-b004-4d821bc0a6db">ActiveConnection</legacyLink>
              </para>
            </TD>
            <TD>
              <para>read/write</para>
            </TD>
            <TD>
              <para>read/write</para>
            </TD>
            <TD>
              <para>read/write</para>
            </TD>
            <TD>
              <para>read/write</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyLink xlink:href="36c31ab2-f3b6-4281-89b6-db7e04e38fd2">BOF</legacyLink>
              </para>
            </TD>
            <TD>
              <para>read-only</para>
            </TD>
            <TD>
              <para>read-only</para>
            </TD>
            <TD>
              <para>read-only</para>
            </TD>
            <TD>
              <para>read-only</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyLink xlink:href="481dcc93-487b-490e-ac58-a1e9b2ebfd43">Bookmark</legacyLink>
              </para>
            </TD>
            <TD>
              <para>not available</para>
            </TD>
            <TD>
              <para>not available</para>
            </TD>
            <TD>
              <para>read/write</para>
            </TD>
            <TD>
              <para>read/write</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyLink xlink:href="49dc9a49-af7b-433b-be36-7a14ca984fb7">CacheSize</legacyLink>
              </para>
            </TD>
            <TD>
              <para>read/write</para>
            </TD>
            <TD>
              <para>read/write</para>
            </TD>
            <TD>
              <para>read/write</para>
            </TD>
            <TD>
              <para>read/write</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyLink xlink:href="39c8d86e-7ee9-4182-be5e-aad5ce952f84">CursorLocation</legacyLink>
              </para>
            </TD>
            <TD>
              <para>read/write</para>
            </TD>
            <TD>
              <para>read/write</para>
            </TD>
            <TD>
              <para>read/write</para>
            </TD>
            <TD>
              <para>read/write</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyLink xlink:href="b62c66ca-58d5-430e-9257-eb38c65e48c2">CursorType</legacyLink>
              </para>
            </TD>
            <TD>
              <para>read/write</para>
            </TD>
            <TD>
              <para>read/write</para>
            </TD>
            <TD>
              <para>read/write</para>
            </TD>
            <TD>
              <para>read/write</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyLink xlink:href="a1b04bb2-8c8b-47f9-8477-bfd0368b6f68">EditMode</legacyLink>
              </para>
            </TD>
            <TD>
              <para>read-only</para>
            </TD>
            <TD>
              <para>read-only</para>
            </TD>
            <TD>
              <para>read-only</para>
            </TD>
            <TD>
              <para>read-only</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyLink xlink:href="80263a7a-5d21-45d1-84fc-34b7a9be4c22">Filter</legacyLink>
              </para>
            </TD>
            <TD>
              <para>read/write</para>
            </TD>
            <TD>
              <para>read/write</para>
            </TD>
            <TD>
              <para>read/write</para>
            </TD>
            <TD>
              <para>read/write</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyLink xlink:href="9920c14e-033a-4de1-8149-0ce9737a3246">LockType</legacyLink>
              </para>
            </TD>
            <TD>
              <para>read/write</para>
            </TD>
            <TD>
              <para>read/write</para>
            </TD>
            <TD>
              <para>read/write</para>
            </TD>
            <TD>
              <para>read/write</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyLink xlink:href="390c8abf-133e-40da-8b99-8f748a983e4f">MarshalOptions</legacyLink>
              </para>
            </TD>
            <TD>
              <para>read/write</para>
            </TD>
            <TD>
              <para>read/write</para>
            </TD>
            <TD>
              <para>read/write</para>
            </TD>
            <TD>
              <para>read/write</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyLink xlink:href="20c76571-8c9a-482c-a99e-726ab1d93f8b">MaxRecords</legacyLink>
              </para>
            </TD>
            <TD>
              <para>read/write</para>
            </TD>
            <TD>
              <para>read/write</para>
            </TD>
            <TD>
              <para>read/write</para>
            </TD>
            <TD>
              <para>read/write</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyLink xlink:href="b601b56c-0ac4-44ee-bc91-c3d2d104f00a">PageCount</legacyLink>
              </para>
            </TD>
            <TD>
              <para>read/write</para>
            </TD>
            <TD>
              <para>not available</para>
            </TD>
            <TD>
              <para>read-only</para>
            </TD>
            <TD>
              <para>read-only</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyLink xlink:href="e57930a6-46c4-4a17-a3b6-f79e94d5c9c7">PageSize</legacyLink>
              </para>
            </TD>
            <TD>
              <para>read/write</para>
            </TD>
            <TD>
              <para>read/write</para>
            </TD>
            <TD>
              <para>read/write</para>
            </TD>
            <TD>
              <para>read/write</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyLink xlink:href="834f0121-394a-44d4-ad7d-999b43a6fe63">RecordCount</legacyLink>
              </para>
            </TD>
            <TD>
              <para>read/write</para>
            </TD>
            <TD>
              <para>not available</para>
            </TD>
            <TD>
              <para>read-only</para>
            </TD>
            <TD>
              <para>read-only</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyLink xlink:href="a05ba2c9-2821-4343-8607-4de9b764ec91">Source</legacyLink>
              </para>
            </TD>
            <TD>
              <para>read/write</para>
            </TD>
            <TD>
              <para>read/write</para>
            </TD>
            <TD>
              <para>read/write</para>
            </TD>
            <TD>
              <para>read/write</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyLink xlink:href="0b993bac-2653-40b1-bcbb-5b57b6aae2bf">State</legacyLink>
              </para>
            </TD>
            <TD>
              <para>read-only</para>
            </TD>
            <TD>
              <para>read-only</para>
            </TD>
            <TD>
              <para>read-only</para>
            </TD>
            <TD>
              <para>read-only</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyLink xlink:href="41d70d89-880f-4850-9d17-19d9790cc8eb">Status</legacyLink>
              </para>
            </TD>
            <TD>
              <para>read-only</para>
            </TD>
            <TD>
              <para>read-only</para>
            </TD>
            <TD>
              <para>read-only</para>
            </TD>
            <TD>
              <para>read-only</para>
            </TD>
          </tr>
        </tbody>
      </table>
      <para>The <legacyLink xlink:href="79f8ee5e-fc70-46d8-8c29-ebf943c66592">AbsolutePosition</legacyLink> and <legacyLink xlink:href="ddb58a35-ec3a-423c-a504-3c65e62c23d4">AbsolutePage</legacyLink> properties are write-only when ADO is used with version 1.0 of the Microsoft OLE DB Provider for ODBC.</para>
      <para>Availability of standard ADO <legacyBold>Recordset</legacyBold> methods:</para>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>Method</para>
            </TD>
            <TD>
              <para>ForwardOnly</para>
            </TD>
            <TD>
              <para>Dynamic</para>
            </TD>
            <TD>
              <para>Keyset</para>
            </TD>
            <TD>
              <para>Static</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>
                <legacyLink xlink:href="a9f54be9-5763-45d0-a6eb-09981b03bc08">AddNew</legacyLink>
              </para>
            </TD>
            <TD>
              <para>Yes</para>
            </TD>
            <TD>
              <para>Yes</para>
            </TD>
            <TD>
              <para>Yes</para>
            </TD>
            <TD>
              <para>Yes</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyLink xlink:href="e0db4e15-6787-41e2-8f13-9e9b524d620a">Cancel</legacyLink>
              </para>
            </TD>
            <TD>
              <para>Yes</para>
            </TD>
            <TD>
              <para>Yes</para>
            </TD>
            <TD>
              <para>Yes</para>
            </TD>
            <TD>
              <para>Yes</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyLink xlink:href="dbdc2574-e44e-4d95-b03d-4a5d9e9adf3c">CancelBatch</legacyLink>
              </para>
            </TD>
            <TD>
              <para>Yes</para>
            </TD>
            <TD>
              <para>Yes</para>
            </TD>
            <TD>
              <para>Yes</para>
            </TD>
            <TD>
              <para>Yes</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyLink xlink:href="eaa856cc-c786-462e-890c-c896261b1741">CancelUpdate</legacyLink>
              </para>
            </TD>
            <TD>
              <para>Yes</para>
            </TD>
            <TD>
              <para>Yes</para>
            </TD>
            <TD>
              <para>Yes</para>
            </TD>
            <TD>
              <para>Yes</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyLink xlink:href="ad49265f-1c05-4271-9bbf-7c00010ac18c">Clone</legacyLink>
              </para>
            </TD>
            <TD>
              <para>No</para>
            </TD>
            <TD>
              <para>No</para>
            </TD>
            <TD>
              <para>Yes</para>
            </TD>
            <TD>
              <para>Yes</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyLink xlink:href="3cdf27d1-a180-4cff-8e42-95dec5fb1b55">Close</legacyLink>
              </para>
            </TD>
            <TD>
              <para>Yes</para>
            </TD>
            <TD>
              <para>Yes</para>
            </TD>
            <TD>
              <para>Yes</para>
            </TD>
            <TD>
              <para>Yes</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyLink xlink:href="1eb9209c-602c-4507-b0c2-6527a599b67d">Delete</legacyLink>
              </para>
            </TD>
            <TD>
              <para>Yes</para>
            </TD>
            <TD>
              <para>Yes</para>
            </TD>
            <TD>
              <para>Yes</para>
            </TD>
            <TD>
              <para>Yes</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyLink xlink:href="14b92860-4171-47d9-a413-dd60dd6a8880">GetRows</legacyLink>
              </para>
            </TD>
            <TD>
              <para>Yes</para>
            </TD>
            <TD>
              <para>Yes</para>
            </TD>
            <TD>
              <para>Yes</para>
            </TD>
            <TD>
              <para>Yes</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyLink xlink:href="13fe9381-d00b-4f4a-9162-83c3f21b3837">Move</legacyLink>
              </para>
            </TD>
            <TD>
              <para>Yes</para>
            </TD>
            <TD>
              <para>Yes</para>
            </TD>
            <TD>
              <para>Yes</para>
            </TD>
            <TD>
              <para>Yes</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyLink xlink:href="a61a01a7-5b33-4150-9126-21dfa63654cb">MoveFirst</legacyLink>
              </para>
            </TD>
            <TD>
              <para>Yes</para>
            </TD>
            <TD>
              <para>Yes</para>
            </TD>
            <TD>
              <para>Yes</para>
            </TD>
            <TD>
              <para>Yes</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyLink xlink:href="a61a01a7-5b33-4150-9126-21dfa63654cb">MoveLast</legacyLink>
              </para>
            </TD>
            <TD>
              <para>No</para>
            </TD>
            <TD>
              <para>Yes</para>
            </TD>
            <TD>
              <para>Yes</para>
            </TD>
            <TD>
              <para>Yes</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyLink xlink:href="a61a01a7-5b33-4150-9126-21dfa63654cb">MoveNext</legacyLink>
              </para>
            </TD>
            <TD>
              <para>Yes</para>
            </TD>
            <TD>
              <para>Yes</para>
            </TD>
            <TD>
              <para>Yes</para>
            </TD>
            <TD>
              <para>Yes</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyLink xlink:href="a61a01a7-5b33-4150-9126-21dfa63654cb">MovePrevious</legacyLink>
              </para>
            </TD>
            <TD>
              <para>No</para>
            </TD>
            <TD>
              <para>Yes</para>
            </TD>
            <TD>
              <para>Yes</para>
            </TD>
            <TD>
              <para>Yes</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyLink xlink:href="ab1fa449-a695-4987-b1ee-bc68f89418dd">NextRecordset</legacyLink>*</para>
            </TD>
            <TD>
              <para>Yes</para>
            </TD>
            <TD>
              <para>Yes</para>
            </TD>
            <TD>
              <para>Yes</para>
            </TD>
            <TD>
              <para>Yes</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyLink xlink:href="3236749c-4b71-4235-89e2-ccdfaaa9319d">Open</legacyLink>
              </para>
            </TD>
            <TD>
              <para>Yes</para>
            </TD>
            <TD>
              <para>Yes</para>
            </TD>
            <TD>
              <para>Yes</para>
            </TD>
            <TD>
              <para>Yes</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyLink xlink:href="d81ab76f-1aa8-4ccf-92ec-b65254dc3ea1">Requery</legacyLink>
              </para>
            </TD>
            <TD>
              <para>Yes</para>
            </TD>
            <TD>
              <para>Yes</para>
            </TD>
            <TD>
              <para>Yes</para>
            </TD>
            <TD>
              <para>Yes</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyLink xlink:href="73b355d4-a4c0-434b-bfc4-039b1c76b32e">Resync</legacyLink>
              </para>
            </TD>
            <TD>
              <para>No</para>
            </TD>
            <TD>
              <para>No</para>
            </TD>
            <TD>
              <para>Yes</para>
            </TD>
            <TD>
              <para>Yes</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyLink xlink:href="298fc41c-0b55-42fc-b373-c5133b4da6a5">Supports</legacyLink>
              </para>
            </TD>
            <TD>
              <para>Yes</para>
            </TD>
            <TD>
              <para>Yes</para>
            </TD>
            <TD>
              <para>Yes</para>
            </TD>
            <TD>
              <para>Yes</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyLink xlink:href="6b2a9c31-1a7e-40db-8a53-30720d0f6cc1">Update</legacyLink>
              </para>
            </TD>
            <TD>
              <para>Yes</para>
            </TD>
            <TD>
              <para>Yes</para>
            </TD>
            <TD>
              <para>Yes</para>
            </TD>
            <TD>
              <para>Yes</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyLink xlink:href="23f9314c-b027-4a51-aeae-50caa2977740">UpdateBatch</legacyLink>
              </para>
            </TD>
            <TD>
              <para>Yes</para>
            </TD>
            <TD>
              <para>Yes</para>
            </TD>
            <TD>
              <para>Yes</para>
            </TD>
            <TD>
              <para>Yes</para>
            </TD>
          </tr>
        </tbody>
      </table>
      <para>*Not supported for Microsoft Access databases.</para>
    </content>
  </section>
  <section>
    <title>Dynamic Properties</title>
    <content>
      <para>The Microsoft OLE DB Provider for ODBC inserts several dynamic properties into the <legacyBold>Properties</legacyBold> collection of the unopened <legacyLink xlink:href="ef6b1824-5b12-43db-89d7-8f3d13896d4d">Connection</legacyLink>, <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink>, and <legacyLink xlink:href="a02c22fb-542d-465e-a629-30fd59dcbebf">Command</legacyLink> objects. </para>
      <para>The following tables are a cross-index of the ADO and OLE DB names for each dynamic property. The OLE DB Programmer's Reference refers to an ADO property name by the term, "Description." You can find more information about these properties in the OLE DB Programmer's Reference. Search for the OLE DB property name in the Index or see <legacyLink xlink:href="deded3ff-f508-4e1b-b2b1-fd9afd3bd292">Appendix C: OLE DB Properties</legacyLink>.</para>
    </content>
  </section>
  <section>
    <title>Connection Dynamic Properties</title>
    <content>
      <para>The following properties are added to the <legacyBold>Connection</legacyBold> object's <legacyBold>Properties</legacyBold> collection.</para>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>ADO Property Name</para>
            </TD>
            <TD>
              <para>OLE DB Property Name</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>Active Sessions</para>
            </TD>
            <TD>
              <para>DBPROP_ACTIVESESSIONS</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Asynchable Abort</para>
            </TD>
            <TD>
              <para>DBPROP_ASYNCTXNABORT</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Asynchable Commit</para>
            </TD>
            <TD>
              <para>DBPROP_ASYNCTNXCOMMIT</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Autocommit Isolation Levels</para>
            </TD>
            <TD>
              <para>DBPROP_SESS_AUTOCOMMITISOLEVELS</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Catalog Location</para>
            </TD>
            <TD>
              <para>DBPROP_CATALOGLOCATION</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Catalog Term</para>
            </TD>
            <TD>
              <para>DBPROP_CATALOGTERM</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Column Definition</para>
            </TD>
            <TD>
              <para>DBPROP_COLUMNDEFINITION</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Connect Timeout</para>
            </TD>
            <TD>
              <para>DBPROP_INIT_TIMEOUT</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Current Catalog</para>
            </TD>
            <TD>
              <para>DBPROP_CURRENTCATALOG</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Data Source</para>
            </TD>
            <TD>
              <para>DBPROP_INIT_DATASOURCE</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Data Source Name</para>
            </TD>
            <TD>
              <para>DBPROP_DATASOURCENAME</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Data Source Object Threading Model</para>
            </TD>
            <TD>
              <para>DBPROP_DSOTHREADMODEL</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>DBMS Name</para>
            </TD>
            <TD>
              <para>DBPROP_DBMSNAME</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>DBMS Version</para>
            </TD>
            <TD>
              <para>DBPROP_DBMSVER</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Extended Properties</para>
            </TD>
            <TD>
              <para>DBPROP_INIT_PROVIDERSTRING</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>GROUP BY Support</para>
            </TD>
            <TD>
              <para>DBPROP_GROUPBY</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Heterogeneous Table Support</para>
            </TD>
            <TD>
              <para>DBPROP_HETEROGENEOUSTABLES</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Identifier Case Sensitivity</para>
            </TD>
            <TD>
              <para>DBPROP_IDENTIFIERCASE</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Initial Catalog</para>
            </TD>
            <TD>
              <para>DBPROP_INIT_CATALOG</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Isolation Levels</para>
            </TD>
            <TD>
              <para>DBPROP_SUPPORTEDTXNISOLEVELS</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Isolation Retention</para>
            </TD>
            <TD>
              <para>DBPROP_SUPPORTEDTXNISORETAIN</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Locale Identifier</para>
            </TD>
            <TD>
              <para>DBPROP_INIT_LCID</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Location</para>
            </TD>
            <TD>
              <para>DBPROP_INIT_LOCATION</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Maximum Index Size</para>
            </TD>
            <TD>
              <para>DBPROP_MAXINDEXSIZE</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Maximum Row Size</para>
            </TD>
            <TD>
              <para>DBPROP_MAXROWSIZE</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Maximum Row Size Includes BLOB</para>
            </TD>
            <TD>
              <para>DBPROP_MAXROWSIZEINCLUDESBLOB</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Maximum Tables in SELECT</para>
            </TD>
            <TD>
              <para>DBPROP_MAXTABLESINSELECT</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Mode</para>
            </TD>
            <TD>
              <para>DBPROP_INIT_MODE</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Multiple Parameter Sets</para>
            </TD>
            <TD>
              <para>DBPROP_MULTIPLEPARAMSETS</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Multiple Results</para>
            </TD>
            <TD>
              <para>DBPROP_MULTIPLERESULTS</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Multiple Storage Objects</para>
            </TD>
            <TD>
              <para>DBPROP_MULTIPLESTORAGEOBJECTS</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Multi-Table Update</para>
            </TD>
            <TD>
              <para>DBPROP_MULTITABLEUPDATE</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>NULL Collation Order</para>
            </TD>
            <TD>
              <para>DBPROP_NULLCOLLATION</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>NULL Concatenation Behavior</para>
            </TD>
            <TD>
              <para>DBPROP_CONCATNULLBEHAVIOR</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>OLE DB Services</para>
            </TD>
            <TD>
              <para>DBPROP_INIT_OLEDBSERVICES</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>OLE DB Version</para>
            </TD>
            <TD>
              <para>DBPROP_PROVIDEROLEDBVER</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>OLE Object Support</para>
            </TD>
            <TD>
              <para>DBPROP_OLEOBJECTS</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Open Rowset Support</para>
            </TD>
            <TD>
              <para>DBPROP_OPENROWSETSUPPORT</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>ORDER BY Columns in Select List</para>
            </TD>
            <TD>
              <para>DBPROP_ORDERBYCOLUMNSINSELECT</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Output Parameter Availability</para>
            </TD>
            <TD>
              <para>DBPROP_OUTPUTPARAMETERAVAILABILITY</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Password</para>
            </TD>
            <TD>
              <para>DBPROP_AUTH_PASSWORD</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Pass By Ref Accessors</para>
            </TD>
            <TD>
              <para>DBPROP_BYREFACCESSORS</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Persist Security Info</para>
            </TD>
            <TD>
              <para>DBPROP_AUTH_PERSIST_SENSITIVE_AUTHINFO</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Persistent ID Type</para>
            </TD>
            <TD>
              <para>DBPROP_PERSISTENTIDTYPE</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Prepare Abort Behavior</para>
            </TD>
            <TD>
              <para>DBPROP_PREPAREABORTBEHAVIOR</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Prepare Commit Behavior</para>
            </TD>
            <TD>
              <para>DBPROP_PREPARECOMMITBEHAVIOR</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Procedure Term</para>
            </TD>
            <TD>
              <para>DBPROP_PROCEDURETERM</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Prompt</para>
            </TD>
            <TD>
              <para>DBPROP_INIT_PROMPT</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Provider Friendly Name</para>
            </TD>
            <TD>
              <para>DBPROP_PROVIDERFRIENDLYNAME</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Provider Name</para>
            </TD>
            <TD>
              <para>DBPROP_PROVIDERFILENAME</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Provider Version</para>
            </TD>
            <TD>
              <para>DBPROP_PROVIDERVER</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Read-Only Data Source</para>
            </TD>
            <TD>
              <para>DBPROP_DATASOURCEREADONLY</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Rowset Conversions on Command</para>
            </TD>
            <TD>
              <para>DBPROP_ROWSETCONVERSIONSONCOMMAND</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Schema Term</para>
            </TD>
            <TD>
              <para>DBPROP_SCHEMATERM</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Schema Usage</para>
            </TD>
            <TD>
              <para>DBPROP_SCHEMAUSAGE</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL Support</para>
            </TD>
            <TD>
              <para>DBPROP_SQLSUPPORT</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Structured Storage</para>
            </TD>
            <TD>
              <para>DBPROP_STRUCTUREDSTORAGE</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Subquery Support</para>
            </TD>
            <TD>
              <para>DBPROP_SUBQUERIES</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Table Term</para>
            </TD>
            <TD>
              <para>DBPROP_TABLETERM</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Transaction DDL</para>
            </TD>
            <TD>
              <para>DBPROP_SUPPORTEDTXNDDL</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>User ID</para>
            </TD>
            <TD>
              <para>DBPROP_AUTH_USERID</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>User Name</para>
            </TD>
            <TD>
              <para>DBPROP_USERNAME</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Window Handle</para>
            </TD>
            <TD>
              <para>DBPROP_INIT_HWND</para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <section>
    <title>Recordset Dynamic Properties</title>
    <content>
      <para>The following properties are added to the <legacyBold>Recordset</legacyBold> object's <legacyBold>Properties</legacyBold> collection.</para>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>ADO Property Name</para>
            </TD>
            <TD>
              <para>OLE DB Property Name</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>Access Order</para>
            </TD>
            <TD>
              <para>DBPROP_ACCESSORDER</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Blocking Storage Objects</para>
            </TD>
            <TD>
              <para>DBPROP_BLOCKINGSTORAGEOBJECTS</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Bookmark Type</para>
            </TD>
            <TD>
              <para>DBPROP_BOOKMARKTYPE</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Bookmarkable</para>
            </TD>
            <TD>
              <para>DBPROP_IROWSETLOCATE</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Change Inserted Rows</para>
            </TD>
            <TD>
              <para>DBPROP_CHANGEINSERTEDROWS</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Column Privileges</para>
            </TD>
            <TD>
              <para>DBPROP_COLUMNRESTRICT</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Column Set Notification</para>
            </TD>
            <TD>
              <para>DBPROP_NOTIFYCOLUMNSET</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Delay Storage Object Updates</para>
            </TD>
            <TD>
              <para>DBPROP_DELAYSTORAGEOBJECTS</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Fetch Backwards</para>
            </TD>
            <TD>
              <para>DBPROP_CANFETCHBACKWARDS</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Hold Rows</para>
            </TD>
            <TD>
              <para>DBPROP_CANHOLDROWS</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>IAccessor</para>
            </TD>
            <TD>
              <para>DBPROP_IAccessor</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>IColumnsInfo</para>
            </TD>
            <TD>
              <para>DBPROP_IColumnsInfo</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>IColumnsRowset</para>
            </TD>
            <TD>
              <para>DBPROP_IColumnsRowset</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>IConnectionPointContainer</para>
            </TD>
            <TD>
              <para>DBPROP_IConnectionPointContainer</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>IConvertType</para>
            </TD>
            <TD>
              <para>DBPROP_IConvertType</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Immobile Rows</para>
            </TD>
            <TD>
              <para>DBPROP_IMMOBILEROWS</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>IRowset</para>
            </TD>
            <TD>
              <para>DBPROP_IRowset</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>IRowsetChange</para>
            </TD>
            <TD>
              <para>DBPROP_IRowsetChange</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>IRowsetIdentity</para>
            </TD>
            <TD>
              <para>DBPROP_IRowsetIdentity</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>IRowsetInfo</para>
            </TD>
            <TD>
              <para>DBPROP_IRowsetInfo</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>IRowsetLocate</para>
            </TD>
            <TD>
              <para>DBPROP_IRowsetLocate</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>IRowsetResynch</para>
            </TD>
            <TD>
              <para> </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>IRowsetUpdate</para>
            </TD>
            <TD>
              <para>DBPROP_IRowsetUpdate</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>ISequentialStream</para>
            </TD>
            <TD>
              <para>DBPROP_ISequentialStream</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>ISupportErrorInfo</para>
            </TD>
            <TD>
              <para>DBPROP_ISupportErrorInfo</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Literal Bookmarks</para>
            </TD>
            <TD>
              <para>DBPROP_LITERALBOOKMARKS</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Literal Row Identity</para>
            </TD>
            <TD>
              <para>DBPROP_LITERALIDENTITY</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Maximum Open Rows</para>
            </TD>
            <TD>
              <para>DBPROP_MAXOPENROWS</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Maximum Pending Rows</para>
            </TD>
            <TD>
              <para>DBPROP_MAXPENDINGROWS</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Maximum Rows</para>
            </TD>
            <TD>
              <para>DBPROP_MAXROWS</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Notification Granularity</para>
            </TD>
            <TD>
              <para>DBPROP_NOTIFICATIONGRANULARITY</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Notification Phases</para>
            </TD>
            <TD>
              <para>DBPROP_NOTIFICATIONPHASES</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Objects Transacted</para>
            </TD>
            <TD>
              <para>DBPROP_TRANSACTEDOBJECT</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Own Changes Visible</para>
            </TD>
            <TD>
              <para>DBPROP_OWNUPDATEDELETE</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Own Inserts Visible</para>
            </TD>
            <TD>
              <para>DBPROP_OWNINSERT</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Preserve on Abort</para>
            </TD>
            <TD>
              <para>DBPROP_ABORTPRESERVE</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Preserve on Commit</para>
            </TD>
            <TD>
              <para>DBPROP_COMMITPRESERVE</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Quick Restart</para>
            </TD>
            <TD>
              <para>DBPROP_QUICKRESTART</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Reentrant Events</para>
            </TD>
            <TD>
              <para>DBPROP_REENTRANTEVENTS</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Remove Deleted Rows</para>
            </TD>
            <TD>
              <para>DBPROP_REMOVEDELETED</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Report Multiple Changes</para>
            </TD>
            <TD>
              <para>DBPROP_REPORTMULTIPLECHANGES</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Return Pending Inserts</para>
            </TD>
            <TD>
              <para>DBPROP_RETURNPENDINGINSERTS</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Row Delete Notification</para>
            </TD>
            <TD>
              <para>DBPROP_NOTIFYROWDELETE</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Row First Change Notification</para>
            </TD>
            <TD>
              <para>DBPROP_NOTIFYROWFIRSTCHANGE</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Row Insert Notification</para>
            </TD>
            <TD>
              <para>DBPROP_NOTIFYROWINSERT</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Row Privileges</para>
            </TD>
            <TD>
              <para>DBPROP_ROWRESTRICT</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Row Resynchronization Notification</para>
            </TD>
            <TD>
              <para>DBPROP_NOTIFYROWRESYNCH</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Row Threading Model</para>
            </TD>
            <TD>
              <para>DBPROP_ROWTHREADMODEL</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Row Undo Change Notification</para>
            </TD>
            <TD>
              <para>DBPROP_NOTIFYROWUNDOCHANGE</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Row Undo Delete Notification</para>
            </TD>
            <TD>
              <para>DBPROP_NOTIFYROWUNDODELETE</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Row Undo Insert Notification</para>
            </TD>
            <TD>
              <para>DBPROP_NOTIFYROWUNDOINSERT</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Row Update Notification</para>
            </TD>
            <TD>
              <para>DBPROP_NOTIFYROWUPDATE</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Rowset Fetch Position Change Notification</para>
            </TD>
            <TD>
              <para>DBPROP_NOTIFYROWSETFETCHPOSISIONCHANGE</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Rowset Release Notification</para>
            </TD>
            <TD>
              <para>DBPROP_NOTIFYROWSETRELEASE</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Scroll Backwards</para>
            </TD>
            <TD>
              <para>DBPROP_CANSCROLLBACKWARDS</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Skip Deleted Bookmarks</para>
            </TD>
            <TD>
              <para>DBPROP_BOOKMARKSKIPPED</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Strong Row Identity</para>
            </TD>
            <TD>
              <para>DBPROP_STRONGITDENTITY</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Unique Rows</para>
            </TD>
            <TD>
              <para>DBPROP_UNIQUEROWS</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Updatability</para>
            </TD>
            <TD>
              <para>DBPROP_UPDATABILITY</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Use Bookmarks</para>
            </TD>
            <TD>
              <para>DBPROP_BOOKMARKS</para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <section>
    <title>Command Dynamic Properties</title>
    <content>
      <para>The following properties are added to the <legacyBold>Command</legacyBold> object's <legacyBold>Properties</legacyBold> collection.</para>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>ADO Property Name</para>
            </TD>
            <TD>
              <para>OLE DB Property Name</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>Access Order</para>
            </TD>
            <TD>
              <para>DBPROP_ACCESSORDER</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Blocking Storage Objects</para>
            </TD>
            <TD>
              <para>DBPROP_BLOCKINGSTORAGEOBJECTS</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Bookmark Type</para>
            </TD>
            <TD>
              <para>DBPROP_BOOKMARKTYPE</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Bookmarkable</para>
            </TD>
            <TD>
              <para>DBPROP_IROWSETLOCATE</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Change Inserted Rows</para>
            </TD>
            <TD>
              <para>DBPROP_CHANGEINSERTEDROWS</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Column Privileges</para>
            </TD>
            <TD>
              <para>DBPROP_COLUMNRESTRICT</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Column Set Notification</para>
            </TD>
            <TD>
              <para>DBPROP_NOTIFYCOLUMNSET</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Delay Storage Object Updates</para>
            </TD>
            <TD>
              <para>DBPROP_DELAYSTORAGEOBJECTS</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Fetch Backwards</para>
            </TD>
            <TD>
              <para>DBPROP_CANFETCHBACKWARDS</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Hold Rows</para>
            </TD>
            <TD>
              <para>DBPROP_CANHOLDROWS</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>IAccessor</para>
            </TD>
            <TD>
              <para>DBPROP_IAccessor</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>IColumnsInfo</para>
            </TD>
            <TD>
              <para>DBPROP_IColumnsInfo</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>IColumnsRowset</para>
            </TD>
            <TD>
              <para>DBPROP_IColumnsRowset</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>IConnectionPointContainer</para>
            </TD>
            <TD>
              <para>DBPROP_IConnectionPointContainer</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>IConvertType</para>
            </TD>
            <TD>
              <para>DBPROP_IConvertType</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Immobile Rows</para>
            </TD>
            <TD>
              <para>DBPROP_IMMOBILEROWS</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>IRowset</para>
            </TD>
            <TD>
              <para>DBPROP_IRowset</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>IRowsetChange</para>
            </TD>
            <TD>
              <para>DBPROP_IRowsetChange</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>IRowsetIdentity</para>
            </TD>
            <TD>
              <para>DBPROP_IRowsetIdentity</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>IRowsetInfo</para>
            </TD>
            <TD>
              <para>DBPROP_IRowsetInfo</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>IRowsetLocate</para>
            </TD>
            <TD>
              <para>DBPROP_IRowsetLocate</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>IRowsetResynch</para>
            </TD>
            <TD>
              <para> </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>IRowsetUpdate</para>
            </TD>
            <TD>
              <para>DBPROP_IRowsetUpdate</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>ISequentialStream</para>
            </TD>
            <TD>
              <para>DBPROP_ISequentialStream</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>ISupportErrorInfo</para>
            </TD>
            <TD>
              <para>DBPROP_ISupportErrorInfo</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Literal Bookmarks</para>
            </TD>
            <TD>
              <para>DBPROP_LITERALBOOKMARKS</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Literal Row Identity</para>
            </TD>
            <TD>
              <para>DBPROP_LITERALIDENTITY</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Maximum Open Rows</para>
            </TD>
            <TD>
              <para>DBPROP_MAXOPENROWS</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Maximum Pending Rows</para>
            </TD>
            <TD>
              <para>DBPROP_MAXPENDINGROWS</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Maximum Rows</para>
            </TD>
            <TD>
              <para>DBPROP_MAXROWS</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Notification Granularity</para>
            </TD>
            <TD>
              <para>DBPROP_NOTIFICATIONGRANULARITY</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Notification Phases</para>
            </TD>
            <TD>
              <para>DBPROP_NOTIFICATIONPHASES</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Objects Transacted</para>
            </TD>
            <TD>
              <para>DBPROP_TRANSACTEDOBJECT</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Own Changes Visible</para>
            </TD>
            <TD>
              <para>DBPROP_OWNUPDATEDELETE</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Own Inserts Visible</para>
            </TD>
            <TD>
              <para>DBPROP_OWNINSERT</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Preserve on Abort</para>
            </TD>
            <TD>
              <para>DBPROP_ABORTPRESERVE</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Preserve on Commit</para>
            </TD>
            <TD>
              <para>DBPROP_COMMITPRESERVE</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Quick Restart</para>
            </TD>
            <TD>
              <para>DBPROP_QUICKRESTART</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Reentrant Events</para>
            </TD>
            <TD>
              <para>DBPROP_REENTRANTEVENTS</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Remove Deleted Rows</para>
            </TD>
            <TD>
              <para>DBPROP_REMOVEDELETED</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Report Multiple Changes</para>
            </TD>
            <TD>
              <para>DBPROP_REPORTMULTIPLECHANGES</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Return Pending Inserts</para>
            </TD>
            <TD>
              <para>DBPROP_RETURNPENDINGINSERTS</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Row Delete Notification</para>
            </TD>
            <TD>
              <para>DBPROP_NOTIFYROWDELETE</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Row First Change Notification</para>
            </TD>
            <TD>
              <para>DBPROP_NOTIFYROWFIRSTCHANGE</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Row Insert Notification</para>
            </TD>
            <TD>
              <para>DBPROP_NOTIFYROWINSERT</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Row Privileges</para>
            </TD>
            <TD>
              <para>DBPROP_ROWRESTRICT</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Row Resynchronization Notification</para>
            </TD>
            <TD>
              <para>DBPROP_NOTIFYROWRESYNCH</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Row Threading Model</para>
            </TD>
            <TD>
              <para>DBPROP_ROWTHREADMODEL</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Row Undo Change Notification</para>
            </TD>
            <TD>
              <para>DBPROP_NOTIFYROWUNDOCHANGE</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Row Undo Delete Notification</para>
            </TD>
            <TD>
              <para>DBPROP_NOTIFYROWUNDODELETE</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Row Undo Insert Notification</para>
            </TD>
            <TD>
              <para>DBPROP_NOTIFYROWUNDOINSERT</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Row Update Notification</para>
            </TD>
            <TD>
              <para>DBPROP_NOTIFYROWUPDATE</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Rowset Fetch Position Change Notification</para>
            </TD>
            <TD>
              <para>DBPROP_NOTIFYROWSETFETCHPOSITIONCHANGE</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Rowset Release Notification</para>
            </TD>
            <TD>
              <para>DBPROP_NOTIFYROWSETRELEASE</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Scroll Backwards</para>
            </TD>
            <TD>
              <para>DBPROP_CANSCROLLBACKWARDS</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Skip Deleted Bookmarks</para>
            </TD>
            <TD>
              <para>DBPROP_BOOKMARKSKIP</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Strong Row Identity</para>
            </TD>
            <TD>
              <para>DBPROP_STRONGIDENTITY</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Updatability</para>
            </TD>
            <TD>
              <para>DBPROP_UPDATABILITY</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Use Bookmarks</para>
            </TD>
            <TD>
              <para>DBPROP_BOOKMARKS</para>
            </TD>
          </tr>
        </tbody>
      </table>
      <para>For details regarding specific implementation and functional information about the Microsoft OLE DB Provider for ODBC, see the <legacyLink xlink:href="3c5e2dd5-35e5-4a93-ac3a-3818bb43bbf8">OLE DB Programmer's Reference</legacyLink> or visit the Data Access and Storage Developer Center Web site on MSDN.</para>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="a02c22fb-542d-465e-a629-30fd59dcbebf">Command Object</link>
<link xlink:href="4dd7e82a-8da5-4a4e-b439-11a29286fa0e">CommandText Property</link>
<link xlink:href="ef6b1824-5b12-43db-89d7-8f3d13896d4d">Connection Object</link>
<link xlink:href="3be75b75-4d36-4479-ab64-9a456869252a">ConnectionString Property</link>
<link xlink:href="f84a5ff3-0528-4ad7-9bea-9a15103378dd">Execute Method (ADO Command)</link>
<link xlink:href="3236749c-4b71-4235-89e2-ccdfaaa9319d">Open Method (ADO Recordset)</link>
<link xlink:href="497cae10-3913-422a-9753-dcbb0a639b1b">Parameters Collection</link>
<link xlink:href="1d539aa8-ce0d-4418-ab03-8d0a3c1e9d82">Properties Collection</link>
<link xlink:href="0ff70e72-0061-4ffc-90fb-e3ea23129bb2">Provider Property</link>
<link xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset Object</link>
<link xlink:href="298fc41c-0b55-42fc-b373-c5133b4da6a5">Supports Method</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>