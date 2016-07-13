---
title: SQLConfigDataSource (dBASE Driver)
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 19909902-054c-4e19-9c06-a212aace13fe
manager:jhubbard
translation.priority.ht: 
  - en-gb
---
# SQLConfigDataSource (dBASE Driver)
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <alert class="note">
      <para>This topic provides dBASE Driver-specific information. For general information about this function, see the appropriate topic under <legacyLink xlink:href="b7a49774-f458-44ce-9a04-a0457501405b">ODBC API Reference</legacyLink>.</para>
    </alert>
    <para>The <legacyBold>SQLConfigDataSource</legacyBold> function that is used to add, modify, or delete a data source dynamically uses the following keywords.</para>
    <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
      <thead>
        <tr>
          <TD>
            <para>Keyword</para>
          </TD>
          <TD>
            <para>Description</para>
          </TD>
        </tr>
      </thead>
      <tbody>
        <tr>
          <TD>
            <para>COLLATINGSEQUENCE</para>
          </TD>
          <TD>
            <para>The sequence in which the fields are sorted.</para>
            <para>The sequence can be: ASCII (the default) or International.</para>
            <para>This sets the same option as <legacyBold>Collating Sequence</legacyBold> in the setup dialog box.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>DEFAULTDIR</para>
          </TD>
          <TD>
            <para>The path specification to the directory.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>DELETED</para>
          </TD>
          <TD>
            <para>For the dBASE driver, specifies whether or not rows that have been marked as deleted can be retrieved or positioned on. If set to 1, deleted rows are not displayed; if set to 0, deleted rows are treated the same as non-deleted rows. </para>
            <para>This sets the same option as <legacyBold>Show Deleted Rows</legacyBold> in the setup dialog box.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>DESCRIPTION</para>
          </TD>
          <TD>
            <para>A description of the data in the data source.</para>
            <para>This sets the same option as <legacyBold>Description</legacyBold> in the setup dialog box.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>DRIVER</para>
          </TD>
          <TD>
            <para>The path specification to the driver DLL.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>DRIVERID</para>
          </TD>
          <TD>
            <para>An integer ID for the driver.</para>
            <para>21 (dBASE III)</para>
            <para>277 (dBASE IV)</para>
            <para>533 (dBASE 5.0)</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>FIL</para>
          </TD>
          <TD>
            <para>File type   dBase III, dBase IV, or dBase 5</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>PAGETIMEOUT</para>
          </TD>
          <TD>
            <para>Specifies the period of time, in tenths of a second, that a page (if not used) remains in the buffer before being removed. The default is 600 tenths of a second (60 seconds). Note that this option applies to all data sources that use the ODBC driver. </para>
            <para>This sets the same option as <legacyBold>Page Timeout</legacyBold> in the setup dialog box.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>READONLY</para>
          </TD>
          <TD>
            <para>TRUE to make file read-only; FALSE to make file not read-only. </para>
            <para>This sets the same option as <legacyBold>Read Only</legacyBold> in the setup dialog box.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>STATISTICS</para>
          </TD>
          <TD>
            <para>For the dBASE driver, determines whether table size statistics are approximated. Note that this option applies to all data sources that use the ODBC driver. </para>
            <para>This sets the same option as <legacyBold>Approximate Row Count</legacyBold> in the setup dialog box.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>THREADS</para>
          </TD>
          <TD>
            <para>The number of background threads for the engine to use. This value is 3 and cannot be changed. </para>
            <para>This sets the same option as <legacyBold>Threads</legacyBold> in the setup dialog box.</para>
          </TD>
        </tr>
      </tbody>
    </table>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>