---
title: Attribute Conformance
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 34fea100-10f9-46d5-bc50-3aa867b70f24
translation.priority.ht: 
  - en-gb
---
# Attribute Conformance
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The following table indicates the conformance level of each ODBC environment attribute, where this is well defined.</para>
    <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
      <thead>
        <tr>
          <TD>
            <para>Function</para>
          </TD>
          <TD>
            <para>Conformance level</para>
          </TD>
        </tr>
      </thead>
      <tbody>
        <tr>
          <TD>
            <para>SQL_ATTR_CONNECTION_POOLING</para>
          </TD>
          <TD>
            <para>--[1]</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_ATTR_CP_MATCH</para>
          </TD>
          <TD>
            <para>--[1]</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_ATTR_ODBC_VER</para>
          </TD>
          <TD>
            <para>Core</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_ATTR_OUTPUT_NTS</para>
          </TD>
          <TD>
            <para>--[1]</para>
          </TD>
        </tr>
      </tbody>
    </table>
    <para>[1]   This is an optional feature and as such is not part of the conformance levels.</para>
    <para>The following table indicates the conformance level of each ODBC connection attribute, where this is well defined.</para>
    <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
      <thead>
        <tr>
          <TD>
            <para>Function</para>
          </TD>
          <TD>
            <para>Conformance level</para>
          </TD>
        </tr>
      </thead>
      <tbody>
        <tr>
          <TD>
            <para>SQL_ATTR_ACCESS_MODE</para>
          </TD>
          <TD>
            <para>Core</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_ATTR_ASYNC_ENABLE</para>
          </TD>
          <TD>
            <para>Level 1/Level 2[1]</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_ATTR_AUTO_IPD</para>
          </TD>
          <TD>
            <para>Level 2</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_ATTR_AUTOCOMMIT</para>
          </TD>
          <TD>
            <para>Level 1</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_ATTR_CONNECTION_DEAD</para>
          </TD>
          <TD>
            <para>Level 1</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_ATTR_CONNECTION_TIMEOUT</para>
          </TD>
          <TD>
            <para>Level 2</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_ATTR_CURRENT_CATALOG</para>
          </TD>
          <TD>
            <para>Level 2</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_ATTR_LOGIN_TIMEOUT</para>
          </TD>
          <TD>
            <para>Level 2</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_ATTR_ODBC_CURSORS</para>
          </TD>
          <TD>
            <para>Core</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_ATTR_PACKET_SIZE</para>
          </TD>
          <TD>
            <para>Level 2</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_ATTR_QUIET_MODE</para>
          </TD>
          <TD>
            <para>Core</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_ATTR_TRACE</para>
          </TD>
          <TD>
            <para>Core</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_ATTR_TRACEFILE</para>
          </TD>
          <TD>
            <para>Core</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_ATTR_TRANSLATE_LIB</para>
          </TD>
          <TD>
            <para>Core</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_ATTR_TRANSLATE_OPTION</para>
          </TD>
          <TD>
            <para>Core</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_ATTR_TXN_ISOLATION</para>
          </TD>
          <TD>
            <para>Level 1/Level 2[2]</para>
          </TD>
        </tr>
      </tbody>
    </table>
    <para>[1]   Applications that support connection-level asynchrony (required for Level 1) must support setting this attribute to SQL_TRUE by calling <legacyBold>SQLSetConnectAttr</legacyBold>; the attribute need not be settable to a value other than its default value through <legacyBold>SQLSetStmtAttr</legacyBold>. Applications that support statement-level asynchrony (required for Level 2) must support setting this attribute to SQL_TRUE using either function.</para>
    <para>[2]   For Level 1 interface conformance, the driver must support one value in addition to the driver-defined default value (available by calling <legacyBold>SQLGetInfo</legacyBold> with the SQL_DEFAULT_TXN_ISOLATION option). For Level 2 interface conformance, the driver must also support SQL_TXN_SERIALIZABLE.</para>
    <para>The following table indicates the conformance level of each ODBC statement attribute, where this is well defined.</para>
    <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
      <thead>
        <tr>
          <TD>
            <para>Function</para>
          </TD>
          <TD>
            <para>Conformance level</para>
          </TD>
        </tr>
      </thead>
      <tbody>
        <tr>
          <TD>
            <para>SQL_ATTR_APP_PARAM_DESC</para>
          </TD>
          <TD>
            <para>Core</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_ATTR_APP_ROW_DESC</para>
          </TD>
          <TD>
            <para>Core</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_ATTR_ASYNC_ENABLE</para>
          </TD>
          <TD>
            <para>Level 1/Level 2[1]</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_ATTR_CONCURRENCY</para>
          </TD>
          <TD>
            <para>Level 1/Level 2[2]</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_ATTR_CURSOR_SCROLLABLE</para>
          </TD>
          <TD>
            <para>Level 1</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_ATTR_CURSOR_SENSITIVITY</para>
          </TD>
          <TD>
            <para>Level 2</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_ATTR_CURSOR_TYPE</para>
          </TD>
          <TD>
            <para>Core/Level 2[3]</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_ATTR_ENABLE_AUTO_IPD</para>
          </TD>
          <TD>
            <para>Level 2</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_ATTR_FETCH_BOOKMARK_PTR</para>
          </TD>
          <TD>
            <para>Level 2</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_ATTR_IMP_PARAM_DESC</para>
          </TD>
          <TD>
            <para>Core</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_ATTR_IMP_ROW_DESC</para>
          </TD>
          <TD>
            <para>Core</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_ATTR_KEYSET_SIZE</para>
          </TD>
          <TD>
            <para>Level 2</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_ATTR_MAX_LENGTH</para>
          </TD>
          <TD>
            <para>Level 1</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_ATTR_MAX_ROWS</para>
          </TD>
          <TD>
            <para>Level 1</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_ATTR_METADATA_ID</para>
          </TD>
          <TD>
            <para>Core</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_ATTR_NOSCAN</para>
          </TD>
          <TD>
            <para>Core</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_ATTR_PARAM_BIND_OFFSET_PTR</para>
          </TD>
          <TD>
            <para>Core</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_ATTR_PARAM_BIND_TYPE</para>
          </TD>
          <TD>
            <para>Core</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_ATTR_PARAM_OPERATION_PTR</para>
          </TD>
          <TD>
            <para>Core</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_ATTR_PARAM_STATUS_PTR</para>
          </TD>
          <TD>
            <para>Core</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_ATTR_PARAMS_PROCESSED_PTR</para>
          </TD>
          <TD>
            <para>Core</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_ATTR_PARAMSET_SIZE</para>
          </TD>
          <TD>
            <para>Core</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_ATTR_QUERY_TIMEOUT</para>
          </TD>
          <TD>
            <para>Level 2</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_ATTR_RETRIEVE_DATA</para>
          </TD>
          <TD>
            <para>Level 1</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_ATTR_ROW_ARRAY_SIZE</para>
          </TD>
          <TD>
            <para>Core</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_ATTR_ROW_BIND_OFFSET_PTR</para>
          </TD>
          <TD>
            <para>Core</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_ATTR_ROW_BIND_TYPE</para>
          </TD>
          <TD>
            <para>Core</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_ATTR_ROW_NUMBER</para>
          </TD>
          <TD>
            <para>Level 1</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_ATTR_ROW_OPERATION_PTR</para>
          </TD>
          <TD>
            <para>Level 1</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_ATTR_ROW_STATUS_PTR</para>
          </TD>
          <TD>
            <para>Core</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_ATTR_ROWS_FETCHED_PTR</para>
          </TD>
          <TD>
            <para>Core</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_ATTR_SIMULATE_CURSOR</para>
          </TD>
          <TD>
            <para>Level 2</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_ATTR_USE_BOOKMARKS</para>
          </TD>
          <TD>
            <para>Level 2</para>
          </TD>
        </tr>
      </tbody>
    </table>
    <para>[1]   Applications that support connection-level asynchrony (required for Level 1) must support setting this attribute to SQL_TRUE by calling <legacyBold>SQLSetConnectAttr</legacyBold>; the attribute need not be settable to a value other than its default value through <legacyBold>SQLSetStmtAttr</legacyBold>. Applications that support statement-level asynchrony (required for Level 2) must support setting this attribute to SQL_TRUE using either function.</para>
    <para>[2]   For Level 2 interface conformance, the driver must support SQL_CONCUR_READ_ONLY and at least one other value.</para>
    <para>[3]   For Level 1 interface conformance, the driver must support SQL_CURSOR_FORWARD_ONLY and at least one other value. For Level 2 interface conformance, the driver must support all values defined in this document.</para>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>