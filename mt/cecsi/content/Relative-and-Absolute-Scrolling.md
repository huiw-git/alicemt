---
title: Relative and Absolute Scrolling
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3d0ff48d-fef5-4c01-bb1d-a583e6269b66
translation.priority.ht: 
  - en-gb
---
# Relative and Absolute Scrolling
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Most of the scrolling options in <legacyBold>SQLFetchScroll</legacyBold> position the cursor relative to the current position or to an absolute position. <legacyBold>SQLFetchScroll</legacyBold> supports fetching the next, prior, first, and last rowsets, as well as relative fetching (fetch the rowset <legacyItalic>n</legacyItalic> rows from the start of the current rowset) and absolute fetching (fetch the rowset starting at row <legacyItalic>n</legacyItalic>). If <legacyItalic>n</legacyItalic> is negative in an absolute fetch, rows are counted from the end of the result set. Thus, an absolute fetch of row –1 means to fetch the rowset that starts with the last row in the result set.</para>
    <para>Dynamic cursors detect rows inserted into and deleted from the result set, so there is no easy way for dynamic cursors to retrieve the row at a particular number other than reading from the start of the result set, which is likely to be slow. Furthermore, absolute fetching is not very useful in dynamic cursors because row numbers change as rows are inserted and deleted; therefore, successively fetching the same row number can yield different rows.</para>
    <para>Applications that use <legacyBold>SQLFetchScroll</legacyBold> only for its block cursor capabilities, such as reports, are likely to pass through the result set a single time, using only the option to fetch the next rowset. Screen-based applications, on the other hand, can take advantage of all the capabilities of <legacyBold>SQLFetchScroll</legacyBold>. If the application sets the rowset size to the number of rows displayed on the screen and binds the screen buffers to the result set, it can translate scroll bar operations directly to calls to <legacyBold>SQLFetchScroll</legacyBold>.</para>
    <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
      <thead>
        <tr>
          <TD>
            <para>Scroll bar operation</para>
          </TD>
          <TD>
            <para>SQLFetchScroll scrolling option</para>
          </TD>
        </tr>
      </thead>
      <tbody>
        <tr>
          <TD>
            <para>Page up</para>
          </TD>
          <TD>
            <para>SQL_FETCH_PRIOR</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>Page down</para>
          </TD>
          <TD>
            <para>SQL_FETCH_NEXT</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>Line up</para>
          </TD>
          <TD>
            <para>SQL_FETCH_RELATIVE with <legacyItalic>FetchOffset</legacyItalic> equal to –1</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>Line down</para>
          </TD>
          <TD>
            <para>SQL_FETCH_RELATIVE with <legacyItalic>FetchOffset</legacyItalic> equal to 1</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>Scroll box at top</para>
          </TD>
          <TD>
            <para>SQL_FETCH_FIRST</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>Scroll box at bottom</para>
          </TD>
          <TD>
            <para>SQL_FETCH_LAST</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>Random scroll box position</para>
          </TD>
          <TD>
            <para>SQL_FETCH_ABSOLUTE</para>
          </TD>
        </tr>
      </tbody>
    </table>
    <para>Such applications also need to position the scroll box after a scrolling operation, which requires the current row number and the number of rows. For the current row number, applications can either keep track of the current row number or call <legacyBold>SQLGetStmtAttr</legacyBold> with the SQL_ATTR_ROW_NUMBER attribute to retrieve it.</para>
    <para>The number of rows in the cursor, which is the size of the result set, is available as the SQL_DIAG_CURSOR_ROW_COUNT field of the diagnostic header. The value in this field is defined only after <legacyBold>SQLExecute</legacyBold>, <legacyBold>SQLExecDirect</legacyBold>, or <legacyBold>SQLMoreResult</legacyBold> has been called. This count can be either an approximate count or an exact count, depending on the capabilities of the driver. The driver's support can be determined by calling <legacyBold>SQLGetInfo</legacyBold> with the cursor attributes information types and checking whether the SQL_CA2_CRC_APPROXIMATE or SQL_CA2_CRC_EXACT bit is returned for the type of cursor.</para>
    <para>An exact row count is never supported for a dynamic cursor. For other types of cursors, the driver can support either exact or approximate row counts, but not both. If the driver supports neither exact nor approximate row counts for a specific cursor type, the SQL_DIAG_CURSOR_ROW_COUNT field contains the number of rows that have been fetched so far. Regardless of what the driver supports, <legacyBold>SQLFetchScroll</legacyBold> with an <legacyItalic>Operation</legacyItalic> of SQL_FETCH_LAST will cause the SQL_DIAG_CURSOR_ROW_COUNT field to contain the exact row count.</para>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>