---
title: Calling SQLSetPos
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 846354b8-966c-4c2c-b32f-b0c8e649cedd
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Calling SQLSetPos
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>In ODBC 2.<legacyItalic>x</legacyItalic>, the pointer to the row status array was an argument to <legacyBold>SQLExtendedFetch</legacyBold>. The row status array was later updated by a call to <legacyBold>SQLSetPos</legacyBold>. Some drivers have relied on the fact that this array does not change between <legacyBold>SQLExtendedFetch</legacyBold> and <legacyBold>SQLSetPos</legacyBold>. In ODBC 3.<legacyItalic>x</legacyItalic>, the pointer to the status array is a descriptor field and therefore the application can easily change it to point to a different array. This can be a problem when an ODBC 3.<legacyItalic>x</legacyItalic> application is working with an ODBC 2.<legacyItalic>x</legacyItalic> driver but is calling <legacyBold>SQLSetStmtAttr</legacyBold> to set the array status pointer and is calling <legacyBold>SQLFetchScroll</legacyBold> to fetch data. The Driver Manager maps it as a sequence of calls to <legacyBold>SQLExtendedFetch</legacyBold>. In the following code, an error would normally be raised when the Driver Manager maps the second <legacyBold>SQLSetStmtAttr</legacyBold> call when working with an ODBC 2<legacyItalic>.x</legacyItalic> driver:</para>
    <code>SQLSetStmtAttr(hstmt, SQL_ATTR_ROW_STATUS_PTR, rgfRowStatus, 0);
SQLFetchScroll(hstmt, fFetchType, iRow);
SQLSetStmtAttr(hstmt, SQL_ATTR_ROW_STATUS_PTR, rgfRowStat1, 0);
SQLSetPos(hstmt, iRow, fOption, fLock);</code>
    <para>The error would be raised if there were no way to change the row status pointer in ODBC 2.<legacyItalic>x </legacyItalic>between calls to <legacyBold>SQLExtendedFetch</legacyBold>. Instead, the Driver Manager performs the following steps when working with an ODBC 2<legacyItalic>.x</legacyItalic> driver:  </para>
    <list class="ordered">
      <listItem>
        <para>Initializes an internal Driver Manager flag <legacyItalic>fSetPosError</legacyItalic> to TRUE.</para>
      </listItem>
      <listItem>
        <para>When an application calls <legacyBold>SQLFetchScroll</legacyBold>, the Driver Manager sets <legacyItalic>fSetPosError</legacyItalic> to FALSE.</para>
      </listItem>
      <listItem>
        <para>When the application calls <legacyBold>SQLSetStmtAttr</legacyBold> to set SQL_ATTR_ROW_STATUS_PTR, the Driver Manager sets <legacyItalic>fSetPosError </legacyItalic>equal toTRUE.</para>
      </listItem>
      <listItem>
        <para>When the application calls <legacyBold>SQLSetPos</legacyBold>, with <legacyItalic>fSetPosError</legacyItalic> equal to TRUE, the Driver Manager raises SQL_ERROR with SQLSTATE HY011 (Attribute cannot be set now) to indicate that the application attempted to call <legacyBold>SQLSetPos</legacyBold> after changing the row status pointer but prior to calling <legacyBold>SQLFetchScroll</legacyBold>.</para>
      </listItem>
    </list>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>