---
title: System Functions
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 36614b4c-e037-43ef-8692-67f4861b144d
manager:jhubbard
translation.priority.ht: 
  - en-gb
---
# System Functions
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The following table lists system functions that are included in the ODBC scalar function set. By calling <legacyBold>SQLGetInfo</legacyBold> with an <legacyItalic>information type</legacyItalic> of SQL_SYSTEM_FUNCTIONS, an application can determine which system functions are supported by a driver.</para>
  </introduction>
  <section>
    <content>
      <para>Arguments denoted as <legacyItalic>exp</legacyItalic> can be the name of a column, the result of another scalar function, or a literal, where the underlying data type could be represented as SQL_NUMERIC, SQL_DECIMAL, SQL_TINYINT, SQL_SMALLINT, SQL_INTEGER, SQL_BIGINT, SQL_FLOAT, SQL_REAL, SQL_DOUBLE, SQL_TYPE_DATE, SQL_TYPE_TIME, or SQL_TYPE_TIMESTAMP.</para>
      <para>Arguments denoted as <legacyItalic>value</legacyItalic> can be a literal constant, where the underlying data type can be represented as SQL_NUMERIC, SQL_DECIMAL, SQL_TINYINT, SQL_SMALLINT, SQL_INTEGER, SQL_BIGINT, SQL_FLOAT, SQL_REAL, SQL_DOUBLE, SQL_TYPE_DATE, SQL_TYPE_TIME, or SQL_TYPE_TIMESTAMP.</para>
      <para>Values returned are represented as ODBC data types. </para>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>Function</para>
            </TD>
            <TD>
              <para>Description</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>
              <legacyBold>DATABASE( ) </legacyBold>
(ODBC 1.0)</para>
            </TD>
            <TD>
              <para>Returns the name of the database corresponding to the connection handle. (The name of the database is also available by calling <legacyBold>SQLGetConnectOption</legacyBold> with the SQL_CURRENT_QUALIFIER connection option.)</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
              <legacyBold>IFNULL(</legacyBold>
              <legacyItalic>exp</legacyItalic>,<legacyItalic>value</legacyItalic><legacyBold>) </legacyBold>
(ODBC 1.0)</para>
            </TD>
            <TD>
              <para>If <legacyItalic>exp</legacyItalic> is null, <legacyItalic>value</legacyItalic> is returned. If <legacyItalic>exp</legacyItalic> is not null, <legacyItalic>exp</legacyItalic> is returned. The possible data type or types of <legacyItalic>value</legacyItalic> must be compatible with the data type of <legacyItalic>exp</legacyItalic>.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
              <legacyBold>USER( ) </legacyBold>
(ODBC 1.0)</para>
            </TD>
            <TD>
              <para>Returns the user name in the DBMS. (The user name is also available by way of <legacyBold>SQLGetInfo</legacyBold> by specifying the information type: SQL_USER_NAME.) This can be different than the login name.</para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>