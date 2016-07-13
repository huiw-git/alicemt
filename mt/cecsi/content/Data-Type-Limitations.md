---
title: Data Type Limitations
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 81c4eab7-1f6b-47a0-b940-89d6c6a14dae
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Data Type Limitations
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The Microsoft ODBC Desktop Database Drivers impose the following limitations on data types:</para>
    <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
      <thead>
        <tr>
          <TD>
            <para>Data type</para>
          </TD>
          <TD>
            <para>Description</para>
          </TD>
        </tr>
      </thead>
      <tbody>
        <tr>
          <TD>
            <para>All data types</para>
          </TD>
          <TD>
            <para>Type conversion failures might result in the affected column being set to NULL.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>BINARY</para>
          </TD>
          <TD>
            <para>Creating a zero-length BINARY column actually returns a 255-byte BINARY column.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>DATE</para>
          </TD>
          <TD>
            <para>The DATE data type cannot be converted to another data type (or itself) by the CONVERT function.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>DECIMAL (Exact Numeric)</para>
          </TD>
          <TD>
            <para>Not supported.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>Floating-Point Data Types</para>
          </TD>
          <TD>
            <para>The number of decimal places in a floating-point number may be limited by the number format set in the International section of the Windows Control Panel. </para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>NUMERIC</para>
          </TD>
          <TD>
            <para>Supports maximum precision and a scale of 28.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>TIMESTAMP</para>
          </TD>
          <TD>
            <para>The TIMESTAMP data type cannot be converted to itself by the CONVERT function.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>TINYINT</para>
          </TD>
          <TD>
            <para>TINYINT values are always unsigned.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>Zero-Length Strings</para>
          </TD>
          <TD>
            <para>When a dBASE, Microsoft Excel, Paradox, or Textdriver is used, inserting a zero-length string into a column actually inserts a NULL instead.</para>
          </TD>
        </tr>
      </tbody>
    </table>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>