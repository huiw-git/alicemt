---
title: "ODBC Cursor Library Error Codes"
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9713480e-8744-4f37-a630-20871590d4a1
caps.latest.revision: 6
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# ODBC Cursor Library Error Codes
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <alert class="important">
      <para>This feature will be removed in a future version of Microsoft Data Access Component. Avoid using this feature in new development work and plan to modify applications that currently use this feature. Instead, use driver and server cursors.</para>
    </alert>
    <para>The ODBC cursor library returns the following SQLSTATEs in addition to those listed in <legacyLink xlink:href="b7a49774-f458-44ce-9a04-a0457501405b">ODBC API Reference</legacyLink>.</para>
  </introduction>
  <section>
    <content>
      <alert class="note">
        <para>The cursor library does not order status records; the Driver Manager and ODBC 3.<legacyItalic>x</legacyItalic> drivers are responsible for ordering status records.</para>
      </alert>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>SQLSTATE</para>
            </TD>
            <TD>
              <para>Description</para>
            </TD>
            <TD>
              <para>Can be returned from</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>01000</para>
            </TD>
            <TD>
              <para>Cursor is not updatable.</para>
            </TD>
            <TD>
              <para>
                <legacyBold>SQLFetch</legacyBold>
              </para>
              <para>
                <legacyBold>SQLFetchScroll</legacyBold> </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>01000</para>
            </TD>
            <TD>
              <para>Cursor library not used. Load failed.</para>
            </TD>
            <TD>
              <para>
                <legacyBold>SQLBrowseConnect</legacyBold>
              </para>
              <para>
                <legacyBold>SQLConnect</legacyBold>
              </para>
              <para>
                <legacyBold>SQLDriverConnect</legacyBold>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>01000</para>
            </TD>
            <TD>
              <para>Cursor library not used. Insufficient driver support.</para>
            </TD>
            <TD>
              <para>
                <legacyBold>SQLBrowseConnect</legacyBold>
              </para>
              <para>
                <legacyBold>SQLConnect</legacyBold>
              </para>
              <para>
                <legacyBold>SQLDriverConnect</legacyBold>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>01000</para>
            </TD>
            <TD>
              <para>Cursor library not used. Version mismatch with Driver Manager.</para>
            </TD>
            <TD>
              <para>
                <legacyBold>SQLBrowseConnect</legacyBold>
              </para>
              <para>
                <legacyBold>SQLConnect</legacyBold>
              </para>
              <para>
                <legacyBold>SQLDriverConnect</legacyBold>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>01000</para>
            </TD>
            <TD>
              <para>Driver returned SQL_SUCCESS_WITH_INFO. The warning message has been lost.</para>
            </TD>
            <TD>
              <para>
                <legacyBold>SQLFetch</legacyBold>
              </para>
              <para>
                <legacyBold>SQLFetchScroll</legacyBold>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>S1000</para>
            </TD>
            <TD>
              <para>General error: Unable to create file buffer.</para>
            </TD>
            <TD>
              <para>
                <legacyBold>SQLFetch</legacyBold>
              </para>
              <para>
                <legacyBold>SQLFetchScroll</legacyBold>
              </para>
              <para>
                <legacyBold>SQLGetData</legacyBold>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>S1000</para>
            </TD>
            <TD>
              <para>General error: Unable to read from file buffer.</para>
            </TD>
            <TD>
              <para>
                <legacyBold>SQLFetch</legacyBold>
              </para>
              <para>
                <legacyBold>SQLFetchScroll</legacyBold>
              </para>
              <para>
                <legacyBold>SQLGetData</legacyBold>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>S1000</para>
            </TD>
            <TD>
              <para>General error: Unable to write to file buffer.</para>
            </TD>
            <TD>
              <para>
                <legacyBold>SQLFetch</legacyBold>
              </para>
              <para>
                <legacyBold>SQLFetchScroll</legacyBold>
              </para>
              <para>
                <legacyBold>SQLGetData</legacyBold>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>S1000</para>
            </TD>
            <TD>
              <para>General error: Unable to close or remove file buffer.</para>
            </TD>
            <TD>
              <para>
                <legacyBold>SQLFreeHandle</legacyBold>
              </para>
              <para>
                <legacyBold>SQLFreeStmt</legacyBold>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SL001</para>
            </TD>
            <TD>
              <para>Positioned request cannot be performed because no searchable columns were bound.</para>
            </TD>
            <TD>
              <para>
                <legacyBold>SQLExecDirect</legacyBold>
              </para>
              <para>
                <legacyBold>SQLGetData</legacyBold>
              </para>
              <para>
                <legacyBold>SQLPrepare</legacyBold>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SL002</para>
            </TD>
            <TD>
              <para>Positioned request could not be performed because result set was created by a join condition.</para>
            </TD>
            <TD>
              <para>
                <legacyBold>SQLExecute</legacyBold>
              </para>
              <para>
                <legacyBold>SQLExecDirect</legacyBold>
              </para>
              <para>
                <legacyBold>SQLGetData</legacyBold>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SL003</para>
            </TD>
            <TD>
              <para>Bound buffer exceeds maximum segment size.</para>
            </TD>
            <TD>
              <para>
                <legacyBold>SQLFetch</legacyBold>
              </para>
              <para>
                <legacyBold>SQLFetchScroll</legacyBold>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SL004</para>
            </TD>
            <TD>
              <para>Result set was not generated by a <legacyBold>SELECT</legacyBold> statement.</para>
            </TD>
            <TD>
              <para>
                <legacyBold>SQLGetData</legacyBold>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SL005</para>
            </TD>
            <TD>
              <para>               <legacyBold>SELECT</legacyBold> statement contains a GROUP BY clause.</para>
            </TD>
            <TD>
              <para>
                <legacyBold>SQLGetData</legacyBold>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SL006</para>
            </TD>
            <TD>
              <para>Parameter arrays are not supported with positioned requests.</para>
            </TD>
            <TD>
              <para>
                <legacyBold>SQLPrepare</legacyBold>
              </para>
              <para>
                <legacyBold>SQLExecDirect</legacyBold> </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SL008</para>
            </TD>
            <TD>
              <para>               <legacyBold>SQLGetData</legacyBold> is not allowed on a forward-only (nonbuffered) cursor.</para>
            </TD>
            <TD>
              <para>
                <legacyBold>SQLGetData</legacyBold> </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SL009</para>
            </TD>
            <TD>
              <para>No columns were bound prior to calling <legacyBold>SQLFetch</legacyBold> or <legacyBold>SQLFetchScroll</legacyBold>.</para>
            </TD>
            <TD>
              <para>
                <legacyBold>SQLFetch</legacyBold>
              </para>
              <para>
                <legacyBold>SQLFetchScroll</legacyBold>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SL010</para>
            </TD>
            <TD>
              <para>               <legacyBold>SQLBindCol</legacyBold> returned SQL_ERROR during an attempt to bind to an internal buffer.</para>
            </TD>
            <TD>
              <para>
                <legacyBold>SQLFetch</legacyBold>
              </para>
              <para>
                <legacyBold>SQLFetchScroll</legacyBold>
              </para>
              <para>
                <legacyBold>SQLGetData</legacyBold>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SL011</para>
            </TD>
            <TD>
              <para>Statement option is valid only after calling <legacyBold>SQLFetch</legacyBold> or <legacyBold>SQLFetchScroll</legacyBold>.</para>
            </TD>
            <TD>
              <para>
                <legacyBold>SQLGetStmtAttr</legacyBold>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SL012</para>
            </TD>
            <TD>
              <para>Statement bindings may not be changed while a cursor is open.</para>
            </TD>
            <TD>
              <para>
                <legacyBold>SQLBindCol</legacyBold>
              </para>
              <para>
                <legacyBold>SQLFreeHandle</legacyBold>
              </para>
              <para>
                <legacyBold>SQLFreeStmt</legacyBold>
              </para>
              <para>
                <legacyBold>SQLSetStmtAttr</legacyBold>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SL014</para>
            </TD>
            <TD>
              <para>A positioned request was issued and not all column count fields were buffered.</para>
            </TD>
            <TD>
              <para>
                <legacyBold>SQLExecDirect</legacyBold>
              </para>
              <para>
                <legacyBold>SQLExecute</legacyBold>
              </para>
              <para>
                <legacyBold>SQLPrepare</legacyBold>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SL015</para>
            </TD>
            <TD>
              <para>               <legacyBold>SQLFetch</legacyBold> and <legacyBold>SQLFetchScroll</legacyBold> cannot be mixed.</para>
            </TD>
            <TD>
              <para>
                <legacyBold>SQLExtendedFetch</legacyBold>
              </para>
              <para>
                <legacyBold>SQLFetch</legacyBold>
              </para>
              <para>
                <legacyBold>SQLFetchScroll</legacyBold>
              </para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>