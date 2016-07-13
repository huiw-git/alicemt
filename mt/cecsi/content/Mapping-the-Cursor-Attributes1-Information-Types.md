---
title: Mapping the Cursor Attributes1 Information Types
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9f112449-ca86-45ac-a865-e6174d67f91b
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Mapping the Cursor Attributes1 Information Types
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>When an ODBC 3.<legacyItalic>x</legacyItalic> application calls <legacyBold>SQLGetInfo</legacyBold> in an ODBC 2<legacyItalic>.x</legacyItalic> driver with the SQL_XXXX_CURSOR_ATTRIBUTES1 information type (for dynamic, forward-only, keyset-driver, or static cursors), the setting of the bits returned by Driver Manager depends on what the ODBC 2.<legacyItalic>x</legacyItalic> driver returns for the corresponding ODBC 2.<legacyItalic>x</legacyItalic> information types. The bits are set as shown in the following table.</para>
    <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
      <thead>
        <tr>
          <TD>
            <para>Bit in</para>
            <para>SQL_XXXX_CURSOR_ATTRIBUTES1</para>
          </TD>
          <TD>
            <para>Cursor type</para>
          </TD>
          <TD>
            <para>ODBC 2.<legacyItalic>x</legacyItalic> information</para>
            <para>type</para>
          </TD>
        </tr>
      </thead>
      <tbody>
        <tr>
          <TD>
            <para>SQL_CA1_NEXT</para>
          </TD>
          <TD>
            <para>All</para>
          </TD>
          <TD>
            <para>SQL_FETCH_DIRECTION</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_CA1_ABSOLUTE SQL_CA1_RELATIVE SQL_CA1_BOOKMARK</para>
          </TD>
          <TD>
            <para>Dynamic, keyset-driver, static</para>
          </TD>
          <TD>
            <para>SQL_FETCH_DIRECTION</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_CA1_LOCK_NO_CHANGE SQL_CA1_LOCK_UNLOCK SQL_CA1_LOCK_EXCLUSIVE</para>
          </TD>
          <TD>
            <para>Dynamic, keyset-driver, static</para>
          </TD>
          <TD>
            <para>SQL_LOCK_TYPES</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_CA1_POSITIONED_UPDATE SQL_CA1_POSITIONED_DELETE SQL_CA1_SELECT_FOR_UPDATE</para>
          </TD>
          <TD>
            <para>All</para>
          </TD>
          <TD>
            <para>SQL_POSITIONED_STATEMENTS</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SQL_CA1_POS_POSITION SQL_CA1_POS_DELETE SQL_CA1_POS_REFRESH SQL_CA1_POS_BULK_ADD </para>
          </TD>
          <TD>
            <para>Dynamic, keyset-driver, static</para>
          </TD>
          <TD>
            <para>SQL_POS_OPERATIONS</para>
          </TD>
        </tr>
      </tbody>
    </table>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>