---
title: "Embedded SQL"
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 8eee3527-f225-4aa2-bd18-a16bd3ab0fb7
caps.latest.revision: 4
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Embedded SQL
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The first technique for sending SQL statements to the DBMS is embedded SQL. Because SQL does not use variables and control-of-flow statements, it is often used as a database sublanguage that can be added to a program written in a conventional programming language, such as C or COBOL. This is a central idea of embedded SQL: placing SQL statements in a program written in a host programming language. Briefly, the following techniques are used to embed SQL statements in a host language:  </para>
    <list class="bullet">
      <listItem>
        <para>Embedded SQL statements are processed by a special SQL precompiler. All SQL statements begin with an introducer and end with a terminator, both of which flag the SQL statement for the precompiler. The introducer and terminator vary with the host language. For example, the introducer is "EXEC SQL" in C and "&amp;SQL(" in MUMPS, and the terminator is a semicolon (;) in C and a right parenthesis in MUMPS.</para>
      </listItem>
      <listItem>
        <para>Variables from the application program, called host variables, can be used in embedded SQL statements wherever constants are allowed. These can be used on input to tailor an SQL statement to a particular situation and on output to receive the results of a query.</para>
      </listItem>
      <listItem>
        <para>Queries that return a single row of data are handled with a singleton SELECT statement; this statement specifies both the query and the host variables in which to return data.</para>
      </listItem>
      <listItem>
        <para>Queries that return multiple rows of data are handled with cursors. A cursor keeps track of the current row within a result set. The DECLARE CURSOR statement defines the query, the OPEN statement begins the query processing, the FETCH statement retrieves successive rows of data, and the CLOSE statement ends query processing.</para>
      </listItem>
      <listItem>
        <para>While a cursor is open, positioned update and positioned delete statements can be used to update or delete the row currently selected by the cursor.</para>
      </listItem>
    </list>
    <para>This section contains the following topics.  </para>
    <list class="bullet">
      <listItem>
        <para>             <legacyLink xlink:href="b8a26e05-3c82-4c5f-8f01-9de0edb645e9">Embedded SQL Example</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="9e94146a-5b80-4a01-b586-1e03ff05b9ac">Compiling an Embedded SQL Program</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="667d92ec-fed9-4028-81d4-bb9ba867356a">Static SQL</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="0bfb9ab7-9c15-4433-93bc-bad8b6c9d287">Dynamic SQL</legacyLink>           </para>
      </listItem>
    </list>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>