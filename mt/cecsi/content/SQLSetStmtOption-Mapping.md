---
title: SQLSetStmtOption Mapping
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6a9921aa-8a53-4668-9b13-87164062f1e5
translation.priority.ht: 
  - en-gb
---
# SQLSetStmtOption Mapping
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>When an application calls <legacyBold>SQLSetStmtOption</legacyBold> through an ODBC 3<legacyItalic>.x</legacyItalic> driver, the call to</para>
  </introduction>
  <section>
    <content>
      <code>SQLSetStmtOption(StatementHandle, fOption, vParam)</code>
      <para>will result as follows:

</para>
      <list class="bullet">
        <listItem>
          <para>If <legacyItalic>fOption</legacyItalic> indicates an ODBC-defined statement attribute that is a string, the Driver Manager calls
</para>
          <code>SQLSetStmtAttr(StatementHandle, fOption, ValuePtr, SQL_NTS)</code>
        </listItem>
        <listItem>
          <para>If <legacyItalic>fOption</legacyItalic> indicates an ODBC-defined statement attribute that returns a 32-bit integer value, the Driver Manager calls
</para>
          <code>SQLSetStmtAttr(StatementHandle, fOption, ValuePtr, 0)</code>
        </listItem>
        <listItem>
          <para>If <legacyItalic>fOption</legacyItalic> indicates a driver-defined statement attribute, the Driver Manager calls
</para>
          <code>SQLSetStmtAttr(StatementHandle, fOption, ValuePtr, BufferLength)</code>
        </listItem>
      </list>
      <para>In the preceding three cases, the <legacyBold>StatementHandle</legacyBold> argument is set to the value in <legacyItalic>hstmt</legacyItalic>, the <legacyItalic>Attribute</legacyItalic> argument is set to the value in <legacyItalic>fOption</legacyItalic>, and the <legacyItalic>ValuePtr</legacyItalic> argument is set to the value as <legacyItalic>vParam</legacyItalic>.</para>
      <para>Because the Driver Manager does not know whether the driver-defined statement attribute needs a string or 32-bit integer value, it has to pass in a valid value for the <legacyItalic>StringLength</legacyItalic> argument of <legacyBold>SQLSetStmtAttr</legacyBold>. If the driver has defined special semantics for driver-defined statement attributes and needs to be called using <legacyBold>SQLSetStmtOption</legacyBold>, it must support <legacyBold>SQLSetStmtOption</legacyBold>.</para>
      <para>If an application calls <legacyBold>SQLSetStmtOption</legacyBold> to set a driver-specific statement option in an ODBC 3<legacyItalic>.x</legacyItalic> driver and the option was defined in an ODBC 2.<legacyItalic>x</legacyItalic> version of the driver, a new manifest constant should be defined for the option in the ODBC 3<legacyItalic>.x</legacyItalic> driver. If the old manifest constant is used in the call to <legacyBold>SQLSetStmtOption</legacyBold>, the Driver Manager will call <legacyBold>SQLSetStmtAttr</legacyBold> with the <legacyItalic>StringLength</legacyItalic> argument set to 0.</para>
      <para>When an application calls <legacyBold>SQLSetStmtAttr</legacyBold> to set SQL_ATTR_USE_BOOKMARKS to SQL_UB_ON in an ODBC 3<legacyItalic>.x</legacyItalic> driver, the SQL_ATTR_USE_BOOKMARKS statement attribute is set to SQL_UB_FIXED. SQL_UB_ON is the same constant as SQL_UB_FIXED. The Driver Manager passes SQL_UB_FIXED through to the driver. SQL_UB_FIXED has been deprecated in ODBC 3<legacyItalic>.x</legacyItalic>, but an ODBC 3<legacyItalic>.x</legacyItalic> driver must implement it to work with ODBC 2.<legacyItalic>x</legacyItalic> applications that use fixed-length bookmarks.</para>
      <para>For an ODBC 3<legacyItalic>.x</legacyItalic> driver, the Driver Manager no longer checks to see if <legacyItalic>Option</legacyItalic> is in between SQL_STMT_OPT_MIN and SQL_STMT_OPT_MAX, or is greater than SQL_CONNECT_OPT_DRVR_START.</para>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>