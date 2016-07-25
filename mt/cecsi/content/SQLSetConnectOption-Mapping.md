---
title: "SQLSetConnectOption Mapping"
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a1b325cf-0c42-41c1-b141-b5a4fee7e708
caps.latest.revision: 4
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# SQLSetConnectOption Mapping
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>When an ODBC 2.<legacyItalic>x</legacyItalic> application calls <legacyBold>SQLSetConnectOption</legacyBold> through an ODBC 3<legacyItalic>.x</legacyItalic> driver, the call to</para>
  </introduction>
  <section>
    <content>
      <code>SQLSetConnectOption(hdbc, fOption, vParam)</code>
      <para>will result as follows:

</para>
      <list class="bullet">
        <listItem>
          <para>If <legacyItalic>fOption</legacyItalic> indicates an ODBC-defined connection attribute that requires a string, the Driver Manager calls 
</para>
          <code>SQLSetConnectAttr(ConnectionHandle, Attribute, ValuePtr, SQL_NTS)</code>
        </listItem>
        <listItem>
          <para>If <legacyItalic>fOption</legacyItalic> indicates an ODBC-defined connection attribute that returns a 32-bit integer value, the Driver Manager calls 
</para>
          <code>SQLSetConnectAttr(ConnectionHandle, Attribute, ValuePtr, 0)</code>
        </listItem>
        <listItem>
          <para>If <legacyItalic>fOption</legacyItalic> indicates a driver-defined connection attribute, the Driver Manager calls 
</para>
          <code>SQLSetConnectAttr(ConnectionHandle, Attribute, ValuePtr, BufferLength)</code>
        </listItem>
      </list>
      <para>In the preceding three cases, the <legacyItalic>ConnectionHandle</legacyItalic> argument is set to the value in <legacyItalic>hdbc</legacyItalic>, the <legacyItalic>Attribute</legacyItalic> argument is set to the value in <legacyItalic>fOption</legacyItalic>, and the <legacyItalic>ValuePtr</legacyItalic> argument is set to the same value as <legacyItalic>vParam</legacyItalic>.</para>
      <para>Because the Driver Manager does not know whether the driver-defined connection attribute needs a string or 32-bit integer value, it has to pass in a valid value for the <legacyItalic>BufferLength</legacyItalic> argument of <legacyBold>SQLSetConnectAttr</legacyBold>. If the driver has defined special semantics for driver-defined connect attributes and needs to be called using <legacyBold>SQLSetConnectOption</legacyBold>, it must support <legacyBold>SQLSetConnectOption</legacyBold>.</para>
      <para>If an ODBC 2.<legacyItalic>x</legacyItalic> application calls <legacyBold>SQLSetConnectOption</legacyBold> to set a driver-specific statement option in an ODBC 3<legacyItalic>.x</legacyItalic> driver, and the option was defined in an ODBC 2.<legacyItalic>x</legacyItalic> version of the driver, a new manifest constant should be defined for the option in the ODBC 3<legacyItalic>.x</legacyItalic> driver. If the old manifest constant is used in the call to <legacyBold>SQLSetConnectOption</legacyBold>, the Driver Manager will call <legacyBold>SQLSetConnectAttr</legacyBold> with the <legacyBold>StringLength</legacyBold> argument set to 0.</para>
      <para>For an ODBC 3<legacyItalic>.x</legacyItalic> driver, the Driver Manager no longer checks to see if <legacyItalic>fOption</legacyItalic> is in between SQL_CONN_OPT_MIN and SQL_CONN_OPT_MAX, or is greater than SQL_CONNECT_OPT_DRVR_START.</para>
    </content>
  </section>
  <section>
    <title>Setting Statement Options on the Connection Level</title>
    <content>
      <para>In ODBC 2.<legacyItalic>x</legacyItalic>, an application could call <legacyBold>SQLSetConnectOption</legacyBold> to set a statement option. When that is done, the driver establishes the statement option as a default for any statements later allocated for that connection. It is driver-defined whether the driver sets the statement option for any existing statements associated with the specified connection. </para>
      <para>This ability has been deprecated in ODBC 3<legacyItalic>.x</legacyItalic>. ODBC 3<legacyItalic>.x</legacyItalic> drivers need only support setting ODBC 2.<legacyItalic>x</legacyItalic> statement attributes at the connection level if they want to work with ODBC 2.<legacyItalic>x</legacyItalic> applications that do this. ODBC 3<legacyItalic>.x</legacyItalic> applications should never set statement attributes at the connection level. ODBC 3<legacyItalic>.x</legacyItalic> statement attributes cannot be set at the connection level, with the exception of the SQL_ATTR_METADATA_ID and SQL_ATTR_ASYNC_ENABLE attributes, which are both connection attributes and statement attributes, and can be set at either the connection level or the statement level.</para>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>