---
title: SQLConfigDataSource (Text File Driver)
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c505d36e-1e72-47b2-a9e5-e4926b408468
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# SQLConfigDataSource (Text File Driver)
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <alert class="note">
      <para>This topic provides Text File Driver-specific information. For general information about this function, see the appropriate topic under <legacyLink xlink:href="b7a49774-f458-44ce-9a04-a0457501405b">ODBC API Reference</legacyLink>.</para>
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
            <para>CHARACTERSET</para>
          </TD>
          <TD>
            <para>For the Text driver, OEM or ANSI.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>COLNAMEHEADER</para>
          </TD>
          <TD>
            <para>For the Text driver, indicates whether the first record of data will specify the column names. Either TRUE or FALSE.</para>
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
            <para>An integer ID for the driver. 27 (Text)</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>EXTENSIONS</para>
          </TD>
          <TD>
            <para>Lists the file name extensions of the Text files on the data source. </para>
            <para>This sets the same option as <legacyBold>Extensions List</legacyBold> in the setup dialog box.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>FIL</para>
          </TD>
          <TD>
            <para>File type   Text</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>FILETYPE</para>
          </TD>
          <TD>
            <para>File type for the Text driver (Text).</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>FORMAT</para>
          </TD>
          <TD>
            <para>For the Text driver, can be FIXEDLENGTH, TABDELIMITED, CSVDELIMITED (by a comma), or DELIMITED() (by the special character specified in the parentheses). The special character is one character in length and can be in character, decimal, or hexadecimal format.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>MAXSCANROWS</para>
          </TD>
          <TD>
            <para>The number of rows to be scanned when setting a column's data type based upon existing data.</para>
            <para>For the Text driver, you can enter a number from 1 to 32767 for the number of rows to scan; however, the value will always default to 25. (A number outside the limit will return an error.) </para>
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
      </tbody>
    </table>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>