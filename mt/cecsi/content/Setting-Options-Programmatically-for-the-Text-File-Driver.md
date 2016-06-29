---
title: Setting Options Programmatically for the Text File Driver
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: cbde2ca1-5d4e-4444-a371-a72f3ac4d92a
translation.priority.ht: 
  - en-gb
---
# Setting Options Programmatically for the Text File Driver
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
            <para>To set this option dynamically, use the <legacyBold>DSN</legacyBold> keyword in a call to <legacyLink xlink:href="c505d36e-1e72-47b2-a9e5-e4926b408468">SQLConfigDataSource</legacyLink>.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>Define Format</para>
          </TD>
          <TD>
            <para>Displays the <legacyBold>Define Text Format</legacyBold> dialog box and enables you to specify the schema for individual tables in the data source directory.</para>
          </TD>
          <TD>
            <para>This option cannot be set dynamically by a call to <legacyLink xlink:href="c505d36e-1e72-47b2-a9e5-e4926b408468">SQLConfigDataSource</legacyLink>.</para>
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
            <para>To set this option dynamically, use the <legacyBold>DESCRIPTION</legacyBold> keyword in a call to <legacyLink xlink:href="c505d36e-1e72-47b2-a9e5-e4926b408468">SQLConfigDataSource</legacyLink>.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>Directory</para>
          </TD>
          <TD>
            <para>Selects the targeted directory.</para>
          </TD>
          <TD>
            <para>To set this option dynamically, use the <legacyBold>DEFAULTDIR</legacyBold> keyword in a call to <legacyLink xlink:href="c505d36e-1e72-47b2-a9e5-e4926b408468">SQLConfigDataSource</legacyLink>.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>Extensions List</para>
          </TD>
          <TD>
            <para>Lists the file name extensions of the text files on the data source. When the Text driver is used, a file with no extension is created when the CREATE TABLE statement is executed with a name that has no extension. Other drivers create a file with a default extension when no extension is provided. To create a file with a .txt extension, the extension must be included in the name. To display files without extensions in the <legacyBold>Define Text Format</legacyBold> dialog box, "*." must be added to the Extensions List.</para>
          </TD>
          <TD>
            <para>To set this option dynamically, use the <legacyBold>EXTENSIONS</legacyBold> keyword in a call to <legacyLink xlink:href="c505d36e-1e72-47b2-a9e5-e4926b408468">SQLConfigDataSource</legacyLink>.</para>
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
            <para>To set this option dynamically, use the <legacyBold>READONLY</legacyBold> keyword in a call to <legacyLink xlink:href="c505d36e-1e72-47b2-a9e5-e4926b408468">SQLConfigDataSource</legacyLink>.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>Rows to Scan</para>
          </TD>
          <TD>
            <para>The number of rows to scan to determine the data type of each column. The data type is determined given the maximum number of kinds of data found. If data is encountered that does not match the data type guessed for the column, the data type will be returned as a NULL value.</para>
            <para>For the Text driver, you may enter a number from 1 to 32767 for the number of rows to scan; however, the value will always default to 25. (A number outside the limit will return an error.)</para>
          </TD>
          <TD>
            <para>To set this option dynamically, use the <legacyBold>MAXSCANROWS</legacyBold> keyword in a call to <legacyLink xlink:href="c505d36e-1e72-47b2-a9e5-e4926b408468">SQLConfigDataSource</legacyLink>.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>Select Directory</para>
          </TD>
          <TD>
            <para>Displays a dialog box where you can select a directory containing the files you want to access.</para>
            <para>When defining a data source directory specify the directory where your most commonly used files are located. The ODBC driver uses this directory as the default directory. Copy other files into this directory if they are used frequently. Alternatively, you can qualify file names in a SELECT statement with the directory name:</para>
            <code>SELECT * FROM C:\MYDIR\EMP</code>
            <para>Or, you can specify a new default directory by using the <legacyBold>SQLSetConnectOption</legacyBold> function with the SQL_CURRENT_QUALIFIER option.</para>
          </TD>
          <TD>
            <para>To set this option dynamically, use the <legacyBold>DEFAULTDIR</legacyBold> keyword in a call to <legacyLink xlink:href="c505d36e-1e72-47b2-a9e5-e4926b408468">SQLConfigDataSource</legacyLink>.</para>
          </TD>
        </tr>
      </tbody>
    </table>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>