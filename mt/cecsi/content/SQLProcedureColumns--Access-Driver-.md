---
title: SQLProcedureColumns (Access Driver)
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 34fee995-5848-4ecb-bda0-fc362a77b2d9
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# SQLProcedureColumns (Access Driver)
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <alert class="note">
      <para>This topic provides Access Driver-specific information. For general information about this function, see the appropriate topic under <legacyLink xlink:href="b7a49774-f458-44ce-9a04-a0457501405b">ODBC API Reference</legacyLink>.</para>
    </alert>
    <para>Application developers should look for driver-defined columns starting at the end of the result set and proceeding backward. </para>
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
            <para>COLUMN_TYPE</para>
          </TD>
          <TD>
            <para>SQL_PARAM_INPUT or SQL_RESULT_COL</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>ORDINAL</para>
          </TD>
          <TD>
            <para>This is a driver-specific column that is returned at the end of the result set. The SQL type of the column is an integer.</para>
          </TD>
        </tr>
      </tbody>
    </table>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>