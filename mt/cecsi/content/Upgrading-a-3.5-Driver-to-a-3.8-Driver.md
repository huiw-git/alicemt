---
title: Upgrading a 3.5 Driver to a 3.8 Driver
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ffba36ac-d22e-40b9-911a-973fa9e10bd3
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Upgrading a 3.5 Driver to a 3.8 Driver
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This topic provides guidelines and considerations for upgrading an ODBC 3.5 driver to an ODBC 3.8 driver.</para>
  </introduction>
  <section>
    <content />
    <sections>
      <section>
        <content />
        <sections>
          <section>
            <content />
            <sections>
              <section>
                <title>Version Numbers</title>
                <content>
                  <para>The following guidelines relate to version numbers:</para>
                  <list class="bullet">
                    <listItem>
                      <para>A driver should support SQL_OV_ODBC3_80 for SQL_ATTR_ODBC_VERSION, returning SQL_ERROR for values other than SQL_OV_ODBC2, SQL_OV_ODBC3, and SQL_OV_ODBC3_80. Future versions of the Driver Manager will assume that a driver supports an ODBC compliance level if the driver returns SQL_SUCCESS from <link xlink:href="0343241c-4b15-4d4b-aa2b-2e8ab5215cd2">SQLSetEnvAttr</link>.</para>
                    </listItem>
                    <listItem>
                      <para>A version 3.8 driver should return 03.80 from <unmanagedCodeEntityReference>SQLGetInfo</unmanagedCodeEntityReference> when SQL_DRIVER_ODBC_VER is passed to <parameterReference>InfoType</parameterReference>. However, older Driver Managers, which were included in older versions of Microsoft Windows, will treat the driver as a version 3.5 driver, and issue a warning.</para>
                      <para>In Windows 7, the Driver Manager version is 03.80. In Windows 8, the Driver Manager version is 03.81 via the SQLGetInfo SQL_DM_VER (<parameterReference>InfoType</parameterReference> parameter). SQL_ODBC_VER reports the version as 03.80 in both Windows 7 and Windows 8.</para>
                    </listItem>
                  </list>
                </content>
              </section>
              <section>
                <title>Driver-Specific C Data Types</title>
                <content>
                  <para>A driver can have customized C data types when it works with a version 3.8 ODBC application. (For more information, see <link xlink:href="c91bef31-3794-4736-966a-d50997b2233c">C Data Types in ODBC</link>.) However, there is no requirement for a 3.8 driver to implement any driver-specific C types. But the driver should still perform the range check of C types; the Driver Manager will not do that for 3.8 drivers. To facilitate driver development, the value of the driver specific, C data type can be defined in the following format:</para>
                  <code>SQL_DRIVER_C_TYPE_BASE+0, SQL_DRIVER_C_TYPE_BASE+1</code>
                </content>
              </section>
              <section>
                <title>Driver-specific Data Types, Descriptor Types, Information Types, Diagnostic Types, and Attributes</title>
                <content>
                  <para>When developing a new driver, you should use the driver-specific range for data types, descriptor types, information types, diagnostic types, and attributes. Driver-specific ranges and their base type values are discussed in <link xlink:href="ad4c76d3-5191-4262-b47c-5dd1d19d1154">Driver-Specific Data Types, Descriptor Types, Information Types, Diagnostic Types, and Attributes</link>.</para>
                </content>
              </section>
              <section>
                <title>Connection Pooling</title>
                <content>
                  <para>For better management of connection pooling, ODBC 3.8 introduces the SQL_ATTR_RESET_CONNECTION connection attribute in <unmanagedCodeEntityReference>SQLSetConnectAttr</unmanagedCodeEntityReference>. SQL_RESET_CONNECTION_YES is the only valid value for this attribute. SQL_ATTR_RESET_CONNECTION will be set just before the Driver Manager puts a connection in the connection pool, allowing the driver to reset the other connection attributes to their default values. </para>
                  <para>To avoid unnecessary communication with the server, a driver can defer the connection attribute reset until the next communication with the remote server, after the connection is reused from the pool.</para>
                  <para>Note that SQL_ATTR_RESET_CONNECTION is only used in communication between the Driver Manager and a driver. An application cannot set this attribute directly. All version 3.8 drivers should implement this connection attribute.</para>
                </content>
              </section>
              <section>
                <title>Streamed Output Parameters</title>
                <content>
                  <para>ODBC version 3.8 introduces streamed output parameters, a more scalable way to retrieve output parameters. (For more information, see <link xlink:href="7a8c298a-2160-491d-a300-d36f45568d9c">Retrieving Output Parameters by SQLGetData</link>.) To support this feature, a driver should set SQL_GD_OUTPUT_PARAMS in the return value when SQL_GETDATA_EXTENSIONS is the <parameterReference>InfoType</parameterReference> in a <unmanagedCodeEntityReference>SQLGetInfo</unmanagedCodeEntityReference> call. Support for an SQL type with streamed output parameters must be implemented in the driver. The Driver Manager will not generate an error for an invalid SQL type. The SQL types that support streamed output parameters is defined in the driver.</para>
                  <para>A driver should return SQL_ERROR if the application used <unmanagedCodeEntityReference>SQLGetData</unmanagedCodeEntityReference> to retrieve a parameter that is not the same as the parameter returned by <unmanagedCodeEntityReference>SQLParamData</unmanagedCodeEntityReference>.</para>
                </content>
              </section>
              <section>
                <title>Asynchronous Execution for Connection Operations (Polling Method)</title>
                <content>
                  <para>A driver can enable asynchronous support for various connection operations.</para>
                  <para>Beginning in Windows 7, ODBC supports the polling method (for more information, see <link xlink:href="8cd21734-ef8e-4066-afd5-1f340e213f9c">Asynchronous Execution</link>. There is no requirement for a version 3.8 ODBC driver to implement asynchronous operations on connection handles. Even if a driver does not implement asynchronous operations on connection handles, the driver should still implement the SQL_ASYNC_DBC_FUNCTIONS <parameterReference>InfoType</parameterReference> and return <languageKeyword>SQL_ASYNC_DBC_NOT_CAPABLE</languageKeyword>.</para>
                  <para>When asynchronous connection operations are enabled, the running time of a connection operation is the total time of all repeated calls. If the last repeated call occurs after the total time has exceeded the value set by the SQL_ATTR_CONNECTION_TIMEOUT connection attribute, and the operation has not finished, the driver returns SQL_ERROR and logs a diagnostic record with SQLState HYT01 and the message "Connection timeout expired". There is no timeout if the operation finished.</para>
                </content>
              </section>
              <section>
                <title>SQLCancelHandle Function</title>
                <content>
                  <para>ODBC 3.8 supports <link xlink:href="16049b5b-22a7-4640-9897-c25dd0f19d21">SQLCancelHandle Function</link>, which is used to cancel both connection and statement operations. A driver that supports <unmanagedCodeEntityReference>SQLCancelHandle</unmanagedCodeEntityReference> must export the function. A driver should not cancel any synchronous or asynchronous connection function that is in progress if the application calls <unmanagedCodeEntityReference>SQLCancel</unmanagedCodeEntityReference> or<unmanagedCodeEntityReference> SQLCancelHandle</unmanagedCodeEntityReference> on a statement handle. Similarly, a driver should not cancel any synchronous or asynchronous statement function that is in progress if an application calls <unmanagedCodeEntityReference>SQLCancelHandle</unmanagedCodeEntityReference> on the connection handle. Also, a driver should not cancel the browsing operation (<unmanagedCodeEntityReference>SQLBrowseConnect</unmanagedCodeEntityReference> returns SQL_NEED_DATA) if the application calls <unmanagedCodeEntityReference>SQLCancelHandle</unmanagedCodeEntityReference> on the connection handle. In these cases, a driver should return HY010, "function sequence error".</para>
                  <para>It is not necessary to support both <unmanagedCodeEntityReference>SQLCancelHandle</unmanagedCodeEntityReference> and asynchronous connection operations at the same time. A driver can support asynchronous connection operations but not <unmanagedCodeEntityReference>SQLCancelHandle</unmanagedCodeEntityReference>, or vice versa.</para>
                </content>
              </section>
              <section>
                <title>Suspended Connections</title>
                <content>
                  <para>The ODBC 3.8 Driver Manager can put a connection into suspended state. An application will call <unmanagedCodeEntityReference>SQLDisconnect</unmanagedCodeEntityReference> to release resources associated with the connection. In this case, a driver should try to release as many resources as possible without checking the state of the connection. For more information about the suspended state, see <link xlink:href="ff375ce1-eb50-4693-b1e6-70181a6dbf9f">SQLEndTran</link>.</para>
                </content>
              </section>
              <section>
                <title>Driver-Aware Connection Pooling</title>
                <content>
                  <para>ODBC in Windows 8 allows drivers to customize connection pool behavior. For more information, see <link xlink:href="53e7e3f7-edab-4d0b-8943-45442ba3ebc9">Driver-Aware Connection Pooling</link>.</para>
                </content>
              </section>
              <section>
                <title>Asynchronous Execution (Notification Method)</title>
                <content>
                  <para>ODBC 3.8 supports the notification method for asynchronous operations, available beginning on Windows 8. For more information, see <link xlink:href="e509dad9-5263-4a10-9a4e-03b84b66b6b3">Asynchronous Execution (Notification Method)</link>.</para>
                </content>
              </section>
            </sections>
          </section>
        </sections>
      </section>
    </sections>
  </section>
  <relatedTopics>
<link xlink:href="3225a011-5605-46ba-bb74-1ca6106a5271">Developing an ODBC Driver</link>
<link xlink:href="0a1fa7c0-7494-4706-bec1-1ac2c764f6be">ODBC Drivers</link>
<link xlink:href="854f0bb4-17e9-489b-9595-eefffb8ba99f">What's New in ODBC 3.8</link>
</relatedTopics>
</developerConceptualDocument>