---
title: "Arguments in Catalog Functions"
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f5e0abec-8f24-42e0-b94f-16dd1f2004fd
caps.latest.revision: 4
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Arguments in Catalog Functions
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>All catalog functions accept arguments with which an application can restrict the scope of the data returned. For example, the first and second calls to <legacyBold>SQLTables</legacyBold> in the following code return a result set containing information about all tables, while the third call returns information about the Orders table:</para>
    <code>SQLTables(hstmt1, NULL, 0, NULL, 0, NULL, 0, NULL, 0);
SQLTables(hstmt2, NULL, 0, NULL, 0, "%", SQL_NTS, NULL, 0);
SQLTables(hstmt3, NULL, 0, NULL, 0, "Orders", SQL_NTS, NULL, 0);</code>
    <para>Catalog function string arguments fall into four different types: ordinary argument (OA), pattern value argument (PV), identifier argument (ID), and value list argument (VL). Most string arguments can be of one of two different types, depending on the value of the SQL_ATTR_METADATA_ID statement attribute. The following table lists the arguments for each catalog function and describes the type of the argument for an SQL_TRUE or SQL_FALSE value of SQL_ATTR_METADATA_ID.</para>
    <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
      <thead>
        <tr>
          <TD>
            <para>Function</para>
          </TD>
          <TD>
            <para>Argument</para>
          </TD>
          <TD>
            <para>Type when SQL_</para>
            <para>ATTR_METADATA_</para>
            <para>ID = SQL_FALSE</para>
          </TD>
          <TD>
            <para>Type when SQL_</para>
            <para>ATTR_METADATA_</para>
            <para>ID = SQL_TRUE</para>
          </TD>
        </tr>
      </thead>
      <tbody>
        <tr>
          <TD>
            <para>               <legacyBold>SQLColumnPrivileges</legacyBold>             </para>
          </TD>
          <TD>
            <para>               <legacyItalic>CatalogName</legacyItalic>               <legacyItalic>SchemaName</legacyItalic>               <legacyItalic>TableName</legacyItalic>               <legacyItalic>ColumnName</legacyItalic>             </para>
          </TD>
          <TD>
            <para>OA OA OA PV</para>
          </TD>
          <TD>
            <para>ID ID ID ID</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyBold>SQLColumns</legacyBold>             </para>
          </TD>
          <TD>
            <para>               <legacyItalic>CatalogName</legacyItalic>               <legacyItalic>SchemaName</legacyItalic>               <legacyItalic>TableName</legacyItalic>               <legacyItalic>ColumnName</legacyItalic>             </para>
          </TD>
          <TD>
            <para>OA PV PV PV</para>
          </TD>
          <TD>
            <para>ID ID ID ID</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyBold>SQLForeignKeys</legacyBold>             </para>
          </TD>
          <TD>
            <para>               <legacyItalic>PKCatalogName</legacyItalic>               <legacyItalic>PKSchemaName</legacyItalic>               <legacyItalic>PKTableName</legacyItalic>               <legacyItalic>FKCatalogName</legacyItalic>               <legacyItalic>FKSchemaName</legacyItalic>               <legacyItalic>FKTableName</legacyItalic>             </para>
          </TD>
          <TD>
            <para>OA OA OA OA OA OA</para>
          </TD>
          <TD>
            <para>ID ID ID ID ID ID</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyBold>SQLPrimaryKeys</legacyBold>             </para>
          </TD>
          <TD>
            <para>               <legacyItalic>CatalogName</legacyItalic>               <legacyItalic>SchemaName</legacyItalic>               <legacyItalic>TableName</legacyItalic>             </para>
          </TD>
          <TD>
            <para>OA OA OA</para>
          </TD>
          <TD>
            <para>ID ID ID</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyBold>SQLProcedureColumns</legacyBold>             </para>
          </TD>
          <TD>
            <para>               <legacyItalic>CatalogName</legacyItalic>               <legacyItalic>SchemaName</legacyItalic>               <legacyItalic>ProcName</legacyItalic>               <legacyItalic>ColumnName</legacyItalic>             </para>
          </TD>
          <TD>
            <para>OA PV PV PV</para>
          </TD>
          <TD>
            <para>ID ID ID ID</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyBold>SQLProcedures</legacyBold>             </para>
          </TD>
          <TD>
            <para>               <legacyItalic>CatalogName</legacyItalic>               <legacyItalic>SchemaName</legacyItalic>               <legacyItalic>ProcName</legacyItalic>             </para>
          </TD>
          <TD>
            <para>OA PV PV</para>
          </TD>
          <TD>
            <para>ID ID ID</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyBold>SQLSpecialColumns</legacyBold>             </para>
          </TD>
          <TD>
            <para>               <legacyItalic>CatalogName</legacyItalic>               <legacyItalic>SchemaName</legacyItalic>               <legacyItalic>TableName</legacyItalic>             </para>
          </TD>
          <TD>
            <para>OA OA OA</para>
          </TD>
          <TD>
            <para>ID ID ID</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyBold>SQLStatistics</legacyBold>             </para>
          </TD>
          <TD>
            <para>               <legacyItalic>CatalogName</legacyItalic>               <legacyItalic>SchemaName</legacyItalic>               <legacyItalic>TableName</legacyItalic>             </para>
          </TD>
          <TD>
            <para>OA OA OA</para>
          </TD>
          <TD>
            <para>ID ID ID</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyBold>SQLTablePrivileges</legacyBold>             </para>
          </TD>
          <TD>
            <para>               <legacyItalic>CatalogName</legacyItalic>               <legacyItalic>SchemaName</legacyItalic>               <legacyItalic>TableName</legacyItalic>             </para>
          </TD>
          <TD>
            <para>OA PV PV</para>
          </TD>
          <TD>
            <para>ID ID ID</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>               <legacyBold>SQLTables</legacyBold>             </para>
          </TD>
          <TD>
            <para>               <legacyItalic>CatalogName</legacyItalic>               <legacyItalic>SchemaName</legacyItalic>               <legacyItalic>TableName</legacyItalic>               <legacyItalic>TableType</legacyItalic>             </para>
          </TD>
          <TD>
            <para>PV PV PV VL</para>
          </TD>
          <TD>
            <para>ID ID ID  VL</para>
          </TD>
        </tr>
      </tbody>
    </table>
    <para>This section contains the following topics.  </para>
    <list class="bullet">
      <listItem>
        <para>             <legacyLink xlink:href="a18cdae1-6b85-41cb-875c-b5a01ec90aeb">Ordinary Arguments</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="1d3f0ea6-87af-4836-807f-955e7df2b5df">Pattern Value Arguments</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="b9de003f-cb49-4dec-b528-14a5b8ff12bd">Identifier Arguments</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="863837be-603b-4c7a-8b96-b71014037ee5">Value List Arguments</legacyLink>           </para>
      </listItem>
    </list>
  </introduction>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>