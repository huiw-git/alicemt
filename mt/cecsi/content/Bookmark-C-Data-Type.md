---
title: "Bookmark C Data Type"
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: add88e48-ada3-4c0c-a5ac-e78903d3ff41
caps.latest.revision: 4
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Bookmark C Data Type
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The bookmark C data type allows an application to retrieve a bookmark. The bookmark C types are used only to retrieve bookmark values that can be variable in length; they should not be converted to other data types. An application retrieves a bookmark either from column 0 of the result set with <legacyBold>SQLBulkOperations</legacyBold> (with an operation of SQL_ADD), <legacyBold>SQLFetch</legacyBold>, <legacyBold>SQLFetchScroll</legacyBold>, or <legacyBold>SQLGetData</legacyBold>. For more information, see <legacyLink xlink:href="1d7cccc5-f847-4321-b240-28570854ee5c">Bookmarks</legacyLink>.</para>
  </introduction>
  <section>
    <content>
      <para>The following table lists the value of <legacyItalic>CType</legacyItalic> for the bookmark C data type, the ODBC C data type that implements the bookmark C data type, and the definition of this data type from SQL.H.</para>
      <alert class="note">
        <para>The SQL_C_BOOKMARK data type has been deprecated. ODBC 3<legacyItalic>.x</legacyItalic> applications should not use SQL_C_BOOKMARK. ODBC 3<legacyItalic>.x</legacyItalic> drivers need to support SQL_C_BOOKMARK only if they want to work with ODBC 2.<legacyItalic>x</legacyItalic> applications that use it. The Driver Manager maps SQL_C_VARBOOKMARK to SQL_C_BOOKMARK when an application works with an ODBC 2.<legacyItalic>x</legacyItalic> driver.</para>
      </alert>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>C type identifier</para>
            </TD>
            <TD>
              <para>ODBC C typedef</para>
            </TD>
            <TD>
              <para>C type</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>SQL_C_BOOKMARK
(Deprecated)</para>
            </TD>
            <TD>
              <para>BOOKMARK</para>
            </TD>
            <TD>
              <para>unsigned long int</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>SQL_C_VARBOOKMARK</para>
            </TD>
            <TD>
              <para>SQLCHAR *</para>
            </TD>
            <TD>
              <para>unsigned char *</para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>