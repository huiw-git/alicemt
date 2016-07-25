---
title: "Microsoft OLE DB Provider for Microsoft Jet"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: fd956da1-5203-40af-aa7e-fc13a6c6581f
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
# Microsoft OLE DB Provider for Microsoft Jet
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The OLE DB Provider for Microsoft Jet allows ADO to access Microsoft Jet databases.</para>
  </introduction>
  <section>
    <title>Connection String Parameters</title>
    <content>
      <para>To connect to this provider, set the <legacyItalic>Provider</legacyItalic> argument of the <legacyLink xlink:href="3be75b75-4d36-4479-ab64-9a456869252a">ConnectionString</legacyLink> property to the following:</para>
      <code>Microsoft.Jet.OLEDB.4.0</code>
      <para>Reading the <legacyLink xlink:href="0ff70e72-0061-4ffc-90fb-e3ea23129bb2">Provider</legacyLink> property will also return this string.</para>
    </content>
  </section>
  <section>
    <title>Typical Connection String</title>
    <content>
      <para>A typical connection string for this provider is:</para>
      <code>"Provider=Microsoft.Jet.OLEDB.4.0;Data Source=<legacyItalic>databaseName</legacyItalic>;User ID=<legacyItalic>MyUserID</legacyItalic>;Password=<legacyItalic>MyPassword</legacyItalic>;"</code>
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
              <para>Specifies the OLE DB Provider for Microsoft Jet.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyBold>Data Source</legacyBold>
              </para>
            </TD>
            <TD>
              <para>Specifies the database path and file name (for example, <codeInline>c:\Northwind.mdb</codeInline>).</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyBold>User ID</legacyBold>
              </para>
            </TD>
            <TD>
              <para>Specifies the user name. If this keyword is not specified, the string, "<codeInline>admin</codeInline>", is used by default.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyBold>Password</legacyBold>
              </para>
            </TD>
            <TD>
              <para>Specifies the user password. If this keyword is not specified, the empty string (""), is used by default.</para>
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
      <para>The OLE DB Provider for Microsoft Jet supports several provider-specific dynamic properties in addition to those that are defined by ADO. As with all other <legacyBold>Connection</legacyBold> parameters, they can be set by using the <legacyBold>Properties</legacyBold> collection of the <legacyBold>Connection</legacyBold> object or as part of the connection string.</para>
      <para>The following table lists these properties together with the corresponding OLE DB property name in parentheses.</para>
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
              <para>Jet OLEDB:Compact Reclaimed Space Amount (DBPROP_JETOLEDB_COMPACTFREESPACESIZE)</para>
            </TD>
            <TD>
              <para>Indicates an estimate of the amount of space, in bytes, that can be reclaimed by compacting the database. This value is only valid after a database connection has been established.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Jet OLEDB:Connection Control (DBPROP_JETOLEDB_CONNECTIONCONTROL)</para>
            </TD>
            <TD>
              <para>Indicates whether users can connect to the database.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Jet OLEDB:Create System Database (DBPROP_JETOLEDB_CREATESYSTEMDATABASE)</para>
            </TD>
            <TD>
              <para>Indicates whether a system database should be created when creating a new data source.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Jet OLEDB:Database Locking Mode (DBPROP_JETOLEDB_DATABASELOCKMODE)</para>
            </TD>
            <TD>
              <para>Indicates the locking mode for this database. The first user to open the database determines the mode used while the database is open.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Jet OLEDB:Database Password (DBPROP_JETOLEDB_DATABASEPASSWORD)</para>
            </TD>
            <TD>
              <para>Indicates the database password.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Jet OLEDB:Don't Copy Locale on Compact (DBPROP_JETOLEDB_COMPACT_DONTCOPYLOCALE)</para>
            </TD>
            <TD>
              <para>Indicates whether Jet should copy locale information when compacting a database.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Jet OLEDB:Encrypt Database (DBPROP_JETOLEDB_ENCRYPTDATABASE)</para>
            </TD>
            <TD>
              <para>Indicates whether a compacted database should be encrypted. If this property is not set, the compacted database will be encrypted if the original database was also encrypted.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Jet OLEDB:Engine Type (DBPROP_JETOLEDB_ENGINE)</para>
            </TD>
            <TD>
              <para>Indicates the storage engine used to access the current data store.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Jet OLEDB:Exclusive Async Delay (DBPROP_JETOLEDB_EXCLUSIVEASYNCDELAY)</para>
            </TD>
            <TD>
              <para>Indicates the maximum length of time, in milliseconds, that Jet can delay asynchronous writes to disk when the database is opened exclusively.</para>
              <para>This property is ignored unless <legacyBold>Jet OLEDB:Flush Transaction Timeout</legacyBold> is set to 0.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Jet OLEDB:Flush Transaction Timeout (DBPROP_JETOLEDB_FLUSHTRANSACTIONTIMEOUT)</para>
            </TD>
            <TD>
              <para>Indicates the amount of time to wait before data stored in a cache for asynchronous writing is actually written to disk. This setting overrides the values for <legacyBold>Jet OLEDB:Shared Async Delay</legacyBold> and <legacyBold>Jet OLEDB:Exclusive Async Delay</legacyBold>.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Jet OLEDB:Global Bulk Transactions (DBPROP_JETOLEDB_GLOBALBULKNOTRANSACTIONS)</para>
            </TD>
            <TD>
              <para>Indicates whether SQL bulk transactions are transacted.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Jet OLEDB:Global Partial Bulk Ops (DBPROP_JETOLEDB_GLOBALBULKPARTIAL)</para>
            </TD>
            <TD>
              <para>Indicates the password used to open the database.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Jet OLEDB:Implicit Commit Sync (DBPROP_JETOLEDB_IMPLICITCOMMITSYNC)</para>
            </TD>
            <TD>
              <para>Indicates whether changes that were made in internal implicit transactions are written in synchronous or asynchronous mode.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Jet OLEDB:Lock Delay (DBPROP_JETOLEDB_LOCKDELAY)</para>
            </TD>
            <TD>
              <para>Indicates the number of milliseconds to wait before trying to acquire a lock after a previous attempt has failed.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Jet OLEDB:Lock Retry (DBPROP_JETOLEDB_LOCKRETRY)</para>
            </TD>
            <TD>
              <para>Indicates how many times an attempt to access a locked page is repeated.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Jet OLEDB:Max Buffer Size (DBPROP_JETOLEDB_MAXBUFFERSIZE)</para>
            </TD>
            <TD>
              <para>Indicates the maximum amount of memory, in kilobytes, Jet can use before it starts flushing changes to disk.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Jet OLEDB:Max Locks Per File (DBPROP_JETOLEDB_MAXLOCKSPERFILE)</para>
            </TD>
            <TD>
              <para>Indicates the maximum number of locks Jet can place on a database. The default value is 9500.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Jet OLEDB:New Database Password (DBPROP_JETOLEDB_NEWDATABASEPASSWORD)</para>
            </TD>
            <TD>
              <para>Indicates the new password to be set for this database. The old password is stored in <legacyBold>Jet OLEDB:Database Password</legacyBold>.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Jet OLEDB:ODBC Command Time Out (DBPROP_JETOLEDB_ODBCCOMMANDTIMEOUT)</para>
            </TD>
            <TD>
              <para>Indicates the number of milliseconds before a remote ODBC query from Jet will time out.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Jet OLEDB:Page Locks to Table Lock (DBPROP_JETOLEDB_PAGELOCKSTOTABLELOCK)</para>
            </TD>
            <TD>
              <para>Indicates how many pages must be locked within a transaction before Jet tries to promote the lock to a table lock. If this value is 0, the lock is never promoted.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Jet OLEDB:Page Timeout (DBPROP_JETOLEDB_PAGETIMEOUT)</para>
            </TD>
            <TD>
              <para>Indicates the number of milliseconds Jet will wait before checking to see whether its cache is out of date with the database file.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Jet OLEDB:Recycle Long-Valued Pages (DBPROP_JETOLEDB_RECYCLELONGVALUEPAGES)</para>
            </TD>
            <TD>
              <para>Indicates whether Jet should aggressively try to reclaim BLOB pages when they are freed.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Jet OLEDB:Registry Path (DBPROP_JETOLEDB_REGPATH)</para>
            </TD>
            <TD>
              <para>Indicates the Windows registry key that contains values for the Jet database engine.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Jet OLEDB:Reset ISAM Stats (DBPROP_JETOLEDB_RESETISAMSTATS)</para>
            </TD>
            <TD>
              <para>Indicates whether the schema <legacyBold>Recordset</legacyBold> DBSCHEMA_JETOLEDB_ISAMSTATS should reset its performance counters after it returns performance information.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Jet OLEDB:Shared Async Delay (DBPROP_JETOLEDB_SHAREDASYNCDELAY)</para>
            </TD>
            <TD>
              <para>Indicates the maximum amount of time, in milliseconds, Jet can delay asynchronous writes to disk when the database is opened in multiuser mode.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Jet OLEDB:System Database (DBPROP_JETOLEDB_SYSDBPATH)</para>
            </TD>
            <TD>
              <para>Indicates the path and file name for the workgroup information file (system database).</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Jet OLEDB:Transaction Commit Mode (DBPROP_JETOLEDB_TXNCOMMITMODE)</para>
            </TD>
            <TD>
              <para>Indicates whether Jet writes data to disk synchronously or asynchronously when a transaction is committed.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Jet OLEDB:User Commit Sync (DBPROP_JETOLEDB_USERCOMMITSYNC)</para>
            </TD>
            <TD>
              <para>Indicates whether changes that were made in transactions are written in synchronous or asynchronous mode.</para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <section>
    <title>Provider-Specific Recordset and Command Properties</title>
    <content>
      <para>The Jet provider also supports several provider-specific <legacyBold>Recordset</legacyBold> and <legacyBold>Command</legacyBold> properties. These properties are accessed and set through the <legacyBold>Properties</legacyBold> collection of the <legacyBold>Recordset</legacyBold> or <legacyBold>Command</legacyBold> object. The table lists the ADO property name and its corresponding OLE DB property name in parentheses.</para>
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
              <para>Jet OLEDB:Bulk Transactions (DBPROP_JETOLEDB_BULKNOTRANSACTIONS)</para>
            </TD>
            <TD>
              <para>Indicates whether SQL bulk operations are transacted. Large bulk operations might fail when transacted, because of resource delays.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Jet OLEDB:Enable Fat Cursors (DBPROP_JETOLEDB_ENABLEFATCURSOR)</para>
            </TD>
            <TD>
              <para>Indicates whether Jet should cache multiple rows when populating a recordset for remote row sources.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Jet OLEDB:Fat Cursor Cache Size (DBPROP_JETOLEDB_FATCURSORMAXROWS)</para>
            </TD>
            <TD>
              <para>Indicates the number of rows to cache when using remote data store row caching. This value is ignored unless <legacyBold>Jet OLEDB:Enable Fat Cursors</legacyBold> is True.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Jet OLEDB:Inconsistent (DBPROP_JETOLEDB_INCONSISTENT)</para>
            </TD>
            <TD>
              <para>Indicates whether query results allow inconsistent updates.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Jet OLEDB:Locking Granularity (DBPROP_JETOLEDB_LOCKGRANULARITY)</para>
            </TD>
            <TD>
              <para>Indicates whether a table is opened using row-level locking.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Jet OLEDB:ODBC Pass-Through Statement (DBPROP_JETOLEDB_ODBCPASSTHROUGH)</para>
            </TD>
            <TD>
              <para>Indicates that Jet should pass the SQL text in a <legacyBold>Command</legacyBold> object to the back end unaltered.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Jet OLEDB:Partial Bulk Ops (DBPROP_JETOLEDB_BULKPARTIAL)</para>
            </TD>
            <TD>
              <para>Indicates Jet's behavior when SQL DML operations fail.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Jet OLEDB:Pass Through Query Bulk-Op (DBPROP_JETOLEDB_PASSTHROUGHBULKOP)</para>
            </TD>
            <TD>
              <para>Indicates whether queries that do not return a <legacyBold>Recordset</legacyBold> are passed unaltered to the data source.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Jet OLEDB:Pass Through Query Connect String (DBPROP_JETOLEDB_ODBCPASSTHROUGHCONNECTSTRING)</para>
            </TD>
            <TD>
              <para>Indicates the Jet connect string used to connect to a remote data store. This value is ignored unless <legacyBold>Jet OLEDB:ODBC Pass-Through Statement</legacyBold> is True.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Jet OLEDB:Stored Query (DBPROP_JETOLEDB_STOREDQUERY)</para>
            </TD>
            <TD>
              <para>Indicates whether the command text should be interpreted as a stored query instead of an SQL command.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Jet OLEDB:Validate Rules On Set (DBPROP_JETOLEDB_VALIDATEONSET)</para>
            </TD>
            <TD>
              <para>Indicates whether the Jet validation rules are evaluated when column data is set or when the changes are committed to the database.</para>
            </TD>
          </tr>
        </tbody>
      </table>
      <para>By default, the OLE DB Provider for Microsoft Jet opens Microsoft Jet databases in read/write mode. To open a database in read-only mode, set the <legacyLink xlink:href="808661eb-0d7c-4e6d-8e40-9dc3bef3d77a">Mode</legacyLink> property on the ADO <legacyBold>Connection</legacyBold> object to <legacyBold>adModeRead</legacyBold>.</para>
    </content>
  </section>
  <section>
    <title>Command Object Usage</title>
    <content>
      <para>Command text in the <legacyLink xlink:href="a02c22fb-542d-465e-a629-30fd59dcbebf">Command</legacyLink> object uses the Microsoft Jet SQL dialect. You can specify row-returning queries, action queries, and table names in the command text; however, stored procedures are not supported and should not be specified.</para>
    </content>
  </section>
  <section>
    <title>Recordset Behavior</title>
    <content>
      <para>The Microsoft Jet database engine does not support dynamic cursors. Therefore, the OLE DB Provider for Microsoft Jet does not support the <legacyBold>adLockDynamic</legacyBold> cursor type. When a dynamic cursor is requested, the provider will return a keyset cursor and reset the <legacyLink xlink:href="b62c66ca-58d5-430e-9257-eb38c65e48c2">CursorType</legacyLink> property to indicate the type of <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink> returned. Further, if an updatable <legacyBold>Recordset</legacyBold> is requested (<legacyBold>LockType</legacyBold> is <legacyBold>adLockOptimistic</legacyBold>, <legacyBold>adLockBatchOptimistic</legacyBold>, or <legacyBold>adLockPessimistic</legacyBold>) the provider will also return a keyset cursor and reset the <legacyBold>CursorType</legacyBold> property.</para>
    </content>
  </section>
  <section>
    <title>Dynamic Properties</title>
    <content>
      <para>The OLE DB Provider for Microsoft Jet inserts several dynamic properties into the <legacyBold>Properties</legacyBold> collection of the unopened <legacyLink xlink:href="ef6b1824-5b12-43db-89d7-8f3d13896d4d">Connection</legacyLink>, <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink>, and <legacyLink xlink:href="a02c22fb-542d-465e-a629-30fd59dcbebf">Command</legacyLink> objects.</para>
      <para>The following tables are a cross-index of the ADO and OLE DB names for each dynamic property. The OLE DB Programmer's Reference refers to an ADO property name by the term, "Description." You can find more information about these properties in the OLE DB Programmer's Reference.</para>
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
              <para>Append-Only Rowset</para>
            </TD>
            <TD>
              <para>DBPROP_APPENDONLY</para>
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
              <para>Bookmarks Ordered</para>
            </TD>
            <TD>
              <para>DBPROP_ORDEREDBOOKMARKS</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Cache Deferred Columns</para>
            </TD>
            <TD>
              <para>DBPROP_CACHEDEFERRED</para>
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
              <para>Column Writable</para>
            </TD>
            <TD>
              <para>DBPROP_MAYWRITECOLUMN</para>
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
              <para>ILockBytes</para>
            </TD>
            <TD>
              <para>DBPROP_ILockBytes</para>
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
              <para>IRowsetIndex</para>
            </TD>
            <TD>
              <para>DBPROP_IRowsetIndex</para>
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
              <para> </para>
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
              <para>IStorage</para>
            </TD>
            <TD>
              <para>DBPROP_IStorage</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>IStream</para>
            </TD>
            <TD>
              <para>DBPROP_IStream</para>
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
              <para>Memory Usage</para>
            </TD>
            <TD>
              <para>DBPROP_MEMORYUSAGE</para>
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
              <para>Append-Only Rowset</para>
            </TD>
            <TD>
              <para>DBPROP_APPENDONLY</para>
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
              <para>ILockBytes</para>
            </TD>
            <TD>
              <para>DBPROP_ILockBytes</para>
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
              <para>IRowsetIndex</para>
            </TD>
            <TD>
              <para>DBPROP_IRowsetIndex</para>
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
              <para>IStorage</para>
            </TD>
            <TD>
              <para>DBPROP_IStorage</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>IStream</para>
            </TD>
            <TD>
              <para>DBPROP_IStream</para>
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
        </tbody>
      </table>
      <para>For specific implementation details and functional information about the OLE DB Provider for Microsoft Jet, see <externalLink><linkText>Jet Provider</linkText><linkUri>https://msdn.microsoft.com/library/windows/desktop/ms722791.aspx</linkUri></externalLink> in the OLE DB documentation.</para>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>