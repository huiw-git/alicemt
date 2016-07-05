---
title: SQLGetInfo Support
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 57326f57-daba-46b6-b0be-6c97213b9ef1
translation.priority.ht: 
  - en-gb
---
# SQLGetInfo Support
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>When an ODBC 2.<legacyItalic>x</legacyItalic> application calls <legacyBold>SQLGetInfo</legacyBold> to an ODBC 3<legacyItalic>.x</legacyItalic> driver, the <legacyItalic>InfoType</legacyItalic> arguments in the following table must be supported.</para>
    <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
      <thead>
        <tr>
          <TD>
            <para>                 <legacyItalic>InfoType</legacyItalic>               </para>
          </TD>
          <TD>
            <para>Returns</para>
          </TD>
        </tr>
      </thead>
      <tbody>
        <tr>
          <TD>
            <para>SQL_ALTER_TABLE (ODBC 2.0)</para>
            <alert class="note">
              <para>This information type is not deprecated; the bitmasks in the column to the right are deprecated.</para>
            </alert>
          </TD>
          <TD>
            <para>An SQLINTEGER bitmask enumerating the clauses in the <legacyBold>ALTER TABLE</legacyBold> statement supported by the data source.</para>
            <para>The following bitmasks are used to determine which clauses are supported:</para>
            <para>SQL_AT_DROP_COLUMN = The ability to drop columns is supported. Whether this results in cascade or restrict behavior is driver-defined. (ODBC 2.0)</para>
            <para>SQL_AT_ADD_COLUMN = The ability to add multiple columns in a single ALTER TABLE statement is supported. This bit does not combine with other SQL_AT_ADD_COLUMN_XXX bits or SQL_AT_CONSTRAINT_XXX bits. (ODBC 2.0) </para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_FETCH_DIRECTION (ODBC 1.0)</para>
            <para>The information type was introduced in ODBC 1.0; each bitmask is labeled with the version in which it was introduced.</para>
          </TD>
          <TD>
            <para>An SQLINTEGER bitmask enumerating the supported fetch direction options. </para>
            <para>The following bitmasks are used in conjunction with the flag to determine which options are supported:</para>
            <para>SQL_FD_FETCH_NEXT          (ODBC 1.0) SQL_FD_FETCH_FIRST         (ODBC 1.0) SQL_FD_FETCH_LAST          (ODBC 1.0) SQL_FD_FETCH_PRIOR         (ODBC 1.0) SQL_FD_FETCH_ABSOLUTE   (ODBC 1.0) SQL_FD_FETCH_RELATIVE    (ODBC 1.0) SQL_FD_FETCH_BOOKMARK (ODBC 2.0)</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_LOCK_TYPES (ODBC 2.0)</para>
          </TD>
          <TD>
            <para>An SQLINTEGER bitmask enumerating the supported lock types for the <legacyItalic>fLock</legacyItalic> argument in <legacyBold>SQLSetPos</legacyBold>.</para>
            <para>The following bitmasks are used in conjunction with the flag to determine which lock types are supported:</para>
            <para>SQL_LCK_NO_CHANGE SQL_LCK_EXCLUSIVE SQL_LCK_UNLOCK</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_ODBC_API_CONFORMANCE (ODBC 1.0)</para>
          </TD>
          <TD>
            <para>An SQLSMALLINT value indicating the level of ODBC conformance.</para>
            <para>SQL_OAC_NONE = None</para>
            <para>SQL_OAC_LEVEL1 = Level 1 supported</para>
            <para>SQL_OAC_LEVEL2 = Level 2 supported</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_ODBC_SQL_CONFORMANCE (ODBC 1.0)</para>
          </TD>
          <TD>
            <para>An SQLSMALLINT value indicating SQL grammar supported by the driver. See <legacyLink xlink:href="0ee36f09-59e7-4b94-88ca-7ebc0952a3be">Appendix C: SQL Grammar</legacyLink> for a definition of SQL conformance levels.</para>
            <para>SQL_OSC_MINIMUM = Minimum grammar supported</para>
            <para>SQL_OSC_CORE = Core grammar supported</para>
            <para>SQL_OSC_EXTENDED = Extended grammar supported</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_POS_OPERATIONS (ODBC 2.0)</para>
          </TD>
          <TD>
            <para>An SQLINTEGER bitmask enumerating the supported operations in <legacyBold>SQLSetPos</legacyBold>.</para>
            <para>The following bitmasks are used to in conjunction with the flag to determine which options are supported:</para>
            <para>SQL_POS_POSITION (ODBC 2.0) SQL_POS_REFRESH   (ODBC 2.0) SQL_POS_UPDATE     (ODBC 2.0) SQL_POS_DELETE     (ODBC 2.0) SQL_POS_ADD          (ODBC 2.0)</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_POSITIONED_STATEMENTS (ODBC 2.0)</para>
          </TD>
          <TD>
            <para>An SQLINTEGER bitmask enumerating the supported positioned SQL statements.</para>
            <para>The following bitmasks are used to determine which statements are supported:</para>
            <para>SQL_PS_POSITIONED_DELETE SQL_PS_POSITIONED_UPDATE SQL_PS_SELECT_FOR_UPDATE</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_SCROLL_CONCURRENCY (ODBC 1.0)</para>
          </TD>
          <TD>
            <para>An SQLINTEGER bitmask enumerating the concurrency control options supported for the cursor.</para>
            <para>The following bitmasks are used to determine which options are supported:</para>
            <para>SQL_SCCO_READ_ONLY = Cursor is read-only. No updates are allowed.</para>
            <para>SQL_SCCO_LOCK = Cursor uses the lowest level of locking sufficient to ensure that the row can be updated.</para>
            <para>SQL_SCCO_OPT_ROWVER = Cursor uses optimistic concurrency control, comparing row versions, such as SQLBase ROWID or Sybase TIMESTAMP.</para>
            <para>SQL_SCCO_OPT_VALUES = Cursor uses optimistic concurrency control, comparing values.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_STATIC_SENSITIVITY (ODBC 2.0)</para>
          </TD>
          <TD>
            <para>An SQLINTEGER bitmask enumerating whether changes made by an application to a static or keyset-driven cursor through <legacyBold>SQLSetPos</legacyBold> or positioned update or delete statements can be detected by that application.</para>
            <para>SQL_SS_ADDITIONS = Added rows are visible to the cursor; the cursor can scroll to these rows. Where these rows are added to the cursor is driver-dependent.</para>
            <para>SQL_SS_DELETIONS = Deleted rows are no longer available to the cursor and do not leave a "hole" in the result set; after the cursor scrolls from a deleted row, it cannot return to that row.</para>
            <para>SQL_SS_UPDATES = Updates to rows are visible to the cursor; if the cursor scrolls from and returns to an updated row, the data returned by the cursor is the updated data, not the original data. This option applies only to static cursors or updates on keyset-driven cursors that do not update the key. This option does not apply for a dynamic cursor or in the case in which a key is changed in a mixed cursor.</para>
            <para>Whether an application can detect changes made to the result set by other users, including other cursors in the same application, depends on the cursor type.</para>
          </TD>
        </tr>
      </tbody>
    </table>
    <para>An ODBC 3<legacyItalic>.x</legacyItalic> application working with an ODBC 3<legacyItalic>.x</legacyItalic> driver should not call <legacyBold>SQLGetInfo</legacyBold> with the <legacyItalic>InfoType</legacyItalic> arguments described in the preceding table but should use the ODBC 3<legacyItalic>.x</legacyItalic> <legacyItalic>InfoType</legacyItalic> arguments listed in the following paragraph. There is not a one-to-one correspondence between <legacyItalic>InfoType</legacyItalic> arguments used in ODBC 2.<legacyItalic>x</legacyItalic> and those used in ODBC 3<legacyItalic>.x</legacyItalic>. An ODBC 3<legacyItalic>.x</legacyItalic> application working with an ODBC 2.<legacyItalic>x</legacyItalic> driver, on the other hand, should use the <legacyItalic>InfoType</legacyItalic> arguments described previously.</para>
    <para>Some of the information types in the previous table are deprecated in favor of the cursor attributes information types. These deprecated information types are SQL_FETCH_DIRECTION, SQL_LOCK_TYPES, SQL_POS_OPERATIONS, SQL_POSITIONED_STATEMENTS, SQL_SCROLL_CONCURRENCY, and SQL_STATIC_SENSITIVITY. The new cursor attributes types are SQL_XXX_CURSOR_ATTRIBUTES1and SQL_XXX_CURSOR_ATTRIBUTES2, where XXX equals DYNAMIC, FORWARD_ONLY, KEYSET_DRIVEN, or STATIC. Each of the new types indicates the driver capabilities for a single cursor type. For more information about these options, see the <legacyLink xlink:href="49dceccc-d816-4ada-808c-4c6138dccb64">SQLGetInfo</legacyLink> function description.</para>
  </introduction>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>