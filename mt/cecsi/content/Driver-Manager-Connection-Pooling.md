---
title: "Driver Manager Connection Pooling"
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ee95ffdb-5aa1-49a3-beb2-7695b27c3df9
caps.latest.revision: 31
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Driver Manager Connection Pooling
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Connection pooling enables an application to use a connection from a pool of connections that do not need to be re-established for each use. Once a connection has been created and placed in a pool, an application can reuse that connection without performing the complete connection process.</para>
    <para>Using a pooled connection can result in significant performance gains, because applications can save the overhead involved in making a connection. This can be particularly significant for middle-tier applications that connect over a network or for applications that repeatedly connect and disconnect, such as Internet applications.</para>
    <para>In addition to performance gains, the connection pooling architecture enables an environment and its associated connections to be used by multiple components in a single process. This means that stand-alone components in the same process can interact with each other without being aware of each other. A connection in a connection pool can be used repeatedly by multiple components.</para>
    <alert class="note">
      <para>Connection pooling can be used by an ODBC application exhibiting ODBC 2.<legacyItalic>x</legacyItalic> behavior, as long as the application can call <legacyItalic>SQLSetEnvAttr</legacyItalic>. When using connection pooling, the application must not execute SQL statements that change the database or the context of the database, such as changing the &lt;<legacyItalic>database</legacyItalic> <legacyItalic>name</legacyItalic>&gt;, which changes the catalog used by a data source.</para>
    </alert>
    <para>An ODBC driver must be fully thread-safe, and connections must not have thread affinity to support connection pooling. This means the driver is able to handle a call on any thread at any time and is able to connect on one thread, to use the connection on another thread, and to disconnect on a third thread.</para>
    <para>The connection pool is maintained by the Driver Manager. Connections are drawn from the pool when the application calls <legacyBold>SQLConnect</legacyBold> or <legacyBold>SQLDriverConnect</legacyBold> and are returned to the pool when the application calls <legacyBold>SQLDisconnect</legacyBold>. The size of the pool grows dynamically, based on the requested resource allocations. It shrinks based on the inactivity timeout: If a connection is inactive for a period of time (it has not been used in a connection), it is removed from the pool. The size of the pool is limited only by memory constraints and limits on the server.</para>
    <para>The Driver Manager determines whether a specific connection in a pool should be used according to the arguments passed in <legacyBold>SQLConnect</legacyBold> or <legacyBold>SQLDriverConnect</legacyBold>, and according to the connection attributes set after the connection was allocated.</para>
    <para>When the Driver Manager is pooling connections, it needs to be able to determine if a connection is still working before handing out the connection. Otherwise, the Driver Manager keeps on handing out the dead connection to the application whenever a transient network failure occurs. A new connection attribute has been defined in ODBC 3<legacyItalic>.x</legacyItalic>: SQL_ATTR_CONNECTION_DEAD. This is a read-only connection attribute that returns either SQL_CD_TRUE or SQL_CD_FALSE. The value SQL_CD_TRUE means that the connection has been lost, while the value SQL_CD_FALSE means that the connection is still active. (Drivers conforming to earlier versions of ODBC can also support this attribute.)</para>
    <para>A driver must implement this option efficiently or it will impair the connection pooling performance. Specifically, a call to get this connection attribute should not cause a round trip to the server. Instead, a driver should just return the last known state of the connection. The connection is dead if the last trip to the server failed, and not dead if the last trip succeeded.</para>
  </introduction>
  <languageReferenceRemarks>
    <content>
      <para>If a connection has been lost (reported via SQL_ATTR_CONNECTION_DEAD), the ODBC Driver Manager will destroy that connection by calling SQLDisconnect in the driver. New connection requests might not find a usable connection in the pool. Eventually the Driver Manager might make a new connection, assuming the pool is empty.</para>
      <para>To use a connection pool, an application performs the following steps:</para>
      <list class="ordered">
        <listItem>
          <para>Enables connection pooling by calling <legacyBold>SQLSetEnvAttr</legacyBold> to set the SQL_ATTR_CONNECTION_POOLING environment attribute to SQL_CP_ONE_PER_DRIVER or SQL_CP_ONE_PER_HENV. This call must be made before the application allocates the shared environment for which connection pooling is to be enabled. The environment handle in the call to <legacyBold>SQLSetEnvAttr</legacyBold> should be set to null, which makes SQL_ATTR_CONNECTION_POOLING a process-level attribute. If the attribute is set to SQL_CP_ONE_PER_DRIVER, a single connection pool is supported for each driver. If an application works with many drivers and few environments, this might be more efficient because fewer comparisons may be required. If set to SQL_CP_ONE_PER_HENV, a single connection pool is supported for each environment. If an application works with many environments and few drivers, this might be more efficient because fewer comparisons may be required. Connection pooling is disabled by setting SQL_ATTR_CONNECTION_POOLING to SQL_CP_OFF.</para>
        </listItem>
        <listItem>
          <para>Allocates an environment by calling <legacyBold>SQLAllocHandle</legacyBold> with the <legacyItalic>HandleType</legacyItalic> argument set to SQL_HANDLE_ENV. The environment allocated by this call will be an implicit shared environment because connection pooling has been enabled. The environment to be used is not determined, however, until <legacyBold>SQLAllocHandle</legacyBold> with a <legacyItalic>HandleType</legacyItalic> of SQL_HANDLE_DBC is called on this environment.</para>
        </listItem>
        <listItem>
          <para>Allocates a connection by calling <legacyBold>SQLAllocHandle</legacyBold> with <legacyItalic>InputHandle</legacyItalic> set to SQL_HANDLE_DBC, and the <legacyItalic>InputHandle</legacyItalic> set to the environment handle allocated for connection pooling. The Driver Manager attempts to find an existing environment that matches the environment attributes set by the application. If no such environment exists, one is created, with a reference count (maintained by the Driver Manager) of 1. If a matching shared environment is found, the environment is returned to the application and its reference count is incremented. (The actual connection to be used is not determined by the Driver Manager until <legacyBold>SQLConnect</legacyBold> or <legacyBold>SQLDriverConnect</legacyBold> is called.)</para>
        </listItem>
        <listItem>
          <para>Calls <legacyBold>SQLConnect</legacyBold> or <legacyBold>SQLDriverConnect</legacyBold> to make the connection. The Driver Manager uses the connection options in the call to <legacyBold>SQLConnect</legacyBold> (or the connection keywords in the call to <legacyBold>SQLDriverConnect</legacyBold>) and the connection attributes set after connection allocation to determine which connection in the pool should be used.</para>
          <alert class="note">
            <para>How a requested connection is matched to a pooled connection is determined by the SQL_ATTR_CP_MATCH environment attribute. For more information, see <legacyLink xlink:href="0343241c-4b15-4d4b-aa2b-2e8ab5215cd2">SQLSetEnvAttr</legacyLink>.</para>
          </alert>
          <para>ODBC applications using connection pooling should call <externalLink><linkText>CoInitializeEx</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkID=116307</linkUri></externalLink> during application initialization and <externalLink><linkText>CoUninitialize</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=116310</linkUri></externalLink> when the application closes.</para>
        </listItem>
        <listItem>
          <para>Calls <legacyBold>SQLDisconnect</legacyBold> when done with the connection. The connection is returned to the connection pool and becomes available for reuse. </para>
        </listItem>
      </list>
      <para>For an in-depth discussion, see <externalLink><linkText>Pooling in the Microsoft Data Access Components</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=120776</linkUri></externalLink>.</para>
    </content>
  </languageReferenceRemarks>
  <section>
    <title>Connection Pooling Considerations</title>
    <content>
      <para>Performing any of the following actions using a SQL command (rather than through the ODBC API) can affect the connection's state and cause unexpected problems when connection pooling is active:</para>
      <list class="bullet">
        <listItem>
          <para>Opening a connection and changing the default database.</para>
        </listItem>
        <listItem>
          <para>Using the SET statement to change any configurable options (including SET ROWCOUNT, ANSI_NULL, IMPLICIT_TRANSACTIONS, SHOWPLAN, STATISTICS, TEXTSIZE, and DATEFORMAT).</para>
        </listItem>
        <listItem>
          <para>Creating temporary tables and stored procedures.</para>
        </listItem>
      </list>
      <para>If any of these actions are performed outside of the ODBC API, the next person who uses the connection will automatically inherit the previous settings, tables, or procedures.</para>
      <alert class="note">
        <para>Do not expect certain settings to be present in the connection state. You should always set the connection state in your application and ensure that the application removes any unused connection pooling settings.</para>
      </alert>
    </content>
  </section>
  <section>
    <title>Driver-Aware Connection Pooling</title>
    <content>
      <para>Beginning in Windows 8, an ODBC driver can use connections in the pool more efficiently. For more information, see <link xlink:href="53e7e3f7-edab-4d0b-8943-45442ba3ebc9">Driver-Aware Connection Pooling</link>.</para>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="e93027ab-9e60-47b7-ba96-8289dae32a22">Connecting to a Data Source or Driver</link>
<link xlink:href="3225a011-5605-46ba-bb74-1ca6106a5271">Developing an ODBC Driver</link>
<externalLink><linkText>Pooling in the Microsoft Data Access Components</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=120776</linkUri></externalLink>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>