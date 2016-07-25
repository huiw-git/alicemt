---
title: "Descriptor Transitions"
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0cf24fe6-5e3c-45fa-81b8-4f52ddf8501d
caps.latest.revision: 4
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Descriptor Transitions
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>ODBC descriptors have the following three states.</para>
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
            <para>D0</para>
          </TD>
          <TD>
            <para>Unallocated descriptor</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>D1i</para>
          </TD>
          <TD>
            <para>Implicitly allocated descriptor</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>D1e</para>
          </TD>
          <TD>
            <para>Explicitly allocated descriptor</para>
          </TD>
        </tr>
      </tbody>
    </table>
    <para>The following tables show how each ODBC function affects the descriptor state.</para>
  </introduction>
  <section>
    <title>SQLAllocHandle</title>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>D0</para>
              <para>Unallocated</para>
            </TD>
            <TD>
              <para>D1i</para>
              <para>Implicit</para>
            </TD>
            <TD>
              <para>D1e</para>
              <para>Explicit</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>D1i[1]</para>
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
              <para>D1e[2]</para>
            </TD>
            <TD>
              <para>--</para>
            </TD>
            <TD>
              <para>--</para>
            </TD>
          </tr>
        </tbody>
      </table>
      <para>[1]   This row shows transitions when <legacyItalic>HandleType</legacyItalic> was SQL_HANDLE_STMT.</para>
      <para>[2]   This row shows transitions when <legacyItalic>HandleType</legacyItalic> was SQL_HANDLE_DESC.</para>
    </content>
  </section>
  <section>
    <title>SQLCopyDesc</title>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>D0</para>
              <para>Unallocated</para>
            </TD>
            <TD>
              <para>D1i</para>
              <para>Implicit</para>
            </TD>
            <TD>
              <para>D1e</para>
              <para>Explicit</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>(IH)</para>
            </TD>
            <TD>
              <para>--</para>
            </TD>
            <TD>
              <para>--</para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <section>
    <title>SQLFreeHandle</title>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>D0</para>
              <para>Unallocated</para>
            </TD>
            <TD>
              <para>D1i</para>
              <para>Implicit</para>
            </TD>
            <TD>
              <para>D1e</para>
              <para>Explicit</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>--[1]</para>
            </TD>
            <TD>
              <para>D0</para>
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
              <para>(HY017)</para>
            </TD>
            <TD>
              <para>D0</para>
            </TD>
          </tr>
        </tbody>
      </table>
      <para>[1]   This row shows transitions when <legacyItalic>HandleType</legacyItalic> was SQL_HANDLE_STMT.</para>
      <para>[2]   This row shows transitions when <legacyItalic>HandleType</legacyItalic> was SQL_HANDLE_DESC.</para>
    </content>
  </section>
  <section>
    <title>SQLGetDescField and SQLGetDescRec</title>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>D0</para>
              <para>Unallocated</para>
            </TD>
            <TD>
              <para>D1i</para>
              <para>Implicit</para>
            </TD>
            <TD>
              <para>D1e</para>
              <para>Explicit</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>(IH)</para>
            </TD>
            <TD>
              <para>--</para>
            </TD>
            <TD>
              <para>--</para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <section>
    <title>SQLSetDescField and SQLSetDescRec</title>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>D0</para>
              <para>Unallocated</para>
            </TD>
            <TD>
              <para>D1i</para>
              <para>Implicit</para>
            </TD>
            <TD>
              <para>D1e</para>
              <para>Explicit</para>
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
        </tbody>
      </table>
      <para>[1]   This row shows transitions when <legacyItalic>DescriptorHandle</legacyItalic> was the handle of an ARD, APD, or IPD, or (for <legacyBold>SQLSetDescField</legacyBold>) when <legacyItalic>DescriptorHandle</legacyItalic> was the handle of an IRD and <legacyItalic>FieldIdentifier</legacyItalic> was SQL_DESC_ARRAY_STATUS_PTR or SQL_DESC_ROWS_PROCESSED_PTR.</para>
    </content>
  </section>
  <section>
    <title>All Other ODBC Functions</title>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>D0</para>
              <para>Unallocated</para>
            </TD>
            <TD>
              <para>D1i</para>
              <para>Implicit</para>
            </TD>
            <TD>
              <para>D1e</para>
              <para>Explicit</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>--</para>
            </TD>
            <TD>
              <para>--</para>
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