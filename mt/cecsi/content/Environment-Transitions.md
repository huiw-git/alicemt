---
title: Environment Transitions
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9d11b1ab-f4c8-48ca-9812-8c04303f939d
translation.priority.ht: 
  - en-gb
---
# Environment Transitions
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>ODBC environments have the following three states.</para>
    <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
      <thead>
        <tr>
          <TD>
            <para>State</para>
          </TD>
          <TD>
            <para>Description</para>
          </TD>
        </tr>
      </thead>
      <tbody>
        <tr>
          <TD>
            <para>E0</para>
          </TD>
          <TD>
            <para>Unallocated environment</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>E1</para>
          </TD>
          <TD>
            <para>Allocated environment, unallocated connection</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>E2</para>
          </TD>
          <TD>
            <para>Allocated environment, allocated connection</para>
          </TD>
        </tr>
      </tbody>
    </table>
    <para>The following tables show how each ODBC function affects the environment state.</para>
  </introduction>
  <section>
    <title>SQLAllocHandle</title>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>E0</para>
              <para>Unallocated</para>
            </TD>
            <TD>
              <para>E1</para>
              <para>Allocated</para>
            </TD>
            <TD>
              <para>E2</para>
              <para>Connection</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>E1[1]</para>
            </TD>
            <TD>
              <para>--[4]</para>
            </TD>
            <TD>
              <para>--[4]</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>(IH)[2]</para>
            </TD>
            <TD>
              <para>E2[5]
(HY010)[6]</para>
            </TD>
            <TD>
              <para>--[4]</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>(IH)[3]</para>
            </TD>
            <TD>
              <para>(IH)</para>
            </TD>
            <TD>
              <para>--[4]</para>
            </TD>
          </tr>
        </tbody>
      </table>
      <para>[1]   This row shows transitions when <legacyItalic>HandleType</legacyItalic> was SQL_HANDLE_ENV.</para>
      <para>[2]   This row shows transitions when <legacyItalic>HandleType</legacyItalic> was SQL_HANDLE_DBC.</para>
      <para>[3]   This row shows transitions when <legacyItalic>HandleType</legacyItalic> was SQL_HANDLE_STMT or SQL_HANDLE_DESC.</para>
      <para>[4]   Calling <legacyBold>SQLAllocHandle</legacyBold> with <legacyItalic>OutputHandlePtr</legacyItalic> pointing to a valid handle overwrites that handle. This might be an application programming error. </para>
      <para>[5]   The SQL_ATTR_ODBC_VERSION environment attribute had been set on the environment.</para>
      <para>[6]   The SQL_ATTR_ODBC_VERSION environment attribute had not been set on the environment.</para>
    </content>
  </section>
  <section>
    <title>SQLDataSources and SQLDrivers</title>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>E0</para>
              <para>Unallocated</para>
            </TD>
            <TD>
              <para>E1</para>
              <para>Allocated</para>
            </TD>
            <TD>
              <para>E2</para>
              <para>Connection</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>(IH)</para>
            </TD>
            <TD>
              <para>--[1]
(HY010)[2]</para>
            </TD>
            <TD>
              <para>--[1]
(HY010)[2]</para>
            </TD>
          </tr>
        </tbody>
      </table>
      <para>[1]   The SQL_ATTR_ODBC_VERSION environment attribute had been set on the environment.</para>
      <para>[2]   The SQL_ATTR_ODBC_VERSION environment attribute had not been set on the environment.</para>
    </content>
  </section>
  <section>
    <title>SQLEndTran</title>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>E0</para>
              <para>Unallocated</para>
            </TD>
            <TD>
              <para>E1</para>
              <para>Allocated</para>
            </TD>
            <TD>
              <para>E2</para>
              <para>Connection</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>(IH)[1]</para>
            </TD>
            <TD>
              <para>--[3]
(HY010)[4]</para>
            </TD>
            <TD>
              <para>--[3]
(HY010)[4]</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>(IH)[2]</para>
            </TD>
            <TD>
              <para>(IH)</para>
            </TD>
            <TD>
              <para>--</para>
            </TD>
          </tr>
        </tbody>
      </table>
      <para>[1]   This row shows transitions when <legacyItalic>HandleType</legacyItalic> was SQL_HANDLE_ENV.</para>
      <para>[2]   This row shows transitions when <legacyItalic>HandleType</legacyItalic> was SQL_HANDLE_DBC.</para>
      <para>[3]   The SQL_ATTR_ODBC_VERSION environment attribute had been set on the environment.</para>
      <para>[4]   The SQL_ATTR_ODBC_VERSION environment attribute had not been set on the environment.</para>
    </content>
  </section>
  <section>
    <title>SQLFreeHandle</title>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>E0</para>
              <para>Unallocated</para>
            </TD>
            <TD>
              <para>E1</para>
              <para>Allocated</para>
            </TD>
            <TD>
              <para>E2</para>
              <para>Connection</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>(IH)[1]</para>
            </TD>
            <TD>
              <para>E0</para>
            </TD>
            <TD>
              <para>(HY010)</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>(IH)[2]</para>
            </TD>
            <TD>
              <para>(IH)</para>
            </TD>
            <TD>
              <para>--[4]
