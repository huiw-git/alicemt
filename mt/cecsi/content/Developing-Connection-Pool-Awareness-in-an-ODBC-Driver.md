---
title: Developing Connection-Pool Awareness in an ODBC Driver
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c63d5cae-24fc-4fee-89a9-ad0367cddc3e
manager:jhubbard
translation.priority.ht: 
  - en-gb
---
# Developing Connection-Pool Awareness in an ODBC Driver
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This topic discusses the details of developing an ODBC driver that contains information about how the driver should provide connection pooling services.</para>
  </introduction>
  <section>
    <title>Enabling Driver-Aware Connection Pooling</title>
    <content>
      <para>A driver must implement the following ODBC Service Provider Interface (SPI) functions:</para>
      <list class="bullet">
        <listItem>
          <para>SQLSetConnectAttrForDbcInfo</para>
        </listItem>
        <listItem>
          <para>SQLSetConnectInfo</para>
        </listItem>
        <listItem>
          <para>SQLSetDriverConnectInfo</para>
        </listItem>
        <listItem>
          <para>SQLGetPoolID</para>
        </listItem>
        <listItem>
          <para>SQLRateConnection</para>
        </listItem>
        <listItem>
          <para>SQLPoolConnect</para>
        </listItem>
        <listItem>
          <para>SQLCleanupConnectionPoolID</para>
        </listItem>
      </list>
      <para>See <link xlink:href="cdeffb4a-f344-4abe-97f3-be2ede1c8e59">ODBC Service Provider Interface (SPI) Reference</link> for more information.</para>
      <para>A driver must also implement the following existing functions so that the driver-aware pooling can be enabled:</para>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>Function</para>
            </TD>
            <TD>
              <para>Added Functionality</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>
                <legacyLink xlink:href="6e7fe420-8cf4-4e72-8dad-212affaff317">SQLAllocHandle</legacyLink>
              </para>
              <para>
                <legacyLink xlink:href="17a6fcdc-b05a-4de7-be93-a316f39696a1">SQLFreeHandle</legacyLink>
              </para>
              <para>
                <legacyLink xlink:href="1dbc4398-97a8-4585-bb77-1f7ea75e24c4">SQLGetDiagField</legacyLink>
              </para>
              <para>
                <legacyLink xlink:href="ebdbac93-3d68-438f-8416-ef1f08e04269">SQLGetDiagRec</legacyLink>
              </para>
            </TD>
            <TD>
              <para>Support the new handle type: SQL_HANDLE_DBC_INFO_TOKEN (see the description below).</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <legacyLink xlink:href="97fc7445-5a66-4eb9-8e77-10990b5fd685">SQLSetConnectAttr</legacyLink>
              </para>
            </TD>
            <TD>
              <para>Support the new set-only connection attribute: SQL_ATTR_DBC_INFO_TOKEN for resetting the connection (see the description below).</para>
            </TD>
          </tr>
        </tbody>
      </table>
      <alert class="note">
        <para>Deprecated functions such as <system>SQLError</system> and <system>SQLSetConnectOption</system> are not supported for driver-aware connection pooling.</para>
      </alert>
    </content>
  </section>
  <section>
    <title>The Pool ID</title>
    <content>
      <para>The pool ID is a pointer-length driver-specific ID to represent a particular group of connections that can be used interchangeably. Given a set of connection information, a driver should be able to quickly deduce the corresponding pool ID.</para>
      <para>For example, the pool ID should encode the server name and credential information. However, the database name is not needed because a driver may be able to reuse a connection and then change the database in less time than making a new connection.</para>
      <para>A driver should define a set of key attributes, which will comprise the pool ID. The value of these key attributes can come from connection attributes, connection string, and DSN. In case there are any conflicts in these sources, the existing, driver-specific resolution policy should be used for backward compatibility.</para>
      <para>The Driver Manager will use a different pool for different pool IDs. All connections in the same pool are reusable. The Driver Manager will never reuse a connection with a different pool ID. </para>
      <para>Therefore drivers should assign a unique pool ID for every group of connections with the same value in their defined key attributes. If a driver uses the same pool ID for two connections with different values in their key attributes, the Driver Manager will still put them into the same pool (the Driver Manager knows nothing about the driver-specific key attributes). This means that the driver will need to report to the Driver Manager that a connection with a different set of key attributes is not reusable inside <link xlink:href="e8da2ffb-d6ef-4ca7-824f-57afd29585d8">SQLRateConnection</link>. This can decrease performance and this is not recommended.</para>
      <para>The Driver Manager will not reuse a connection allocated from another driver environment even if all connection information matches. The Driver Manager will use a different pool for different environment, even when connections have the same pool ID. Therefore, the pool ID is local to its driver environment.</para>
      <para>The function for getting the pool ID from the driver is <link xlink:href="95a8666a-ad68-4d89-bf65-f2cc797f8820">SQLGetPoolID</link>.</para>
    </content>
  </section>
  <section>
    <title>The Connection Rating</title>
    <content>
      <para>Compared to establishing a new connection, you can get better performance by resetting some connection information (such as DATABASE) in a pooled connection. So, you may not want the database name to be in your set of key attributes. Otherwise, you can have a separate pool for each database, which may not be good in mid-tier applications, where customers use various different connection strings.</para>
      <para>Whenever you reuse a connection that has some attribute mismatch, you should reset the mismatched attributes based on the new application request, so that the returned connection is identical to the application request (see the discussion of the attribute SQL_ATTR_DBC_INFO_TOKEN in <externalLink><linkText>SQLSetConnectAttr Function</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=59368</linkUri></externalLink>). However, resetting those attributes may decrease performance. For example, resetting a database requires a network call to server. Therefore, reuse a connection that is perfectly matched, if one is available.</para>
      <para>A rating function in the driver can evaluate an existing connection with a new connection request. For example, the driver's rating function can determine:</para>
      <list class="nobullet">
        <listItem>
          <para>If the existing connection is perfectly matched with the request.</para>
        </listItem>
        <listItem>
          <para>If there are only some insignificant mismatches, such as connection timeout, which do not require communication with the server to reset.</para>
        </listItem>
        <listItem>
          <para>If there are some mismatched attributes that require a communication with the server to reset but would still result in better performance than establishing a new connection.</para>
        </listItem>
        <listItem>
          <para>If the mismatched occurred for an attribute that is very time-consuming to reset (the developer of the driver may consider adding this attribute into the set of key attributes, which is used to generate the pool ID).</para>
        </listItem>
      </list>
      <para>A score between 0 and 100 is possible, where 0 means do not reuse and 100 means perfectly matched. <legacyLink xlink:href="e8da2ffb-d6ef-4ca7-824f-57afd29585d8">SQLRateConnection</legacyLink> is the function for rating a connection.</para>
    </content>
  </section>
  <section>
    <title>New ODBC Handle - SQL_HANDLE_DBC_INFO_TOKEN</title>
    <content>
      <para>To support driver-aware connection pooling, the driver needs connection information to compute the Pool ID. The driver also needs connection information to compare new connection requests with connections in the pool.  Whenever no connection in the pool can be reused, the driver has to establish a new connection, hence requiring connection information.</para>
      <para>Since connection information can come from multiple sources (connection string, connection attributes, and DSN), the driver may need to parse the connection string and resolve the conflict between these sources in each of the above function call.</para>
      <para>Therefore, a new ODBC handle is introduced: SQL_HANDLE_DBC_INFO_TOKEN. With SQL_HANDLE_DBC_INFO_TOKEN, a driver does not need to parse the connection string and resolve conflicts in connection information more than once. Since this is a driver-specific data structure, the driver can store data such as connection information or pool ID.</para>
      <para>This handle is only used as an interface between the Driver Manager and driver. An application cannot allocate this handle directly.</para>
      <para>The parent handle of this handle is of type SQL_HANDLE_ENV, meaning that the driver can obtain the environment information from the HENV handle during connection information resolution.</para>
      <para>Whenever it receives a new connection request, the Driver Manager will allocate a handle of type SQL_HANDLE_DBC_INFO_TOKEN for storing connection information, after it confirms that the driver supports connection-pool awareness. When finished using the handle (but before returning some return codes other than SQL_STILL_EXECUTING from <legacyLink xlink:href="e299be1d-5c74-4ede-b6a3-430eb189134f">SQLDriverConnect</legacyLink> or <legacyLink xlink:href="59075e46-a0ca-47bf-972a-367b08bb518d">SQLConnect</legacyLink>), the Driver Manager will free the handle. Therefore, the handle is created after the SQLAllocHandle call, and destroyed after the SQLFreeHandle call. The Driver Manager guarantees the handle will be freed before freeing its associated HENV (when <legacyLink xlink:href="e299be1d-5c74-4ede-b6a3-430eb189134f">SQLDriverConnect</legacyLink> or <legacyLink xlink:href="59075e46-a0ca-47bf-972a-367b08bb518d">SQLConnect</legacyLink> returns an error).</para>
      <para>The driver should modify the following functions to accept the new handle type SQL_HANDLE_DBC_INFO_TOKEN:</para>
      <list class="ordered">
        <listItem>
          <para>
            <legacyLink xlink:href="6e7fe420-8cf4-4e72-8dad-212affaff317">SQLAllocHandle</legacyLink>
          </para>
        </listItem>
        <listItem>
          <para>
            <legacyLink xlink:href="17a6fcdc-b05a-4de7-be93-a316f39696a1">SQLFreeHandle</legacyLink>
          </para>
        </listItem>
        <listItem>
          <para>
            <legacyLink xlink:href="1dbc4398-97a8-4585-bb77-1f7ea75e24c4">SQLGetDiagField</legacyLink>
          </para>
        </listItem>
        <listItem>
          <para>
            <legacyLink xlink:href="ebdbac93-3d68-438f-8416-ef1f08e04269">SQLGetDiagRec</legacyLink>
          </para>
        </listItem>
      </list>
      <para>The Driver Manager guarantees that multiple threads will not use the same SQL_HANDLE_DBC_INFO_TOKEN handle simultaneously. Therefore, the synchronization model of this handle can be very simple inside the driver. The Driver Manager will not take an environment lock before allocating and freeing SQL_HANDLE_DBC_INFO_TOKEN.</para>
      <para>The Driver Manager's <legacyBold>SQLAllocHandle</legacyBold> and <legacyBold>SQLFreeHandle</legacyBold> will not accept this new handle type.</para>
      <para>SQL_HANDLE_DBC_INFO_TOKEN may contain confidential information such as credentials. Therefore, a driver should securely clear the memory buffer (using <externalLink><linkText>SecureZeroMemory</linkText><linkUri>http://msdn.microsoft.com/library/windows/desktop/aa366877(v=vs.85).aspx</linkUri></externalLink>) that contains the sensitive information before releasing this handle with <legacyBold>SQLFreeHandle</legacyBold>. Whenever an application’s environment handle is closed, all associated connection pools will be closed.</para>
    </content>
  </section>
  <section>
    <title>Driver Manager Connection Pool Rating Algorithm</title>
    <content>
      <para>This section discusses the rating algorithm for Driver Manager connection pooling. Driver developers can implement the same algorithm for backward compatibility. This algorithm may not be the best one. You should refine this algorithm based your implementation (otherwise, there is no reason to implement this feature).</para>
      <para>The Driver Manager will return an integral rating from 0 to 100 for each connection from the pool. 0 means the connection cannot be reused and 100 indicates a perfect matched. Assume the connection request is named hRequest and the existing connection from the pool is named as hCandidate. If any one of the following conditions is false, the pooled connection hCandidate cannot be reused for hRequest (the Driver Manager will assign a rating of 0).</para>
      <list class="bullet">
        <listItem>
          <para>hCandidate and hRequest both come from either UNICODE API (such as SQLDriverConnectW) or ANSI API (such as SQLDriverConnectA). (UNICODE drivers can behavior different given ANSI API and UNICODE API (see the connection attribute SQL_ATTR_ANSI_APP).)</para>
        </listItem>
        <listItem>
          <para> hCandidate and hRequest are created by the same function; either SQLDriverConnect or SQLConnect.</para>
        </listItem>
        <listItem>
          <para>The connection string used to open hCandidate should be the same as hRequest, when SQLDriverConnect is used.</para>
        </listItem>
        <listItem>
          <para>The ServerName (or DSN), user name, and password used to open hCandidate should be the same used to open hRequest when SQLConnect is used.</para>
        </listItem>
        <listItem>
          <para>The security identifier (SID) of the current thread should be the same as the SID used to open hCandidate.</para>
        </listItem>
        <listItem>
          <para>For driver that is expensive to enlist and unenlist (see the discussion of SQL_DTC_TRANSITION_COST in <legacyLink xlink:href="59075e46-a0ca-47bf-972a-367b08bb518d">SQLConnect</legacyLink>), reusing <parameterReference>hRequest</parameterReference> must not require an extra enlistment or unenlistment.</para>
        </listItem>
      </list>
      <para>The following table shows score assignment for different scenarios.</para>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>Comparison on connection attributes between the pooled connection and the request</para>
            </TD>
            <TD>
              <para>No Enlistment / unenlistment</para>
            </TD>
            <TD>
              <para>Require Extra Enlistment / Unenlistment</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>Catalog (SQL_ATTR_CURRENT_CATALOG) is different</para>
            </TD>
            <TD>
              <para>60</para>
            </TD>
            <TD>
              <para>50</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Some connection attributes are different, but catalog is the same</para>
            </TD>
            <TD>
              <para>90</para>
            </TD>
            <TD>
              <para>70</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>All connection attributes perfectly matched</para>
            </TD>
            <TD>
              <para>100</para>
            </TD>
            <TD>
              <para>80</para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <section>
    <title>Sequence Diagram</title>
    <content>
      <para>This sequence diagram shows the basic pooling mechanism described in this topic. It only shows the use of <legacyLink xlink:href="e299be1d-5c74-4ede-b6a3-430eb189134f">SQLDriverConnect</legacyLink> but the <legacyLink xlink:href="59075e46-a0ca-47bf-972a-367b08bb518d">SQLConnect</legacyLink> case is similar.</para>
      <mediaLink>
        <image xlink:href="441d53ae-79e1-489f-840c-70ea348e9ff3" />
      </mediaLink>
    </content>
  </section>
  <section>
    <title>State Diagram</title>
    <content>
      <para>This state diagram shows the connection info token object, described in this topic. The diagram only shows <legacyLink xlink:href="e299be1d-5c74-4ede-b6a3-430eb189134f">SQLDriverConnect</legacyLink> but the <legacyLink xlink:href="59075e46-a0ca-47bf-972a-367b08bb518d">SQLConnect</legacyLink> case is similar. Since the Driver Manager may need to handle errors at any time, the Driver Manager can call <legacyLink xlink:href="17a6fcdc-b05a-4de7-be93-a316f39696a1">SQLFreeHandle</legacyLink> for any state.</para>
      <mediaLink>
        <image xlink:href="c6bf1e29-e3a9-46f1-849d-ee74182cfd08" />
      </mediaLink>
    </content>
  </section>
  <relatedTopics>
    <link xlink:href="53e7e3f7-edab-4d0b-8943-45442ba3ebc9">Driver-Aware Connection Pooling</link>
<link xlink:href="cdeffb4a-f344-4abe-97f3-be2ede1c8e59">ODBC Service Provider Interface (SPI) Reference</link></relatedTopics>
</developerConceptualDocument>