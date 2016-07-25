---
title: "Setting Options Programmatically for the Excel Driver"
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b5ee3636-4591-427a-a65a-a2d5926fcc1a
caps.latest.revision: 5
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Setting Options Programmatically for the Excel Driver
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
      <thead>
        <tr>
          <TD>
            <para>Option</para>
          </TD>
          <TD>
            <para>Description</para>
          </TD>
          <TD>
            <para>Method</para>
          </TD>
        </tr>
      </thead>
      <tbody>
        <tr>
          <TD>
            <para>Data Source Name</para>
          </TD>
          <TD>
            <para>A name that identifies the data source, such as Payroll or Personnel.</para>
          </TD>
          <TD>
            <para>To set this option dynamically, use the <legacyBold>DSN</legacyBold> keyword in a call to <legacyLink xlink:href="885b3bea-f4b6-4902-b994-f78a912b612f">SQLConfigDataSource</legacyLink>.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>Database</para>
          </TD>
          <TD>
            <para>A Microsoft Access data source can be set up without selecting or creating a database. If no database is provided upon setup, the user will be prompted to choose a database file when connecting to the data source.</para>
          </TD>
          <TD>
            <para>To set this option dynamically, use the <legacyBold>DBQ</legacyBold> keyword in a call to <legacyLink xlink:href="885b3bea-f4b6-4902-b994-f78a912b612f">SQLConfigDataSource</legacyLink>.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>Description</para>
          </TD>
          <TD>
            <para>An optional description of the data in the data source; for example, "Hire date, salary history, and current review of all employees."</para>
          </TD>
          <TD>
            <para>To set this option dynamically, use the <legacyBold>DESCRIPTION</legacyBold> keyword in a call to <legacyLink xlink:href="885b3bea-f4b6-4902-b994-f78a912b612f">SQLConfigDataSource</legacyLink>.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>Directory</para>
          </TD>
          <TD>
            <para>Displays the currently selected directory. </para>
            <para>For Microsoft Excel 3.0/4.0 files, the path display is labeled "Directory", while for Microsoft Excel 5.0, 7.0, or 97 files, the path display is labeled "Workbook".</para>
          </TD>
          <TD>
            <para>To set this option dynamically, use the <legacyBold>DEFAULTDIR</legacyBold> keyword in a call to <legacyLink xlink:href="885b3bea-f4b6-4902-b994-f78a912b612f">SQLConfigDataSource</legacyLink>.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>Read Only</para>
          </TD>
          <TD>
            <para>Designates the database as read-only.</para>
          </TD>
          <TD>
            <para>To set this option dynamically, use the <legacyBold>READONLY</legacyBold> keyword in a call to <legacyLink xlink:href="885b3bea-f4b6-4902-b994-f78a912b612f">SQLConfigDataSource</legacyLink>.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>Rows to Scan</para>
          </TD>
          <TD>
            <para>The number of rows to scan to determine the data type of each column. The data type is determined given the maximum number of kinds of data found. If data is encountered that does not match the data type guessed for the column, the data type will be returned as a NULL value.</para>
            <para>For the Microsoft Excel driver, you can enter a number from 1 to 16 for the rows to scan. The value defaults to 8; if it is set to 0, all rows are scanned. (A number outside the limit will return an error.)</para>
          </TD>
          <TD>
            <para>To set this option dynamically, use the <legacyBold>MAXSCANROWS</legacyBold> keyword in a call to <legacyLink xlink:href="885b3bea-f4b6-4902-b994-f78a912b612f">SQLConfigDataSource</legacyLink>.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>Select Directory</para>
          </TD>
          <TD>
            <para>Displays a dialog box where you can select a directory containing the files you want to access.</para>
            <para>When defining a data source directory (for all drivers except Microsoft Access), specify the directory where your most commonly used files are located. The ODBC driver uses this directory as the default directory. Copy other files into this directory if they are used frequently. Alternatively, you can qualify file names in a SELECT statement with the directory name:</para>
            <para>SELECT * FROM C:\MYDIR\EMP</para>
            <para>Or, you can specify a new default directory by using the <legacyBold>SQLSetConnectOption</legacyBold> function with the SQL_CURRENT_QUALIFIER option.</para>
            <para>For Microsoft Excel 3.0 or 4.0 files, the path display is labeled "Directory", and the path selection button is labeled "Select Directory". For Microsoft Excel 5.0, 7.0, or 97 files, the path display is labeled "Workbook", and the path selection button is labeled "Select Workbook". When defining a data source directory, specify the directory where your most commonly used Microsoft Excel files are located for Microsoft Excel 3.0/4.0, or the directory where the workbook file is located for Microsoft Excel 5.0, 7.0, or 97. <legacyBold>Use Current Directory</legacyBold> is disabled for Microsoft Excel 5.0, 7.0, and 97.</para>
          </TD>
          <TD>
            <para>To set this option dynamically, use the <legacyBold>DEFAULTDIR</legacyBold> keyword in a call to <legacyLink xlink:href="885b3bea-f4b6-4902-b994-f78a912b612f">SQLConfigDataSource</legacyLink>.</para>
          </TD>
        </tr>
      </tbody>
    </table>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>