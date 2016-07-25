---
title: "SQLGetInfo (Cursor Library)"
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1b4d220d-2c07-4f56-987e-36813bb1a6ce
caps.latest.revision: 7
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# SQLGetInfo (Cursor Library)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <alert class="important">
      <para>This feature will be removed in a future version of Windows. Avoid using this feature in new development work and plan to modify applications that currently use this feature. Microsoft recommends using the driver's cursor functionality.</para>
    </alert>
    <para>This topic discusses the use of the <legacyBold>SQLGetInfo</legacyBold> function in the cursor library. For general information about <legacyBold>SQLGetInfo</legacyBold>, see <legacyLink xlink:href="49dceccc-d816-4ada-808c-4c6138dccb64">SQLGetInfo Function</legacyLink>.</para>
  </introduction>
  <section>
    <content>
      <para>The cursor library returns values for the following values of <legacyItalic>InfoType</legacyItalic> (| represents a bitwise OR); for all other values of <legacyItalic>InfoType</legacyItalic>, it calls <legacyBold>SQLGetInfo</legacyBold> in the driver.</para>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>
                <legacyItalic>InfoType</legacyItalic>
              </para>
            </TD>
            <TD>
              <para>Returned value</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>SQL_BOOKMARK_PERSISTENCE</para>
            </TD>
            <TD>
              <para>SQL_BP_SCROLL</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_DYNAMIC_CURSOR_ATTRIBUTES1</para>
            </TD>
            <TD>
              <para>0</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_DYNAMIC_CURSOR_ATTRIBUTES2</para>
            </TD>
            <TD>
              <para>0</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_FETCH_DIRECTION[1]</para>
            </TD>
            <TD>
              <para>SQL_FD_FETCH_ABSOLUTE | SQL_FD_FETCH_FIRST | SQL_FD_FETCH_LAST | SQL_FD_FETCH_NEXT | SQL_FD_FETCH_PRIOR | SQL_FD_FETCH_RELATIVE | SQL_FD_FETCH_BOOKMARK</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES1</para>
            </TD>
            <TD>
              <para>SQL_CA1_NEXT | SQL_CA1_ABSOLUTE | SQL_CA1_RELATIVE | SQL_CA1_LOCK_NO_CHANGE | SQL_CA1_POS_POSITION | SQL_CA1_POSITIONED_DELETE | SQL_CA1_POSITIONED_UPDATE | SQL_CA1_SELECT_FOR_UPDATE</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES2</para>
            </TD>
            <TD>
              <para>SQL_CA2_READ_ONLY_CONCUR | SQL_CA2_OPT_VALUES_CONCURRENCY | SQL_CA2_SENSITIVITY_UPDATES</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_GETDATA_EXTENSIONS</para>
            </TD>
            <TD>
              <para>SQL_GD_BLOCK | any values returned by the driver</para>
              <alert class="note">
                <para>When data is retrieved with <legacyBold>SQLFetchScroll</legacyBold>, <legacyBold>SQLGetData</legacyBold> supports the functionality specified with the SQL_GD_ANY_COLUMN and SQL_GD_BOUND bitmasks.</para>
              </alert>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_KEYSET_DRIVEN_CURSOR_ATTRIBUTES1</para>
            </TD>
            <TD>
              <para>0</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_KEYSET_DRIVEN_CURSOR_ATTRIBUTES2</para>
            </TD>
            <TD>
              <para>0</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_LOCK_TYPES[1]</para>
            </TD>
            <TD>
              <para>SQL_LCK_NO_CHANGE</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_STATIC_CURSOR_ATTRIBUTES1</para>
            </TD>
            <TD>
              <para>SQL_CA1_NEXT | SQL_CA1_ABSOLUTE | SQL_CA1_RELATIVE | SQL_CA1_BOOKMARK | SQL_CA1_LOCK_NO_CHANGE | SQL_CA1_POS_POSITION | SQL_CA1_POSITIONED_DELETE | SQL_CA1_POSITIONED_UPDATE | SQL_CA1_SELECT_FOR_UPDATE</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_STATIC_CURSOR_ATTRIBUTES2</para>
            </TD>
            <TD>
              <para>SQL_CA2_READ_ONLY_CONCUR | SQL_CA2_OPT_VALUES_ CONCURRENCY | SQL_CA2_SENSITIVITY_UPDATES</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_POS_OPERATIONS[1]</para>
            </TD>
            <TD>
              <para>SQL_POS_POSITION</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_POSITIONED_STATEMENTS[1]</para>
            </TD>
            <TD>
              <para>SQL_PS_POSITIONED_DELETE | SQL_PS_POSITIONED_UPDATE | SQL_PS_SELECT_FOR_UPDATE</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_ROW_UPDATES</para>
            </TD>
            <TD>
              <para>"Y"</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_SCROLL_CONCURRENCY[1]</para>
            </TD>
            <TD>
              <para>SQL_SCCO_READ_ONLY | SQL_SCCO_OPT_VALUES</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_SCROLL_OPTIONS</para>
            </TD>
            <TD>
              <para>SQL_SO_FORWARD_ONLY | SQL_SO_STATIC</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_STATIC_SENSITIVITY[1]</para>
            </TD>
            <TD>
              <para>SQL_SS_UPDATES</para>
            </TD>
          </tr>
        </tbody>
      </table>
      <para>[1]   Used only when the cursor library is used with an ODBC 2.x driver.</para>
      <alert class="important">
        <para>The cursor library implements the same cursor behavior when transactions are committed or rolled back as the data source. That is, committing or rolling back a transaction, either by calling <legacyBold>SQLEndTran</legacyBold> or by using the SQL_ATTR_AUTOCOMMIT connection attribute, can cause the data source to delete the access plans and close the cursors for all statements on a connection. For more information, see the SQL_CURSOR_COMMIT_BEHAVIOR and SQL_CURSOR_ROLLBACK_BEHAVIOR information types in <legacyLink xlink:href="49dceccc-d816-4ada-808c-4c6138dccb64">SQLGetInfo</legacyLink>.</para>
      </alert>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>