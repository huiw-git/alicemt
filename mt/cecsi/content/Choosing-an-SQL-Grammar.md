---
title: Choosing an SQL Grammar
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4e0d189b-e407-47e0-92a9-f9982230dd0e
translation.priority.ht: 
  - en-gb
---
# Choosing an SQL Grammar
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The first decision to make when constructing SQL statements is which grammar to use. In addition to the grammars available from the various standards bodies, such as Open Group, ANSI, and ISO, virtually every DBMS vendor defines its own grammar, each of which varies slightly from the standard.</para>
    <para>         <legacyLink xlink:href="0ee36f09-59e7-4b94-88ca-7ebc0952a3be">Appendix C: SQL Grammar</legacyLink>, describes the minimum SQL grammar that all ODBC drivers must support. This grammar is a subset of the Entry level of SQL-92. Drivers may support additional grammar to conform to the Intermediate, Full, or FIPS 127-2 Transitional levels defined by SQL-92. For more information, see <legacyLink xlink:href="4f36d785-104f-4fec-93be-f201203bc7c7">SQL Minimum Grammar</legacyLink> in Appendix C: SQL Grammar, and SQL-92.</para>
    <para>Appendix C also defines <legacyItalic>escape sequences</legacyItalic> containing standard grammar for commonly available language features, such as outer joins, that are not covered by the SQL-92 grammar. For more information, see <legacyLink xlink:href="646d5f0b-df0c-47a6-a630-99cac1026a4c">ODBC Escape Sequences</legacyLink> in Appendix C: SQL Grammar, and <legacyLink xlink:href="5913abfa-d280-43e4-a2f1-05a924388bf9">Escape Sequences</legacyLink>, later in this section.</para>
    <para>The grammar that is chosen affects how the driver processes the statement. Drivers must modify SQL-92 SQL and the ODBC-defined escape sequences to DBMS-specific SQL. Because most SQL grammars are based on one or more of the various standards, most drivers do little or no work to meet this requirement. It often consists only of searching for the escape sequences defined by ODBC and replacing them with DBMS-specific grammar. When a driver encounters grammar it does not recognize, it assumes the grammar is DBMS-specific and passes the SQL statement without modification to the data source for execution.</para>
    <para>Therefore, there are really two choices of grammar to use: the SQL-92 grammar (and the ODBC escape sequences) and a DBMS-specific grammar. Of the two, only the SQL-92 grammar is interoperable, so all interoperable applications should use it. Applications that are not interoperable can use the SQL-92 grammar or a DBMS-specific grammar. DBMS-specific grammars have two advantages: They can exploit any features not covered by SQL-92, and they are marginally faster because the driver does not have to modify them. The latter feature can be partially enforced by setting the SQL_ATTR_NOSCAN statement attribute, which stops the driver from searching for and replacing escape sequences.</para>
    <para>If the SQL-92 grammar is used, the application can discover how it is modified by the driver by calling <legacyBold>SQLNativeSql</legacyBold>. This is often useful when debugging applications. <legacyBold>SQLNativeSql</legacyBold> accepts an SQL statement and returns it after the driver has modified it. Because this function is in the Core interface conformance level, it is supported by all drivers.</para>
  </introduction>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>