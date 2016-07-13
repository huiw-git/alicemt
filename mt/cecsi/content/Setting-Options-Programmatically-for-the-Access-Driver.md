---
title: Setting Options Programmatically for the Access Driver
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1690eb71-0cd3-4c00-9e15-f6a3ac5316dd
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Setting Options Programmatically for the Access Driver
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
            <para>Buffer Size</para>
          </TD>
          <TD>
            <para>The size of the internal buffer, in kilobytes, that is used by Microsoft Access to transfer data to and from the disk. The default buffer size is 2048 KB (displayed as 2048). Any integer value divisible by 256 can be entered.</para>
          </TD>
          <TD>
            <para>To set this option dynamically, use the MAXBUFFERSIZE keyword in a call to <legacyLink xlink:href="1b152fb7-fa12-46b9-b168-006bb1355e77">SQLConfigDataSource</legacyLink>.</para>
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
            <para>To set this option dynamically, use the <legacyBold>DSN</legacyBold> keyword in a call to <legacyLink xlink:href="1b152fb7-fa12-46b9-b168-006bb1355e77">SQLConfigDataSource</legacyLink>.</para>
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
            <para>To set this option dynamically, use the <legacyBold>DBQ</legacyBold> keyword in a call to <legacyLink xlink:href="1b152fb7-fa12-46b9-b168-006bb1355e77">SQLConfigDataSource</legacyLink>.</para>
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
            <para>To set this option dynamically, use the <legacyBold>DESCRIPTION</legacyBold> keyword in a call to <legacyLink xlink:href="1b152fb7-fa12-46b9-b168-006bb1355e77">SQLConfigDataSource</legacyLink>.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>Exclusive</para>
          </TD>
          <TD>
            <para>If the <legacyBold>Exclusive</legacyBold> box is selected, the database will be opened in Exclusive mode and can be accessed by only one user at a time. Performance is enhanced when running in Exclusive mode.</para>
          </TD>
          <TD>
            <para>To set this option dynamically, use the <legacyBold>EXCLUSIVE</legacyBold> keyword in a call to <legacyLink xlink:href="1b152fb7-fa12-46b9-b168-006bb1355e77">SQLConfigDataSource</legacyLink>.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>ImplicitCommitSync</para>
          </TD>
          <TD>
            <para>Determines how changes made outside of a transaction are written to the database. This value is initially set to "Yes", which means that the Microsoft Access driver will wait for commits in an internal/implicit transaction to be completed.</para>
          </TD>
          <TD>
            <para>This option is included in the <legacyBold>Set Advanced Options</legacyBold> dialog box for the Microsoft Access driver.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>Page Timeout</para>
          </TD>
          <TD>
            <para>Specifies the period of time, in milliseconds, that a page (if not used) remains in the buffer before being removed. For the Microsoft Access driver, the default is 500 milliseconds (0.5 seconds). This option applies to all data sources that use the ODBC driver.</para>
            <para>The page timeout cannot be 0 because of an inherent delay. The page timeout cannot be less than the inherent delay, even if the page timeout option is set below that value.</para>
          </TD>
          <TD>
            <para>To set this option dynamically, use the <legacyBold>PAGETIMEOUT</legacyBold> keyword in a call to <legacyLink xlink:href="1b152fb7-fa12-46b9-b168-006bb1355e77">SQLConfigDataSource</legacyLink>.</para>
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
            <para>To set this option dynamically, use the <legacyBold>READONLY</legacyBold> keyword in a call to <legacyLink xlink:href="1b152fb7-fa12-46b9-b168-006bb1355e77">SQLConfigDataSource</legacyLink>.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>System Database</para>
          </TD>
          <TD>
            <para>The full path of the Microsoft Access system database to be used with the Microsoft Access database you want to access.</para>
            <para>Click the <legacyBold>System Database</legacyBold> button to select the system database to be used. The ODBC Microsoft Access driver prompts the user for a name and password. The default name is Admin and the default password in Microsoft Access for the Admin user is an empty string. </para>
            <para>To increase the security of your Microsoft Access database, create a new user to replace the Admin user and delete the Admin user, or change the objects to which the Admin user has access.</para>
          </TD>
          <TD>
            <para>To set this option dynamically, use the <legacyBold>SYSTEMDB</legacyBold> keyword in a call to <legacyLink xlink:href="1b152fb7-fa12-46b9-b168-006bb1355e77">SQLConfigDataSource</legacyLink>.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>Threads</para>
          </TD>
          <TD>
            <para>The number of background threads for the engine to use. For the Microsoft Access driver, this value defaults to 3, but can be changed. The user may want to increase the number of threads if there is a large amount of activity in the database.</para>
            <para>This option is included in the <legacyBold>Set Advanced Options</legacyBold> dialog box for the Microsoft Access driver.</para>
          </TD>
          <TD>
            <para>To set this option dynamically, use the <legacyBold>THREADS</legacyBold> keyword in a call to <legacyLink xlink:href="1b152fb7-fa12-46b9-b168-006bb1355e77">SQLConfigDataSource</legacyLink>.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>UserCommitSync</para>
          </TD>
          <TD>
            <para>Determines whether the Microsoft Access driver will perform an explicit user-defined transactions asynchronously. This value is initially set to "Yes", which means that the Microsoft Access driver will wait for commits in a user-defined transaction to be completed.</para>
            <para>Setting this option to False can have unpredictable consequences in a multi-user environment.</para>
          </TD>
          <TD>
            <para>To set this option dynamically, use the <legacyBold>USERCOMMITSYNC</legacyBold> keyword in a call to <legacyLink xlink:href="1b152fb7-fa12-46b9-b168-006bb1355e77">SQLConfigDataSource</legacyLink>.</para>
          </TD>
        </tr>
      </tbody>
    </table>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>