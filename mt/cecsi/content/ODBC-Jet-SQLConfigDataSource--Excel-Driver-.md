---
title: ODBC Jet SQLConfigDataSource (Excel Driver)
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 885b3bea-f4b6-4902-b994-f78a912b612f
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# ODBC Jet SQLConfigDataSource (Excel Driver)
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <alert class="note">
      <para>This topic provides Excel Driver-specific information. For general information about this function, see the appropriate topic under <legacyLink xlink:href="b7a49774-f458-44ce-9a04-a0457501405b">ODBC API Reference</legacyLink>.</para>
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
            <para>DBQ</para>
          </TD>
          <TD>
            <para>For the Microsoft Excel driver when accessing Microsoft Excel 5.0 or later files, the name of the workbook file.</para>
            <para>This sets the same option as <legacyBold>Database</legacyBold> in the setup dialog box.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>DEFAULTDIR</para>
          </TD>
          <TD>
            <para>The path specification to the directory.</para>
            <para>This sets the same option as <legacyBold>Select Directory </legacyBold>or <legacyBold>Select Workbook</legacyBold> in the setup dialog box.</para>
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
            <para>534 (Microsoft Excel 3.0)</para>
            <para>278 (Microsoft Excel 4.0)</para>
            <para>22 (Microsoft Excel 5.0/7.0)</para>
            <para>790 (Microsoft Excel 97-2003)</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>FIL</para>
          </TD>
          <TD>
            <para>File type, for example, Excel 3.0, Excel 4.0, Excel 5.0, Excel 7.0, Excel 97, Excel 2000, or Excel 2003.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>FIRSTROWHASNAMES</para>
          </TD>
          <TD>
            <para>Indicates whether the cells of the first row of the range contain the column names for the table (1) or not (0).</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>MAXSCANROWS</para>
          </TD>
          <TD>
            <para>The number of rows to be scanned when setting a column's data type based upon existing data.</para>
            <para>A number from 1 to 16 can be entered for the rows to scan. The value defaults to 8; if it is set to 0, all rows are scanned. (A number outside the limit will return an error.) </para>
            <para>This sets the same option as <legacyBold>Rows to</legacyBold> <legacyBold>Scan </legacyBold>in the setup dialog box.</para>
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
            <para>THREADS</para>
          </TD>
          <TD>
            <para>The number of background threads for the engine to use. For the Microsoft Access driver, this value defaults to 3, but can be changed. For the dBASE, MicrosoftExceldriver this value is 3, and cannot be changed. </para>
            <para>This sets the same option as <legacyBold>Threads</legacyBold> in the setup dialog box.</para>
          </TD>
        </tr>
      </tbody>
    </table>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>