E1[5]</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>(IH)[3]</para>
            </TD>
            <TD>
              <para>(IH)</para>
            </TD>
            <TD>
              <para>--</para>
            </TD>
          </tr>
        </tbody>
      </table>
      <para>[1]   This row shows transitions when <legacyItalic>HandleType</legacyItalic> was SQL_HANDLE_ENV.</para>
      <para>[2]   This row shows transitions when <legacyItalic>HandleType</legacyItalic> was SQL_HANDLE_DBC.</para>
      <para>[3]   This row shows transitions when <legacyItalic>HandleType</legacyItalic> was SQL_HANDLE_STMT or SQL_HANDLE_DESC.</para>
      <para>[4]   There were other allocated connection handles.</para>
      <para>[5]   The connection handle specified in <legacyItalic>Handle</legacyItalic> was the only allocated connection handle.</para>
    </content>
  </section>
  <section>
    <title>SQLGetDiagField and SQLGetDiagRec</title>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>E0</para>
              <para>Unallocated</para>
            </TD>
            <TD>
              <para>E1</para>
              <para>Allocated</para>
            </TD>
            <TD>
              <para>E2</para>
              <para>Connection</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>(IH)[1]</para>
            </TD>
            <TD>
              <para>--</para>
            </TD>
            <TD>
              <para>--</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>(IH)[2]</para>
            </TD>
            <TD>
              <para>(IH)</para>
            </TD>
            <TD>
              <para>--</para>
            </TD>
          </tr>
        </tbody>
      </table>
      <para>[1]   This row shows transitions when <legacyItalic>HandleType</legacyItalic> was SQL_HANDLE_ENV.</para>
      <para>[2]   This row shows transitions when <legacyItalic>HandleType</legacyItalic> was SQL_HANDLE_DBC, SQL_HANDLE_STMT, or SQL_HANDLE_DESC.</para>
    </content>
  </section>
  <section>
    <title>SQLGetEnvAttr</title>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>E0</para>
              <para>Unallocated</para>
            </TD>
            <TD>
              <para>E1</para>
              <para>Allocated</para>
            </TD>
            <TD>
              <para>E2</para>
              <para>Connection</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>(IH)</para>
            </TD>
            <TD>
              <para>--[1]
(HY010)[2]</para>
            </TD>
            <TD>
              <para>--</para>
            </TD>
          </tr>
        </tbody>
      </table>
      <para>[1]   The SQL_ATTR_ODBC_VERSION environment attribute had been set on the environment.</para>
      <para>[2]   The SQL_ATTR_ODBC_VERSION environment attribute had not been set on the environment.</para>
    </content>
  </section>
  <section>
    <title>SQLSetEnvAttr</title>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>E0</para>
              <para>Unallocated</para>
            </TD>
            <TD>
              <para>E1</para>
              <para>Allocated</para>
            </TD>
            <TD>
              <para>E2</para>
              <para>Connection</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>(IH)</para>
            </TD>
            <TD>
              <para>--[1]
(HY010)[2]</para>
            </TD>
            <TD>
              <para>(HY011)</para>
            </TD>
          </tr>
        </tbody>
      </table>
      <para>[1]   The SQL_ATTR_ODBC_VERSION environment attribute had been set on the environment.</para>
      <para>[2]   The <legacyItalic>Attribute</legacyItalic> argument was not SQL_ATTR_ODBC_VERSION, and the SQL_ATTR_ODBC_VERSION environment attribute had not been set on the environment.</para>
    </content>
  </section>
  <section>
    <title>All Other ODBC Functions</title>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>E0</para>
              <para>Unallocated</para>
            </TD>
            <TD>
              <para>E1</para>
              <para>Allocated</para>
            </TD>
            <TD>
              <para>E2</para>
              <para>Connection</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>(IH)</para>
            </TD>
            <TD>
              <para>(IH)</para>
            </TD>
            <TD>
              <para>--</para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>