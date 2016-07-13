---
title: SQLGetConnectOption Mapping
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e3792fe4-a955-473a-a297-c1b2403660c4
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# SQLGetConnectOption Mapping
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>When an application calls <legacyBold>SQLGetConnectOption</legacyBold> through an ODBC 3<legacyItalic>.x</legacyItalic> driver, the call to</para>
  </introduction>
  <section>
    <content>
      <code>SQLGetConnectOption(hdbc, fOption, pvParam) </code>
      <para>is mapped as follows:

</para>
      <list class="bullet">
        <listItem>
          <para>If <legacyItalic>fOption</legacyItalic> indicates an ODBC-defined connection option that returns a string, the Driver Manager calls
</para>
          <code>SQLGetConnectAttr(ConnectionHandle, Attribute, ValuePtr, BufferLength, NULL)</code>
        </listItem>
        <listItem>
          <para>If <legacyItalic>fOption</legacyItalic> indicates an ODBC-defined connection option that returns a 32-bit integer value, the Driver Manager calls 
</para>
          <code>SQLGetConnectAttr(ConnectionHandle, Attribute, ValuePtr, 0, NULL)</code>
        </listItem>
        <listItem>
          <para>If <legacyItalic>fOption</legacyItalic> indicates a driver-defined statement option, the Driver Manager calls 
</para>
          <code>SQLGetConnectAttr(ConnectionHandle, Attribute, ValuePtr, BufferLength, NULL)</code>
        </listItem>
      </list>
      <para>In the preceding three cases, the <legacyItalic>ConnectionHandle</legacyItalic> argument is set to the value in <legacyItalic>hdbc</legacyItalic>, the <legacyItalic>Attribute</legacyItalic> argument is set to the value in <legacyItalic>fOption</legacyItalic>, and the <legacyItalic>ValuePtr</legacyItalic> argument is set to the same value as <legacyItalic>pvParam</legacyItalic>.</para>
      <para>For ODBC-defined string connection options, the Driver Manager sets the <legacyItalic>BufferLength</legacyItalic> argument in the call to <legacyBold>SQLGetConnectAttr</legacyBold> to the predefined maximum length (SQL_MAX_OPTION_STRING_LENGTH); for a nonstring connection option, <legacyItalic>BufferLength</legacyItalic> is set to 0. </para>
      <para>For an ODBC 3<legacyItalic>.x</legacyItalic> driver, the Driver Manager no longer checks to see if <legacyItalic>Option</legacyItalic> is in between SQL_CONN_OPT_MIN and SQL_CONN_OPT_MAX, or is greater than SQL_CONNECT_OPT_DRVR_START. The driver must check the validity of the option values.</para>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>