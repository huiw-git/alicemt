---
title: SQLProcedures (Desktop Database Drivers)
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c996ad6f-e790-40f4-a962-843422496149
manager:jhubbard
translation.priority.ht: 
  - en-gb
---
# SQLProcedures (Desktop Database Drivers)
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>       <legacyBold>SQLProcedures</legacyBold> will only return rows for those procedures that have at least one argument. Procedures that have no arguments are treated as views.</para>
    <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
      <thead>
        <tr>
          <TD>
            <para>Column</para>
          </TD>
          <TD>
            <para>Comments</para>
          </TD>
        </tr>
      </thead>
      <tbody>
        <tr>
          <TD>
            <para>PROCEDURE_QUALIFIER</para>
          </TD>
          <TD>
            <para>The path to the database file.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>PROCEDURE_OWNER</para>
          </TD>
          <TD>
            <para>NULL</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>PROCEDURE_NAME</para>
          </TD>
          <TD>
            <para>Undelimited procedure name</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>PROCEDURE_TYPE</para>
          </TD>
          <TD>
            <para>SQL_PT_PROCEDURE</para>
          </TD>
        </tr>
      </tbody>
    </table>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>