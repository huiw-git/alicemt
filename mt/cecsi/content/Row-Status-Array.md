---
title: "Row Status Array"
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4b69f189-2722-4314-8a02-f4ffecd6dabd
caps.latest.revision: 4
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Row Status Array
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>In addition to data, <legacyBold>SQLFetch</legacyBold> and <legacyBold>SQLFetchScroll</legacyBold> can return an array that gives the status of each row in the rowset. This array is specified through the SQL_ATTR_ROW_STATUS_PTR statement attribute. This array is allocated by the application and must have as many elements as are specified by the SQL_ATTR_ROW_ARRAY_SIZE statement attribute. The values in the array are set by <legacyBold>SQLBulkOperations</legacyBold>, <legacyBold>SQLFetch</legacyBold>, <legacyBold>SQLFetchScroll</legacyBold>, and <legacyBold>SQLSetPos. </legacyBold>The values describe the status of the row and whether that status has changed since it was last fetched.</para>
    <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
      <thead>
        <tr>
          <TD>
            <para>Row status array value</para>
          </TD>
          <TD>
            <para>Description</para>
          </TD>
        </tr>
      </thead>
      <tbody>
        <tr>
          <TD>
            <para>SQL_ROW_SUCCESS</para>
          </TD>
          <TD>
            <para>The row was successfully fetched and has not changed since it was last fetched.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_ROW_SUCCESS_WITH_INFO</para>
          </TD>
          <TD>
            <para>The row was successfully fetched and has not changed since it was last fetched. However, a warning was returned about the row.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_ROW_ERROR</para>
          </TD>
          <TD>
            <para>An error occurred while fetching the row.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_ROW_UPDATED</para>
          </TD>
          <TD>
            <para>The row was successfully fetched and has been updated since it was last fetched. If the row is fetched again or refreshed by <legacyBold>SQLSetPos</legacyBold>, its status is changed to the new status.</para>
            <para>Some drivers cannot detect changes to data and therefore cannot return this value. To determine whether a driver can detect updates to refetched rows, an application calls <legacyBold>SQLGetInfo</legacyBold> with the SQL_ROW_UPDATES option.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_ROW_DELETED</para>
          </TD>
          <TD>
            <para>The row has been deleted since it was last fetched.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_ROW_ADDED</para>
          </TD>
          <TD>
            <para>The row was inserted by <legacyBold>SQLBulkOperations</legacyBold>. If the row is fetched again or is refreshed by <legacyBold>SQLSetPos</legacyBold>, its status is SQL_ROW_SUCCESS.</para>
            <para>This value is not set by <legacyBold>SQLFetch</legacyBold> or <legacyBold>SQLFetchScroll</legacyBold>.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_ROW_NOROW</para>
          </TD>
          <TD>
            <para>The rowset overlapped the end of the result set, and no row was returned that corresponded to this element of the row status array.</para>
          </TD>
        </tr>
      </tbody>
    </table>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>