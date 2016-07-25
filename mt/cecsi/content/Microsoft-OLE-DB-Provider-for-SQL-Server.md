---
title: "Microsoft OLE DB Provider for SQL Server"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 99bc40c4-9181-4ca1-a06f-9a1a914a0b7b
caps.latest.revision: 18
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
# Microsoft OLE DB Provider for SQL Server
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The Microsoft OLE DB Provider for SQL Server, SQLOLEDB, allows ADO to access Microsoft SQL Server.</para>
  </introduction>
  <section>
    <title>Connection String Parameters</title>
    <content>
      <para>To connect to this provider, set the <legacyItalic>Provider</legacyItalic> argument to the <legacyLink xlink:href="3be75b75-4d36-4479-ab64-9a456869252a">ConnectionString</legacyLink> property to:</para>
      <code>SQLOLEDB</code>
      <para>This value can also be set or read using the <legacyLink xlink:href="0ff70e72-0061-4ffc-90fb-e3ea23129bb2">Provider</legacyLink> property.</para>
    </content>
  </section>
  <section>
    <title>Typical Connection String</title>
    <content>
      <para>A typical connection string for this provider is:</para>
      <code>"Provider=SQLOLEDB;Data Source=<legacyItalic>serverName</legacyItalic>;"
Initial Catalog=<legacyItalic>databaseName</legacyItalic>;
User ID=<legacyItalic>MyUserID</legacyItalic>;Password=<legacyItalic>MyPassword</legacyItalic>;"</code>
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
              <para>Specifies the OLE DB Provider for SQL Server. </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyBold>Data Source</legacyBold> or <legacyBold>Server</legacyBold></para>
            </TD>
            <TD>
              <para>Specifies the name of a server. </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyBold>Initial Catalog</legacyBold> or <legacyBold>Database</legacyBold></para>
            </TD>
            <TD>
              <para>Specifies the name of a database on the server.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyBold>User ID</legacyBold> or <legacyBold>uid</legacyBold></para>
            </TD>
            <TD>
              <para>Specifies the user name (for SQL Server Authentication).</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyBold>Password</legacyBold> or <legacyBold>pwd</legacyBold></para>
            </TD>
            <TD>
              <para>Specifies the user password (for SQL Server Authentication).</para>
            </TD>
          </tr>
        </tbody>
      </table>
      <alert class="note">
        <para>If you are connecting to a data source provider that supports Windows authentication, you should specify <languageKeyword>Trusted_Connection=yes</languageKeyword> or <languageKeyword>Integrated Security = SSPI</languageKeyword> instead of user ID and password information in the connection string.</para>
      </alert>
    </content>
  </section>
  <section>
    <title>Provider-Specific Connection Parameters</title>
    <content>
      <para>The provider supports several provider-specific connection parameters in addition to those defined by ADO. As with the ADO connection properties, these provider-specific properties can be set via the <legacyLink xlink:href="1d539aa8-ce0d-4418-ab03-8d0a3c1e9d82">Properties</legacyLink> collection of a <legacyLink xlink:href="ef6b1824-5b12-43db-89d7-8f3d13896d4d">Connection</legacyLink> or can be set as part of the <legacyBold>ConnectionString</legacyBold>.</para>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>Parameter</para>
            </TD>
            <TD>
              <para>Description</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>Trusted_Connection</para>
            </TD>
            <TD>
              <para>Indicates the user authentication mode. This can be set to <legacyBold>Yes</legacyBold> or <legacyBold>No</legacyBold>. The default value is <legacyBold>No</legacyBold>. If this property is set to <legacyBold>Yes</legacyBold>, SQLOLEDB uses Microsoft Windows NT Authentication Mode to authorize user access to the SQL Server database specified by the <legacyBold>Location</legacyBold> and <legacyLink xlink:href="300a702a-3544-48c5-b759-83b511fe97e0">Datasource</legacyLink> property values. If this property is set to <legacyBold>No</legacyBold>, SQLOLEDB uses Mixed Mode to authorize user access to the SQL Server database. The SQL Server login and password are specified in the <legacyBold>User Id</legacyBold> and <legacyBold>Password</legacyBold> properties.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Current Language</para>
            </TD>
            <TD>
              <para>Indicates a SQL Server language name. Identifies the language used for system message selection and formatting. The language must be installed on the SQL Server, otherwise opening the connection will fail.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Network Address</para>
            </TD>
            <TD>
              <para>Indicates the network address of the SQL Server specified by the <legacyBold>Location</legacyBold> property.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Network Library</para>
            </TD>
            <TD>
              <para>Indicates the name of the network library (DLL) used to communicate with the SQL Server. The name should not include the path or the .dll file name extension. The default is provided by the SQL Server client configuration.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Use Procedure for Prepare</para>
            </TD>
            <TD>
              <para>Determines whether SQL Server creates temporary stored procedures when Commands are prepared (by the <legacyBold>Prepared</legacyBold> property).</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Auto Translate</para>
            </TD>
            <TD>
              <para>Indicates whether OEM/ANSI characters are converted. This property can be set to <legacyBold>True</legacyBold> or <legacyBold>False</legacyBold>. The default value is <legacyBold>True</legacyBold>. If this property is set to <legacyBold>True</legacyBold>, SQLOLEDB performs OEM/ANSI character conversion when multi-byte character strings are retrieved from, or sent to, the SQL Server. If this property is set to <legacyBold>False</legacyBold>, SQLOLEDB does not perform OEM/ANSI character conversion on multi-byte character string data.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Packet Size</para>
            </TD>
            <TD>
              <para>Indicates a network packet size in bytes. The packet size property value must be between 512 and 32767. The default SQLOLEDB network packet size is 4096.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Application Name</para>
            </TD>
            <TD>
              <para>Indicates the client application name.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Workstation ID</para>
            </TD>
            <TD>
              <para>A string identifying the workstation.</para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <section>
    <title>Command Object Usage</title>
    <content>
      <para>SQLOLEDB accepts an amalgam of ODBC, ANSI, and SQL Server-specific Transact-SQL as valid syntax. For example, the following SQL statement uses an ODBC SQL escape sequence to specify the LCASE string function:</para>
      <code>SELECT customerid={fn LCASE(CustomerID)} FROM Customers
  </code>
      <para>LCASE returns a character string, converting all uppercase characters to their lowercase equivalents. The ANSI SQL string function LOWER performs the same operation, so the following SQL statement is an ANSI equivalent to the ODBC statement presented earlier:</para>
      <code>SELECT customerid=LOWER(CustomerID) FROM Customers
  </code>
      <para>SQLOLEDB successfully processes either form of the statement when specified as text for a command.</para>
    </content>
  </section>
  <section>
    <title>Stored Procedures</title>
    <content>
      <para>When executing a SQL Server stored procedure using a SQLOLEDB command, use the ODBC procedure call escape sequence in the command text. SQLOLEDB then uses the remote procedure call mechanism of SQL Server to optimize command processing. For example, the following ODBC SQL statement is the preferred command text over the Transact-SQL form:</para>
    </content>
  </section>
  <section>
    <title>ODBC SQL</title>
    <content>
      <code>{call SalesByCategory('Produce', '1995')}
  </code>
    </content>
  </section>
  <section>
    <title>Transact-SQL</title>
    <content>
      <code>EXECUTE SalesByCategory 'Produce', '1995'
  </code>
    </content>
  </section>
  <section>
    <title>SQL Server Features</title>
    <content>
      <para>With SQL Server, ADO can use XML for <legacyBold>Command</legacyBold> input and retrieve results in XML stream format instead of in <legacyBold>Recordset</legacyBold> objects. For more information, see <legacyLink xlink:href="0ac09dbe-2665-411e-8fbb-d1efe6c777be">Using Streams for Command Input</legacyLink> and <legacyLink xlink:href="996c1321-c926-4f57-8297-85c8c20de974">Retrieving Resultsets Into Streams</legacyLink>.</para>
    </content>
    <sections>
      <section>
        <title>Accessing sql_variant data using MDAC 2.7, MDAC 2.8, or Windows DAC 6.0</title>
        <content>
          <para>Microsoft SQL Server has a data type called <legacyBold>sql_variant</legacyBold>. Similar to OLE DB's <legacyBold>DBTYPE_VARIANT</legacyBold>, the <legacyBold>sql_variant</legacyBold> data type can store data of several different types. However, there are a few key differences between <legacyBold>DBTYPE_VARIANT</legacyBold> and <legacyBold>sql_variant</legacyBold>. ADO also handles data stored as a <legacyBold>sql_variant</legacyBold> value differently than how it handles other data types. The following list describes issues to consider when you access SQL Server data stored in columns of type <legacyBold>sql_variant</legacyBold>.  </para>
          <list class="bullet">
            <listItem>
              <para>In MDAC 2.7, MDAC 2.8, and Windows Data Access Components (Windows DAC) 6.0, the OLE DB Provider for SQL Server supports the <legacyBold>sql_variant</legacyBold> type. The OLE DB Provider for ODBC does not.</para>
            </listItem>
            <listItem>
              <para>The <legacyBold>sql_variant</legacyBold> type does not exactly match the <legacyBold>DBTYPE_VARIANT</legacyBold> data type.  The <legacyBold>sql_variant</legacyBold> type supports a few new subtypes not supported by <legacyBold>DBTYPE_VARIANT,</legacyBold> including <legacyBold>GUID</legacyBold>, <legacyBold>ANSI</legacyBold> (non-UNICODE) strings, and <legacyBold>BIGINT</legacyBold>. Using subtypes other than those listed earlier will work correctly. </para>
            </listItem>
            <listItem>
              <para>The <legacyBold>sql_variant</legacyBold> subtype <legacyBold>NUMERIC</legacyBold> does not match the <legacyBold>DBTYPE_DECIMAL</legacyBold> in size.</para>
            </listItem>
            <listItem>
              <para>Multiple data type coercions will result in types that do not match. For example, coercing a <legacyBold>sql_variant</legacyBold> with a subtype of <legacyBold>GUID</legacyBold> to a <legacyBold>DBTYPE_VARIANT</legacyBold> will result in a subtype of <legacyBold>safearray</legacyBold>(bytes). Converting this type back to a <legacyBold>sql_variant</legacyBold> will result in a new subtype of <legacyBold>array</legacyBold>(bytes). </para>
            </listItem>
            <listItem>
              <para>  <legacyBold>Recordset</legacyBold> fields that contain <legacyBold>sql_variant</legacyBold> data can be remoted (marshaled) or persisted only if the <legacyBold>sql_variant</legacyBold> contains specific subtypes. Attempting to remote or persist data with the following unsupported subtypes will cause a run-time error (unsupported conversion) from the Microsoft Persistence Provider (MSPersist): <legacyBold>VT_VARIANT</legacyBold>, <legacyBold>VT_RECORD</legacyBold>, <legacyBold>VT_ILLEGAL</legacyBold>, <legacyBold>VT_UNKNOWN</legacyBold>, <legacyBold>VT_BSTR</legacyBold>, and <legacyBold>VT_DISPATCH.</legacyBold></para>
            </listItem>
            <listItem>
              <para>The OLE DB Provider for SQL Server in MDAC 2.7, MDAC 2.8, and Windows DAC 6.0 has a dynamic property called <legacyBold>Allow Native Variants</legacyBold> which, as the name implies, allows developers to access the <legacyBold>sql_variant</legacyBold> in its native form as opposed to a <legacyBold>DBTYPE_VARIANT</legacyBold>. If this property is set, and a <legacyBold>Recordset</legacyBold> is opened with the Client Cursor Engine (<legacyBold>adUseClient</legacyBold>), the <legacyBold>Recordset.Open</legacyBold> call will fail. If this property is set and a <legacyBold>Recordset</legacyBold> is opened with server cursors (<legacyBold>adUseServer</legacyBold>), the <legacyBold>Recordset.Open</legacyBold> call will succeed, but accessing columns of type <legacyBold>sql_variant</legacyBold> will produce an error.</para>
            </listItem>
            <listItem>
              <para>In client applications that use MDAC 2.5, <legacyBold>sql_variant </legacyBold>data can be used with queries against Microsoft SQL Server. However, the values of the <legacyBold>sql_variant</legacyBold> data are treated as strings. Such client applications should be upgraded to MDAC 2.7, MDAC 2.8, or Windows DAC 6.0. </para>
            </listItem>
          </list>
        </content>
      </section>
    </sections>
  </section>
  <section>
    <title>Recordset Behavior</title>
    <content>
      <para>SQLOLEDB cannot use SQL Server cursors to support the multiple-result generated by many commands. If a consumer requests a recordset requiring SQL Server cursor support, an error occurs if the command text used generates more than a single recordset as its result.</para>
      <para>Scrollable SQLOLEDB recordsets are supported by SQL Server cursors. SQL Server imposes limitations on cursors that are sensitive to changes made by other users of the database. Specifically, the rows in some cursors cannot be ordered, and attempting to create a recordset using a command containing an SQL ORDER BY clause can fail.</para>
    </content>
  </section>
  <section>
    <title>Dynamic Properties</title>
    <content>
      <para>The Microsoft OLE DB Provider for SQL Server inserts several dynamic properties into the <legacyBold>Properties</legacyBold> collection of the unopened <legacyLink xlink:href="ef6b1824-5b12-43db-89d7-8f3d13896d4d">Connection</legacyLink>, <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink>, and <legacyLink xlink:href="a02c22fb-542d-465e-a629-30fd59dcbebf">Command</legacyLink> objects. </para>
      <para>The following tables are a cross-index of the ADO and OLE DB names for each dynamic property. The OLE DB Programmer's Reference refers to an ADO property name by the term "Description." You can find more information about these properties in the OLE DB Programmer's Reference. Search for the OLE DB property name in the Index or see <legacyLink xlink:href="deded3ff-f508-4e1b-b2b1-fd9afd3bd292">Appendix C: OLE DB Properties</legacyLink>.</para>
    </content>
  </section>
  <section>
    <title>Connection Dynamic Properties</title>
    <content>
      <para>The following properties are added to the <legacyBold>Properties</legacyBold> collection of the <legacyBold>Connection</legacyBold> object.</para>
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
              <para>Pass By Ref Accessors</para>
            </TD>
            <TD>
              <para>DBPROP_BYREFACCESSORS</para>
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
      <para>The following properties are added to the <legacyBold>Properties</legacyBold> collection of the <legacyBold>Recordset</legacyBold> object.</para>
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
              <para>Command Time Out</para>
            </TD>
            <TD>
              <para>DBPROP_COMMANDTIMEOUT</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Defer Column</para>
            </TD>
            <TD>
              <para>DBPROP_DEFERRED</para>
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
              <para>DBPROP_IRowsestLocate</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>IRowsetResynch</para>
            </TD>
            <TD>
              <para>              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>IRowsetScroll</para>
            </TD>
            <TD>
              <para>DBPROP_IRowsetScroll</para>
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
              <para>Others' Changes Visible</para>
            </TD>
            <TD>
              <para>DBPROP_OTHERUPDATEDELETE</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Others' Inserts Visible</para>
            </TD>
            <TD>
              <para>DBPROP_OTHERINSERT</para>
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
              <para>Server Cursor</para>
            </TD>
            <TD>
              <para>DBPROP_SERVERCURSOR</para>
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
      <para>The following properties are added to the <legacyBold>Properties</legacyBold> collection of the <legacyBold>Command</legacyBold> object.</para>
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
              <para>Base Path</para>
            </TD>
            <TD>
              <para>SSPROP_STREAM_BASEPATH</para>
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
              <para>Content Type</para>
            </TD>
            <TD>
              <para>SSPROP_STREAM_CONTENTTYPE</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Cursor Auto Fetch</para>
            </TD>
            <TD>
              <para>SSPROP_CURSORAUTOFETCH</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Defer Column</para>
            </TD>
            <TD>
              <para>DBPROP_DEFERRED</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Defer Prepare</para>
            </TD>
            <TD>
              <para>SSPROP_DEFERPREPARE</para>
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
              <para>DBPROP_IRowsetResynch</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>IRowsetScroll</para>
            </TD>
            <TD>
              <para>DBPROP_IRowsetScroll</para>
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
              <para>Lock Mode</para>
            </TD>
            <TD>
              <para>DBPROP_LOCKMODE</para>
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
              <para>Others' Changes Visible</para>
            </TD>
            <TD>
              <para>DBPROP_OTHERUPDATEDELETE</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Others' Inserts Visible</para>
            </TD>
            <TD>
              <para>DBPROP_OTHERINSERT</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Output Encoding Property</para>
            </TD>
            <TD>
              <para>DBPROP_OUTPUTENCODING</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Output Stream Property</para>
            </TD>
            <TD>
              <para>DBPROP_OUTPUTSTREAM</para>
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
              <para>Server Cursor</para>
            </TD>
            <TD>
              <para>DBPROP_SERVERCURSOR</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Server Data on Insert</para>
            </TD>
            <TD>
              <para>DBPROP_SERVERDATAONINSERT</para>
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
          <tr>
            <TD>
              <para>XML Root</para>
            </TD>
            <TD>
              <para>SSPROP_STREAM_XMLROOT</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>XSL</para>
            </TD>
            <TD>
              <para>SSPROP_STREAM_XSL</para>
            </TD>
          </tr>
        </tbody>
      </table>
      <para>For specific implementation details and functional information about the Microsoft SQL Server OLE DB Provider, see the <legacyLink xlink:href="adf1d6c4-5930-444a-9248-ff1979729635">SQL Server Provider</legacyLink>.</para>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="3be75b75-4d36-4479-ab64-9a456869252a">ConnectionString Property</link>
<link xlink:href="0ff70e72-0061-4ffc-90fb-e3ea23129bb2">Provider Property</link>
<link xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset Object</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>