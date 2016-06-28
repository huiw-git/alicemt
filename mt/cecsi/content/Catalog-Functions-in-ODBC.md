---
title: Catalog Functions in ODBC
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4f28f557-7eca-4905-aa6d-45a6cf501a66
translation.priority.ht: 
  - en-gb
---
# Catalog Functions in ODBC
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>ODBC contains the following catalog functions:</para>
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
            <para>               <legacyBold>SQLTables</legacyBold>             </para>
          </TD>
          <TD>
            <para>Returns a list of catalogs, schemas, tables, or table types in the data source.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyBold>SQLColumns</legacyBold>             </para>
          </TD>
          <TD>
            <para>Returns a list of columns in one or more tables.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyBold>SQLStatistics</legacyBold>             </para>
          </TD>
          <TD>
            <para>Returns a list of statistics about a single table. Also returns a list of indexes associated with that table.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyBold>SQLSpecialColumns</legacyBold>             </para>
          </TD>
          <TD>
            <para>Returns a list of columns that uniquely identifies a row in a single table. Also returns a list of columns in that table that are automatically updated.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyBold>SQLPrimaryKeys</legacyBold>             </para>
          </TD>
          <TD>
            <para>Returns a list of columns that compose the primary key of a single table. </para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyBold>SQLForeignKeys</legacyBold>             </para>
          </TD>
          <TD>
            <para>Returns a list of foreign keys in a single table or a list of foreign keys in other tables that refer to a single table.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyBold>SQLTablePrivileges</legacyBold>             </para>
          </TD>
          <TD>
            <para>Returns a list of privileges associated with one or more tables.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyBold>SQLColumnPrivileges</legacyBold>             </para>
          </TD>
          <TD>
            <para>Returns a list of privileges associated with one or more columns in a single table.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyBold>SQLProcedures</legacyBold>             </para>
          </TD>
          <TD>
            <para>Returns a list of procedures in the data source.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyBold>SQLProcedureColumns</legacyBold>             </para>
          </TD>
          <TD>
            <para>Returns a list of input and output parameters, the return value, and the columns in the result set of a single procedure.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyBold>SQLGetTypeInfo</legacyBold>             </para>
          </TD>
          <TD>
            <para>Returns a list of the SQL data types supported by the data source. These data types are generally used in <legacyBold>CREATE TABLE</legacyBold> and <legacyBold>ALTER TABLE</legacyBold> statements.</para>
          </TD>
        </tr>
      </tbody>
    </table>
    <para>Because <legacyBold>SQLTables</legacyBold>, <legacyBold>SQLColumns</legacyBold>, <legacyBold>SQLStatistics</legacyBold>, and <legacyBold>SQLSpecialColumns</legacyBold> conform to the Open Group CLI, and <legacyBold>SQLGetTypeInfo</legacyBold> conforms to the ISO 92 CLI, they are implemented by most drivers. The remaining catalog functions are in the ODBC conformance level.</para>
    <para>This section contains the following topics.  </para>
    <list class="bullet">
      <listItem>
        <para>             <legacyLink xlink:href="399e1a64-8766-4c44-81ff-445399b7a1de">Data Returned by Catalog Functions</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="f5e0abec-8f24-42e0-b94f-16dd1f2004fd">Arguments in Catalog Functions</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="f1dfb3e8-a7bd-46c3-92b6-c19531e8409d">Schema Views</legacyLink>           </para>
      </listItem>
    </list>
  </introduction>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>