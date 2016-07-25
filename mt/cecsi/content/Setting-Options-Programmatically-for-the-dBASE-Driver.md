---
title: "Setting Options Programmatically for the dBASE Driver"
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 336d0fd4-5448-4d8c-b7d9-49e857228e36
caps.latest.revision: 6
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Setting Options Programmatically for the dBASE Driver
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
            <para>Approximate Row Count</para>
          </TD>
          <TD>
            <para>Determines whether table size statistics are approximated. This option applies to all data sources that use the ODBC driver.</para>
          </TD>
          <TD>
            <para>To set this option dynamically, use the <legacyBold>STATISTICS</legacyBold> keyword in a call to <legacyLink xlink:href="19909902-054c-4e19-9c06-a212aace13fe">SQLConfigDataSource</legacyLink>.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>Collating Sequence</para>
          </TD>
          <TD>
            <para>The sequence in which the fields are sorted.</para>
            <para>The sequence can be: ASCII (the default) or International.</para>
          </TD>
          <TD>
            <para>To set this option dynamically, use the <legacyBold>COLLATINGSEQUENCE</legacyBold> keyword in a call to <legacyLink xlink:href="19909902-054c-4e19-9c06-a212aace13fe">SQLConfigDataSource</legacyLink>.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>Data Source Name</para>
          </TD>
          <TD>
            <para>A name that identifies the data source, such as Payroll or Personnel.</para>
          </TD>
          <TD>
            <para>To set this option dynamically, use the <legacyBold>DSN</legacyBold> keyword in a call to <legacyLink xlink:href="19909902-054c-4e19-9c06-a212aace13fe">SQLConfigDataSource</legacyLink>.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>Database</para>
          </TD>
          <TD>
            <para>A Microsoft Access data source can be set up without selecting or creating a database. If no database is provided upon setup, users will be prompted to select a database file when they connect to the data source.</para>
          </TD>
          <TD>
            <para>To set this option dynamically, use the <legacyBold>DBQ</legacyBold> keyword in a call to <legacyLink xlink:href="19909902-054c-4e19-9c06-a212aace13fe">SQLConfigDataSource</legacyLink>.</para>
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
            <para>To set this option dynamically, use the <legacyBold>DESCRIPTION</legacyBold> keyword in a call to <legacyLink xlink:href="19909902-054c-4e19-9c06-a212aace13fe">SQLConfigDataSource</legacyLink>.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>Exclusive</para>
          </TD>
          <TD>
            <para>If the <legacyBold>Exclusive</legacyBold> box is selected, the database will be opened in Exclusive mode and can be accessed by only one user at a time. Performance is enhanced when it runs in Exclusive mode.</para>
          </TD>
          <TD>
            <para>To set this option dynamically, use the <legacyBold>EXCLUSIVE</legacyBold> keyword in a call to <legacyLink xlink:href="19909902-054c-4e19-9c06-a212aace13fe">SQLConfigDataSource</legacyLink>.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>Page Timeout</para>
          </TD>
          <TD>
            <para>Specifies the period of time, in tenths of a second, that a page (if not used) remains in the buffer before it is removed. The default is 600 tenths of a second (60 seconds). This option applies to all data sources that use the ODBC driver.</para>
            <para>The page timeout cannot be 0 because of an inherent delay. The page timeout cannot be less than the inherent delay, even if the page timeout option is set below that value.</para>
          </TD>
          <TD>
            <para>To set this option dynamically, use the <legacyBold>PAGETIMEOUT</legacyBold> keyword in a call to <legacyLink xlink:href="19909902-054c-4e19-9c06-a212aace13fe">SQLConfigDataSource</legacyLink>.</para>
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
            <para>To set this option dynamically, use the <legacyBold>READONLY</legacyBold> keyword in a call to <legacyLink xlink:href="19909902-054c-4e19-9c06-a212aace13fe">SQLConfigDataSource</legacyLink>.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>Select Directory</para>
          </TD>
          <TD>
            <para>Displays a dialog box where you can select a directory that contains the files you want to access.</para>
            <para>When you define a data source directory, specify the directory where your most frequently used files are located. The ODBC driver uses this directory as the default directory. Copy other files into this directory if they are used frequently. Alternatively, you can qualify file names in a SELECT statement with the directory name:</para>
            <para>SELECT * FROM C:\MYDIR\EMP</para>
            <para>Or, you can specify a new default directory by using the <legacyBold>SQLSetConnectOption</legacyBold> function with the SQL_CURRENT_QUALIFIER option.</para>
          </TD>
          <TD>
            <para>To set this option dynamically, use the <legacyBold>DEFAULTDIR</legacyBold> keyword in a call to <legacyLink xlink:href="19909902-054c-4e19-9c06-a212aace13fe">SQLConfigDataSource</legacyLink>.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>Show Deleted Rows</para>
          </TD>
          <TD>
            <para>Specifies whether rows that have been marked as deleted can be retrieved or positioned on. If cleared, deleted rows are not displayed; if selected, deleted rows are treated the same as non-deleted rows. The default is cleared.</para>
          </TD>
          <TD>
            <para>To set this option dynamically, use the <legacyBold>DELETED</legacyBold> keyword in a call to <legacyLink xlink:href="19909902-054c-4e19-9c06-a212aace13fe">SQLConfigDataSource</legacyLink>.</para>
          </TD>
        </tr>
      </tbody>
    </table>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>