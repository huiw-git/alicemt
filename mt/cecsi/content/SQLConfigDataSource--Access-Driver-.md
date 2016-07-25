---
title: "SQLConfigDataSource (Access Driver)"
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1b152fb7-fa12-46b9-b168-006bb1355e77
caps.latest.revision: 5
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# SQLConfigDataSource (Access Driver)
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <alert class="note">
      <para>This topic provides Access Driver-specific information. For general information about this function, see the appropriate topic under <legacyLink xlink:href="b7a49774-f458-44ce-9a04-a0457501405b">ODBC API Reference</legacyLink>.</para>
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
            <para>This sets the same option as <legacyBold>Collating Sequence</legacyBold> in the setup dialog box.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>COMPACT_DB</para>
          </TD>
          <TD>
            <para>Performs data compaction on a database file. Has the following format: COMPACT_DB=&lt;path_name&gt;&lt;optionaL_sort_order&gt;&lt;optional ENCRYPT keyword&gt;.</para>
            <para>When using the COMPACT_DB keyword in the same statement with a DSN keyword, this driver ignores the DSN keyword. Therefore, compacting a database and specifying a DSN is a two-step process.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>CREATE_DB</para>
          </TD>
          <TD>
            <para>Creates a database file. Has the following format: CREATE_DB=&lt;path_name&gt;&lt;optional_sort-order&gt;&lt;optional_ENCRYPT keyword&gt;, where the path name is the full path to a Microsoft Access database. An error will be returned if the path name specifies an existing database. The sort order will be as set up in the New Database dialog box displayed when the Create button is pressed in the Microsoft Access Setup dialog box. If no sort order is specified, General is used.</para>
            <para>When using the CREATE_DB keyword in the same statement with a DSN keyword, this driver ignores the DSN keyword. Therefore, creating a database and specifying a DSN is a two-step process.When using the CREATE_DB keyword, if the pathname of the Microsoft Access database to be created contains one or more spaces, then the entire pathname must be enclosed by double quotation marks, as shown in the following examples:</para>
            <para>"C:\PROGRAM FILES\COMMON FILES\ MyAccess.mdb"</para>
            <para>"C:\PROGRAM FILES\Access2.mdb"</para>
            <para>CREATE_DB=C:\TEMP\test.mdb (no quotation marks needed)</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>CREATE_SYSDB</para>
          </TD>
          <TD>
            <para>Creates a system database file. Has the following format: CREATE_SYSDB=&lt;path-name&gt;&lt;optional-sort-order&gt;, where the path name is the full path to a Microsoft Access database. An error will be returned if the path name specifies an existing database. The sort order will be as set up in the <legacyBold>New Database</legacyBold> dialog box displayed when the <legacyBold>Create</legacyBold> button is clicked in the <legacyBold>ODBC Microsoft Access Setup</legacyBold> dialog box. If no sort order is specified, General is used.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>CREATE_V2DB</para>
          </TD>
          <TD>
            <para>Creates a database file that is compatible with Microsoft Access 2.0. Has the following format: CREATE_V2DB=&lt;path-name&gt;&lt;optional-sort-order&gt;, where the path name is the full path to a Microsoft Access database. An error will be returned if the path name specifies an existing database. The sort order will be as set up in the New Database dialog box displayed when the Create button is pressed in the Microsoft Access Setup dialog box. If no sort order is specified, General is used. </para>
            <para>When using the CREATE_V2DB keyword in the same statement with a DSN keyword, this driver ignores the DSN keyword. Therefore, creating a database and specifying a DSN is a two-step process.</para>
            <para>When using the CREATE_V2DB keyword, if the pathname of the Microsoft Access database to be created contains one or more spaces, then the entire pathname must be enclosed by double quotation marks, as shown in the following examples:</para>
            <para>"C:\PROGRAM FILES\COMMON FILES\ MyAccess.mdb"</para>
            <para>"C:\PROGRAM FILES\Access2.mdb"</para>
            <para>CREATE_V2DB=C:\TEMP\test.mdb (no quotation marks needed)</para>
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
            <para>The path specification to the database file. </para>
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
            <para>An integer ID for the driver.  25 (Microsoft Access)</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>FIL</para>
          </TD>
          <TD>
            <para>File type   MS Access for Microsoft Access</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>IMPLICITCOMMITSYNC</para>
          </TD>
          <TD>
            <para>Determines whether the Microsoft Access driver will perform internal or implicit commits asynchronously. This value is initially set to "Yes", which means that the Microsoft Access driver will wait for commits in an internal/implicit transaction to be completed. </para>
            <para>The value of this option should not be changed without careful consideration of the consequences. For more information about the option, see the <legacyItalic>Microsoft Jet Database Engine Programmer's Guide</legacyItalic>.</para>
            <para>This sets the same option as <legacyBold>ImplicitCommitSync</legacyBold> in the setup dialog box.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>MAXBUFFERSIZE</para>
          </TD>
          <TD>
            <para>The size of the internal buffer, in kilobytes, that is used by Microsoft Access to transfer data to and from the disk. The default buffer size is 2048 KB (displayed as 2048). Any integer value divisible by 256 can be used. This sets the same option as <legacyBold>Buffer Size</legacyBold> in the setup dialog box.</para>
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
            <para>PAGETIMEOUT</para>
          </TD>
          <TD>
            <para>Specifies the period of time, in milliseconds, that a page (if not used) remains in the buffer before being removed. The default is five-tenths of a second (0.5 seconds). Note that this option applies to all data sources that use the ODBC driver. </para>
            <para>This sets the same option as <legacyBold>Page Timeout</legacyBold> in the setup dialog box.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>PWD</para>
          </TD>
          <TD>
            <para>The password.</para>
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
            <para>REPAIR_DB</para>
          </TD>
          <TD>
            <para>Repairs a database damaged by a failure that occurs during the commit process.</para>
            <para>When using the REPAIR_DB keyword in the same statement with a DSN keyword, this driver ignores the DSN keyword. Therefore, repairing a database and specifying a DSN is a two-step process.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>SYSTEMDB</para>
          </TD>
          <TD>
            <para>For the Microsoft Access driver, the path specification to the system database file. </para>
            <para>This sets the same option as <legacyBold>System Database</legacyBold> in the setup dialog box.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>THREADS</para>
          </TD>
          <TD>
            <para>The number of background threads for the engine to use. This value defaults to 3, but can be changed. </para>
            <para>This sets the same option as <legacyBold>Threads</legacyBold> in the setup dialog box.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>UID</para>
          </TD>
          <TD>
            <para>For the Microsoft Access driver, the user ID name used for login.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>USERCOMMITSYNC</para>
          </TD>
          <TD>
            <para>Determines whether the Microsoft Access driver will perform user-defined transactions asynchronously. This value is initially set to "Yes", which means that the Microsoft Access driver will wait for commits in a user-defined transaction to be completed. </para>
            <para>The value of this option should not be changed without careful consideration of the consequences. For more information about the option, see the <legacyItalic>Microsoft Jet Database Engine Programmer's Guide</legacyItalic>.</para>
            <para>This sets the same option as <legacyBold>UserCommitSync</legacyBold> in the setup dialog box.</para>
          </TD>
        </tr>
      </tbody>
    </table>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>