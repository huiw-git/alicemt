---
title: "SQLGetStmtOption Mapping"
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: fa599517-3f3e-4dad-a65a-b8596ae3f330
caps.latest.revision: 4
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# SQLGetStmtOption Mapping
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>When an application calls <legacyBold>SQLGetStmtOption</legacyBold> to an ODBC 3<legacyItalic>.x</legacyItalic> driver that does not support it, the call to </para>
  </introduction>
  <section>
    <content>
      <code>SQLGetStmtOption(hstmt, fOption, pvParam)</code>
      <para>will result as follows:

</para>
      <list class="bullet">
        <listItem>
          <para>If <legacyItalic>fOption</legacyItalic> indicates an ODBC-defined statement option that returns a string, the Driver Manager calls 
</para>
          <code>SQLGetStmtAttr(StatementHandle, Attribute, ValuePtr, BufferLength, NULL)</code>
        </listItem>
        <listItem>
          <para>If <legacyItalic>fOption</legacyItalic> indicates an ODBC-defined statement option that returns a 32-bit integer value, the Driver Manager calls 
</para>
          <code>SQLGetStmtAttr(StatementHandle, Attribute, ValuePtr, 0, NULL)</code>
        </listItem>
        <listItem>
          <para>If <legacyItalic>fOption</legacyItalic> indicates a driver-defined statement option, the Driver Manager calls 
</para>
          <code>SQLGetStmtAttr(StatementHandle, Attribute, ValuePtr, BufferLength, NULL)</code>
        </listItem>
      </list>
      <para>In the preceding three cases, the <legacyItalic>StatementHandle</legacyItalic> argument is set to the value in <legacyItalic>hstmt</legacyItalic>, the <legacyItalic>Attribute</legacyItalic> argument is set to the value in <legacyItalic>fOption</legacyItalic>, and the <legacyItalic>ValuePtr</legacyItalic> argument is set to the same value as <legacyItalic>pvParam</legacyItalic>.</para>
      <para>For ODBC-defined string connection options, the Driver Manager sets the <legacyItalic>BufferLength</legacyItalic> argument in the call to <legacyBold>SQLGetConnectAttr</legacyBold> to the predefined maximum length (SQL_MAX_OPTION_STRING_LENGTH); for a nonstring connection option, <legacyItalic>BufferLength</legacyItalic> is set to 0. </para>
      <para>The SQL_GET_BOOKMARK statement option has been deprecated in ODBC 3<legacyItalic>.x</legacyItalic>. For an ODBC 3<legacyItalic>.x</legacyItalic> driver to work with ODBC 2.<legacyItalic>x</legacyItalic> applications that use SQL_GET_BOOKMARK, it must support SQL_GET_BOOKMARK. For an ODBC 3<legacyItalic>.x</legacyItalic> driver to work with ODBC 2.<legacyItalic>x</legacyItalic> applications, it must support setting SQL_USE_BOOKMARKS to SQL_UB_ON and should expose fixed-length bookmarks. If an ODBC 3<legacyItalic>.x</legacyItalic> driver supports only variable-length bookmarks, not fixed-length bookmarks, it must return SQLSTATE HYC00 (Optional feature not implemented) if an ODBC 2.<legacyItalic>x</legacyItalic> application attempts to set SQL_USE_BOOKMARKS to SQL_UB_ON. </para>
      <para>For an ODBC 3<legacyItalic>.x</legacyItalic> driver, the Driver Manager no longer checks to see whether <legacyItalic>Option</legacyItalic> is in between SQL_STMT_OPT_MIN and SQL_STMT_OPT_MAX, or is greater than SQL_CONNECT_OPT_DRVR_START. The driver must check this.</para>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>