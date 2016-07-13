---
title: Writing ODBC 3.x Applications
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 19c54fc5-9dd6-49b6-8c9f-a38961b40a65
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Writing ODBC 3.x Applications
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>When an ODBC 2.<legacyItalic>x </legacyItalic>application is upgraded to ODBC 3.<legacyItalic>x</legacyItalic>, it should be written such that it works with both ODBC 2.<legacyItalic>x </legacyItalic>and 3.<legacyItalic>x</legacyItalic> drivers. The application should incorporate conditional code to take full advantage of the ODBC 3.<legacyItalic>x</legacyItalic> features.</para>
    <para>The SQL_ATTR_ODBC_VERSION environment attribute should be set to SQL_OV_ODBC2. This will ensure that the driver behaves like an ODBC 2<legacyItalic>.x </legacyItalic>driver with respect to the changes described in the section <legacyLink xlink:href="a17ae701-6ab6-4eaf-9e46-d3b9cd0a3a67">Behavioral Changes</legacyLink>.</para>
    <para>If the application will use any of the features described in the section <legacyLink xlink:href="a8fcdd00-6cb3-4871-9489-6018b3d0d65f">New Features</legacyLink>, conditional code should be used to determine whether the driver is an ODBC 3.<legacyItalic>x</legacyItalic> or ODBC 2<legacyItalic>.x</legacyItalic> driver. The application uses <legacyBold>SQLGetDiagField</legacyBold> and <legacyBold>SQLGetDiagRec</legacyBold> to obtain ODBC 3.<legacyItalic>x</legacyItalic> SQLSTATEs while doing error processing on these conditional code fragments. The following points about the new functionality should be considered:  </para>
    <list class="bullet">
      <listItem>
        <para>An application affected by the change in rowset size behavior should be careful not to call <legacyBold>SQLFetch</legacyBold> when the array size is greater than 1. These applications should replace calls to <legacyBold>SQLExtendedFetch</legacyBold> with calls to <legacyBold>SQLSetStmtAttr</legacyBold> to set the SQL_ATTR_ARRAY_STATUS_PTR statement attribute and to <legacyBold>SQLFetchScroll</legacyBold>, so that they have common code that works with both ODBC 3.<legacyItalic>x</legacyItalic> and ODBC 2.<legacyItalic>x </legacyItalic>drivers. Because <legacyBold>SQLSetStmtAttr</legacyBold> with SQL_ATTR_ROW_ARRAY_SIZE will be mapped to <legacyBold>SQLSetStmtAttr</legacyBold> with SQL_ROWSET_SIZE for ODBC 2.<legacyItalic>x </legacyItalic>drivers, applications can just set SQL_ATTR_ROW_ARRAY_SIZE for their multirow fetch operations.</para>
      </listItem>
      <listItem>
        <para>Most applications that are upgrading are not actually affected by changes in SQLSTATE codes. For those applications that are affected, they can do a mechanical search and replace in most cases using the error conversion table in the "SQLSTATE Mapping" section to convert ODBC 3.<legacyItalic>x</legacyItalic> error codes to ODBC 2<legacyItalic>.x</legacyItalic> codes. Since the ODBC 3<legacyItalic>.x</legacyItalic> Driver Manager will perform mapping from ODBC 2.<legacyItalic>x </legacyItalic>SQLSTATEs to ODBC 3.<legacyItalic>x</legacyItalic> SQLSTATEs, these application writers need only check for the ODBC 3.<legacyItalic>x</legacyItalic> SQLSTATEs and not worry about including ODBC 2.<legacyItalic>x </legacyItalic>SQLSTATEs in conditional code.</para>
      </listItem>
      <listItem>
        <para>If an application makes great use of date, time, and timestamp data types, the application can declare itself to be an ODBC 2.<legacyItalic>x </legacyItalic>application and use its existing code instead of using conditioning code.</para>
      </listItem>
    </list>
    <para>The upgrade should also include the following steps:  </para>
    <list class="bullet">
      <listItem>
        <para>Call <legacyBold>SQLSetEnvAttr</legacyBold> before allocating a connection to set the SQL_ATTR_ODBC_VERSION environment attribute to SQL_OV_ODBC2.</para>
      </listItem>
      <listItem>
        <para>Replace all calls to <legacyBold>SQLAllocEnv</legacyBold>, <legacyBold>SQLAllocConnect</legacyBold>, or <legacyBold>SQLAllocStmt</legacyBold> with calls to <legacyBold>SQLAllocHandle</legacyBold> with the appropriate <legacyItalic>HandleType</legacyItalic> argument of SQL_HANDLE_ENV, SQL_HANDLE_DBC, or SQL_HANDLE_STMT.</para>
      </listItem>
      <listItem>
        <para>Replace all calls to <legacyBold>SQLFreeEnv</legacyBold> or <legacyBold>SQLFreeConnect</legacyBold> with calls to <legacyBold>SQLFreeHandle</legacyBold> with the appropriate <legacyItalic>HandleType</legacyItalic> argument of SQL_HANDLE_DBC or SQL_HANDLE_STMT.</para>
      </listItem>
      <listItem>
        <para>Replace all calls to <legacyBold>SQLSetConnectOption</legacyBold> with calls to <legacyBold>SQLSetConnectAttr</legacyBold>. If setting an attribute whose value is a string, set the <legacyItalic>StringLength</legacyItalic> argument appropriately. Change <legacyItalic>Attribute</legacyItalic> argument from SQL_XXXX to SQL_ATTR_XXXX.</para>
      </listItem>
      <listItem>
        <para>Replace all calls to <legacyBold>SQLGetConnectOption</legacyBold> with calls to <legacyBold>SQLGetConnectAttr</legacyBold>. If getting a string or binary attribute, set <legacyItalic>BufferLength</legacyItalic> to the appropriate value and pass in a <legacyItalic>StringLength</legacyItalic> argument. Change <legacyItalic>Attribute</legacyItalic> argument from SQL_XXXX to SQL_ATTR_XXXX.</para>
      </listItem>
      <listItem>
        <para>Replace all calls to <legacyBold>SQLSetStmtOption</legacyBold> with calls to <legacyBold>SQLSetStmtAttr</legacyBold>. If setting an attribute whose value is a string, set the <legacyItalic>StringLength</legacyItalic> argument appropriately. Change <legacyItalic>Attribute</legacyItalic> argument from SQL_XXXX to SQL_ATTR_XXXX.</para>
      </listItem>
      <listItem>
        <para>Replace all calls to <legacyBold>SQLGetStmtOption</legacyBold> with calls to <legacyBold>SQLGetStmtAttr</legacyBold>. If getting a string or binary attribute, set <legacyItalic>BufferLength</legacyItalic> to the appropriate value and pass in a <legacyItalic>StringLength</legacyItalic> argument. Change <legacyItalic>Attribute</legacyItalic> argument from SQL_XXXX to SQL_ATTR_XXXX.</para>
      </listItem>
      <listItem>
        <para>Replace all calls to <legacyBold>SQLTransact</legacyBold> with calls to <legacyBold>SQLEndTran</legacyBold>. If the rightmost valid handle in the <legacyBold>SQLTransact</legacyBold> call is an environment handle, a <legacyItalic>HandleType</legacyItalic> argument of SQL_HANDLE_ENV should be used in the <legacyBold>SQLEndTran</legacyBold> call with the appropriate <legacyItalic>Handle</legacyItalic> argument. If the rightmost valid handle in your <legacyBold>SQLTransact</legacyBold> call is a connection handle, a <legacyItalic>HandleType</legacyItalic> argument of SQL_HANDLE_DBC should be used in the <legacyBold>SQLEndTran</legacyBold> call with the appropriate <legacyItalic>Handle</legacyItalic> argument.</para>
      </listItem>
      <listItem>
        <para>Replace all calls to <legacyBold>SQLColAttributes</legacyBold> with calls to <legacyBold>SQLColAttribute</legacyBold>. If the <legacyItalic>FieldIdentifier</legacyItalic> argument is either SQL_COLUMN_PRECISION, SQL_COLUMN_SCALE, or SQL_COLUMN_LENGTH, do not change anything other than the name of the function. If not, change <legacyItalic>FieldIdentifier</legacyItalic> from SQL_COLUMN_XXXX to SQL_DESC_XXXX. If <legacyItalic>FieldIdentifier</legacyItalic> is SQL_DESC_CONCISE_TYPE and the data type is a datetime data type, change to the corresponding ODBC 3<legacyItalic>.x</legacyItalic> data type.</para>
      </listItem>
      <listItem>
        <para>If using block cursors, scrollable cursors, or both, the application does the following: </para>
        <list class="bullet">
          <listItem>
            <para>Sets the rowset size, cursor type, and cursor concurrency using <legacyBold>SQLSetStmtAttr</legacyBold>.</para>
          </listItem>
          <listItem>
            <para>Calls <legacyBold>SQLSetStmtAttr</legacyBold> to set SQL_ATTR_ROW_STATUS_PTR to point to an array of status records.</para>
          </listItem>
          <listItem>
            <para>Calls <legacyBold>SQLSetStmtAttr</legacyBold> to set SQL_ATTR_ROWS_FETCHED_PTR to point to an SQLINTEGER.</para>
          </listItem>
          <listItem>
            <para>Performs the required bindings and executes the SQL statement.</para>
          </listItem>
          <listItem>
            <para>Calls <legacyBold>SQLFetchScroll</legacyBold> in a loop to fetch rows and move around in the result set.</para>
          </listItem>
          <listItem>
            <para>If it wants to fetch by bookmark, the application calls <legacyBold>SQLSetStmtAttr</legacyBold> to set SQL_ATTR_FETCH_BOOKMARK_PTR to a variable that will contain the bookmark for the row that it wants to fetch, and calls <legacyBold>SQLFetchScroll</legacyBold> with a <legacyItalic>FetchOrientation</legacyItalic> argument of SQL_FETCH_BOOKMARK.</para>
          </listItem>
        </list>
      </listItem>
      <listItem>
        <para>If using arrays of parameters, the application does the following: </para>
        <list class="bullet">
          <listItem>
            <para>Calls <legacyBold>SQLSetStmtAttr</legacyBold> to set the SQL_ATTR_PARAMSET_SIZE attribute to the size of the parameter array.</para>
          </listItem>
          <listItem>
            <para>Calls <legacyBold>SQLSetStmtAttr</legacyBold> to set SQL_ATTR_ROWS_PROCESSED_PTR to point to an internal UDWORD variable.</para>
          </listItem>
          <listItem>
            <para>Performs prepare, bind, and execute operations as appropriate.</para>
          </listItem>
          <listItem>
            <para>If execution halts for some reason (such as SQL_NEED_DATA), it can find the "current" row of parameters by inspecting the location pointed to by SQL_ATTR_ROWS_PROCESSED_PTR.</para>
          </listItem>
        </list>
      </listItem>
    </list>
    <para>This section contains the following topics.  </para>
    <list class="bullet">
      <listItem>
        <para>             <legacyLink xlink:href="f5e6d9da-76ef-42cb-b3f5-f640857df732">Mapping Replacement Functions for Backward Compatibility of Applications</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="ef448c39-a9ad-4f07-8ef3-65bd4cef672a">Calling SQLCloseCursor</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="3c4fb606-b81c-4f11-9820-f0a54e3bc401">Calling SQLGetDiagField</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="846354b8-966c-4c2c-b32f-b0c8e649cedd">Calling SQLSetPos</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="04d514b1-dc4d-4b84-bf35-60f4657ef1f6">Cursor Library Operations</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="9f112449-ca86-45ac-a865-e6174d67f91b">Mapping the Cursor Attributes1 Information Types</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="07a4144a-a548-4578-b2be-715c3cf73bf8">SQL_NO_DATA</legacyLink>           </para>
      </listItem>
    </list>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>