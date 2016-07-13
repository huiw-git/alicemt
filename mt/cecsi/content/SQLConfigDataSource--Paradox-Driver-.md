---
title: SQLConfigDataSource (Paradox Driver)
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 59e84c4e-debe-49d7-b97b-84c736b0c793
manager:jhubbard
translation.priority.ht: 
  - en-gb
---
# SQLConfigDataSource (Paradox Driver)
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <alert class="note">
      <para>This topic provides Paradox Driver-specific information. For general information about this function, see the appropriate topic under <legacyLink xlink:href="b7a49774-f458-44ce-9a04-a0457501405b">ODBC API Reference</legacyLink>.</para>
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
            <para>When the Paradox driver is used, the sequence can be ASCII (default), International, Swedish-Finnish, or Norwegian-Danish.</para>
            <para>This sets the same option as <legacyBold>Collating Sequence</legacyBold> in the setup dialog box.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>DBQ</para>
          </TD>
          <TD>
            <para>The name of the database file.</para>
            <para>This sets the same option as <legacyBold>Database</legacyBold> in the setup dialog box.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>DEFAULTDIR</para>
          </TD>
          <TD>
            <para>The path specification to the directory. </para>
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
            <para>26 (Paradox 3.x)</para>
            <para>282 (Paradox 4.x)</para>
            <para>538 (Paradox 5.x)</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>EXCLUSIVE</para>
          </TD>
          <TD>
            <para>Determines whether the database will be opened in exclusive mode (accessed by only one user at a time) or shared mode (accessed by more than one user at a time). Can be true (exclusive mode) or false (shared mode). </para>
            <para>This sets the same option as <legacyBold>Exclusive</legacyBold> in the setup dialog box.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>FIL</para>
          </TD>
          <TD>
            <para>File type  Paradox 3.x, Paradox 4.x, or Paradox 5.x</para>
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
            <para>PAGETIMEOUT</para>
          </TD>
          <TD>
            <para>Specifies the period of time, in tenths of a second, that a page (if not used) remains in the buffer before being removed. The default is 600 tenths of a second (60 seconds). Note that this option applies to all data sources that use the ODBC driver. </para>
            <para>This sets the same option as <legacyBold>Page Timeout</legacyBold> in the setup dialog box.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>PARADOXNETPATH</para>
          </TD>
          <TD>
            <para>The full path of the directory containing a Paradox lock database, because it contains either the PDOXUSRS.net file (in Paradox 4.<legacyItalic>x</legacyItalic>) or the PARADOX.net file (in Paradox 5.<legacyItalic>x</legacyItalic>). If the directory does not contain one of these files, the Paradox driver creates one. For information about these files, see the Paradox documentation.</para>
            <para>Before a network directory can be selected, a Paradox user name must be entered. </para>
            <para>This sets the same option as <legacyBold>Select Network</legacyBold> <legacyBold>Directory</legacyBold> in the setup dialog box.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>PARADOXNETSTYLE</para>
          </TD>
          <TD>
            <para>For the Paradox driver, the network access style to use when accessing Paradox data: either "3.x" for Paradox 3.<legacyItalic>x</legacyItalic> or "4.x" for Paradox 4.<legacyItalic>x</legacyItalic> or 5.<legacyItalic>x</legacyItalic>. Can be set to "3.x" or "4.x" if the version is Paradox 4.<legacyItalic>x</legacyItalic> or 5.<legacyItalic>x</legacyItalic>; if the version is Paradox 3.<legacyItalic>x</legacyItalic>, the style must be "3.x". </para>
            <para>This sets the same option as <legacyBold>Net Style</legacyBold> in the setup dialog box.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>PARADOXUSERNAME</para>
          </TD>
          <TD>
            <para>For the Paradox driver, the Paradox user name. </para>
            <para>This sets the same option as <legacyBold>User Name</legacyBold> in the setup dialog box.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>PWD</para>
          </TD>
          <TD>
            <para>The password.</para>
            <para>This is an optional keyword and will never be written to the file by the driver. It is used in a call to <legacyBold>SQLDriverConnect</legacyBold> against password-secured Paradox files. The password used will be valid whenever a table is opened. If no password is passed in the connection string, no password is established for that table. If tables have different passwords, more than one cannot be opened in the same session, nor can the tables be joined.</para>
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
            <para>The number of background threads for the engine to use. This value is 3, and cannot be changed. </para>
            <para>This sets the same option as <legacyBold>Threads</legacyBold> in the setup dialog box.</para>
          </TD>
        </tr>
      </tbody>
    </table>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>