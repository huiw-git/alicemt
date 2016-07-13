---
title: SQLSetScrollOptions Mapping
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a0fa4510-8891-4a61-a867-b2555bc35f05
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# SQLSetScrollOptions Mapping
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>When an application calls <legacyBold>SQLSetScrollOptions</legacyBold> through an ODBC 3<legacyItalic>.x</legacyItalic> driver and the driver does not support <legacyBold>SQLSetScrollOptions</legacyBold>, the call to</para>
  </introduction>
  <section>
    <content>
      <code>SQLSetScrollOptions(StatementHandle, Concurrency, KeysetSize, RowsetSize)</code>
      <para>will result as follows:  </para>
      <list class="bullet">
        <listItem>
          <para>A call to </para>
          <code>SQLGetInfo(ConnectionHandle, InfoType, InfoValuePtr, BufferLength, StringLengthPtr)</code>
          <para>with the <legacyItalic>InfoType</legacyItalic> argument set to one of the values in the following table, depending on the value of the <legacyItalic>KeysetSize</legacyItalic> argument in <legacyBold>SQLSetScrollOptions</legacyBold>. </para>
          <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
            <thead>
              <tr>
                <TD>
                  <para>
                    <legacyItalic>KeysetSize argument</legacyItalic>                   </para>
                </TD>
                <TD>
                  <para>
                    <legacyItalic>InfoType argument</legacyItalic>                   </para>
                </TD>
              </tr>
            </thead>
            <tbody>
              <tr>
                <TD>
                  <para>SQL_SCROLL_FORWARD_ONLY</para>
                </TD>
                <TD>
                  <para>SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES2</para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>SQL_SCROLL_STATIC</para>
                </TD>
                <TD>
                  <para>SQL_STATIC_CURSOR_ATTRIBUTES2</para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>SQL_SCROLL_KEYSET_DRIVEN</para>
                </TD>
                <TD>
                  <para>SQL_KEYSET_CURSOR_ATTRIBUTES2</para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>SQL_SCROLL_DYNAMIC</para>
                </TD>
                <TD>
                  <para>SQL_DYNAMIC_CURSOR_ATTRIBUTES2</para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>A value greater than the <legacyItalic>RowsetSize</legacyItalic> argument</para>
                </TD>
                <TD>
                  <para>SQL_KEYSET_CURSOR_ATTRIBUTES2</para>
                </TD>
              </tr>
            </tbody>
          </table>
          <para>If the value of the <legacyItalic>KeysetSize</legacyItalic> argument is not listed in the preceding table, the call to <legacyBold>SQLSetScrollOptions</legacyBold> returns SQLSTATE S1107 (Row value out of range) and none of the following steps are performed.  </para>
          <para>The Driver Manager then verifies whether the appropriate bit is set in the <legacyItalic>*InfoValuePtr</legacyItalic> value returned by the call to <legacyBold>SQLGetInfo</legacyBold>, according to the value of the <legacyItalic>Concurrency</legacyItalic> argument in <legacyBold>SQLSetScrollOptions</legacyBold>. </para>
          <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
            <thead>
              <tr>
                <TD>
                  <para>
                    <legacyItalic>Concurrency</legacyItalic> argument</para>
                </TD>
                <TD>
                  <para>
                    <legacyItalic>InfoType</legacyItalic> setting</para>
                </TD>
              </tr>
            </thead>
            <tbody>
              <tr>
                <TD>
                  <para>SQL_CONCUR_READ_ONLY</para>
                </TD>
                <TD>
                  <para>SQL_CA2_READ_ONLY_CONCURRENCY</para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>SQL_CONCUR_LOCK</para>
                </TD>
                <TD>
                  <para>SQL_CA2_LOCK_CONCURRENCY</para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>SQL_CONCUR_ROWVER</para>
                </TD>
                <TD>
                  <para>SQL_CA2_ROWVER_CONCURRENCY</para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>SQL_CONCUR_VALUES</para>
                </TD>
                <TD>
                  <para>SQL_CA2_VALUES_CONCURRENCY</para>
                </TD>
              </tr>
            </tbody>
          </table>
          <para>If the <legacyItalic>Concurrency</legacyItalic> argument is not one of the values in the preceding table, the call to <legacyBold>SQLSetScrollOptions</legacyBold> returns SQLSTATE S1108 (Concurrency option out of range) and none of the following steps are performed. If the appropriate bit (as indicated in the preceding table) is not set in <legacyItalic>*InfoValuePtr</legacyItalic> to one of the values corresponding to the <legacyItalic>Concurrency</legacyItalic> argument, the call to <legacyBold>SQLSetScrollOptions</legacyBold> returns SQLSTATE S1C00 (Driver not capable) and none of the following steps are performed. </para>
        </listItem>
        <listItem>
          <para>A call to </para>
          <code>SQLSetStmtAttr(StatementHandle, SQL_ATTR_CURSOR_TYPE, ValuePtr, 0)</code>
          <para>with <legacyItalic>*ValuePtr</legacyItalic> set to one of the values in the following table, according to the value of the <legacyItalic>KeysetSize</legacyItalic> argument in <legacyBold>SQLSetScrollOptions</legacyBold>. </para>
          <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
            <thead>
              <tr>
                <TD>
                  <para>
                    <legacyItalic>KeysetSize</legacyItalic> argument</para>
                </TD>
                <TD>
                  <para>
                    <legacyItalic>*ValuePtr</legacyItalic>                   </para>
                </TD>
              </tr>
            </thead>
            <tbody>
              <tr>
                <TD>
                  <para>SQL_SCROLL_FORWARD_ONLY</para>
                </TD>
                <TD>
                  <para>SQL_CURSOR_FORWARD_ONLY</para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>SQL_SCROLL_STATIC</para>
                </TD>
                <TD>
                  <para>SQL_CURSOR_STATIC</para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>SQL_SCROLL_KEYSET_DRIVEN</para>
                </TD>
                <TD>
                  <para>SQL_CURSOR_KEYSET_DRIVEN</para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>SQL_SCROLL_DYNAMIC</para>
                </TD>
                <TD>
                  <para>SQL_CURSOR_DYNAMIC</para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>A value greater than the <legacyItalic>RowsetSize</legacyItalic> argument</para>
                </TD>
                <TD>
                  <para>SQL_CURSOR_KEYSET_DRIVEN</para>
                </TD>
              </tr>
            </tbody>
          </table>
        </listItem>
        <listItem>
          <para>A call to </para>
          <code>SQLSetStmtAttr(StatementHandle, SQL_ATTR_CONCURRENCY, ValuePtr, 0)</code>
          <para>with <legacyItalic>*ValuePtr</legacyItalic> set to the <legacyItalic>Concurrency</legacyItalic> argument in <legacyBold>SQLSetScrollOptions</legacyBold>. </para>
        </listItem>
        <listItem>
          <para>If the <legacyItalic>KeysetSize</legacyItalic> argument in the call to <legacyBold>SQLSetScrollOptions</legacyBold> is positive, a call to </para>
          <code>SQLSetStmtAttr(StatementHandle, SQL_ATTR_KEYSET_SIZE, ValuePtr, 0)</code>
          <para>with <legacyItalic>*ValuePtr</legacyItalic> set to the <legacyItalic>KeysetSize</legacyItalic> argument in <legacyBold>SQLSetScrollOptions</legacyBold>. </para>
        </listItem>
        <listItem>
          <para>A call to </para>
          <code>SQLSetStmtAttr(StatementHandle, SQL_ROWSET_SIZE, ValuePtr, 0)</code>
          <para>with <legacyItalic>*ValuePtr</legacyItalic> set to the <legacyItalic>RowsetSize</legacyItalic> argument in <legacyBold>SQLSetScrollOptions</legacyBold>.  </para>
          <alert class="note">
            <para>When the Driver Manager maps <legacyBold>SQLSetScrollOptions</legacyBold> for an application working with an ODBC 3<legacyItalic>.x</legacyItalic> driver that does not support <legacyBold>SQLSetScrollOptions</legacyBold>, the Driver Manager sets the SQL_ROWSET_SIZE statement option, not the SQL_ATTR_ROW_ARRAY_SIZE statement attribute, to the <legacyItalic>RowsetSize</legacyItalic> argument in <legacyBold>SQLSetScrollOption</legacyBold>. As a result, <legacyBold>SQLSetScrollOptions</legacyBold> cannot be used by an application when fetching multiple rows by a call to <legacyBold>SQLFetch</legacyBold> or <legacyBold>SQLFetchScroll</legacyBold>. It can be used only when fetching multiple rows by a call to <legacyBold>SQLExtendedFetch</legacyBold>.</para>
          </alert>
        </listItem>
      </list>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>