---
title: Managing Data Sources
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 67cc4945-4850-4eb4-8da6-b835ddaeca4c
manager:jhubbard
translation.priority.ht: 
  - en-gb
---
# Managing Data Sources
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>After you have installed an ODBC driver from the driver's setup program, you can define one or more data sources for it. The data source name (DSN) should provide a unique description of the data; for example, <legacyItalic>Payroll</legacyItalic> or <legacyItalic>Accounts Payable</legacyItalic>. The user and system data sources that are defined for all currently installed drivers are listed in the <legacyBold>User DSN</legacyBold> or <legacyBold>System DSN</legacyBold> tabs of the <legacyBold>ODBC Data Source Administrator</legacyBold> dialog box. The file data sources in a given directory are listed in the <legacyBold>File DSN</legacyBold> tab; the directory to be shown is entered in the <legacyBold>Look in</legacyBold> box in the <legacyBold>File DSN</legacyBold> tab.</para>
    <alert class="note">
      <para>To manage a data source that connects to a 32-bit driver under 64-bit platform, use c:\windows\sysWOW64\odbcad32.exe. To manage a data source that connects to a 64-bit driver, use c:\windows\system32\odbcad32.exe. In <legacyBold>Administrative Tools</legacyBold> on a 64-bit Windows 8 operating system, there are icons for both the 32-bit and 64-bit <legacyBold>ODBC Data Source Administrator</legacyBold> dialog box.</para>
    </alert>
    <para>If you use the 64-bit odbcad32.exe to configure or remove a DSN that connects to a 32-bit driver, for example, <languageKeyword>Driver do Microsoft Access (*.mdb)</languageKeyword>, you will receive the following error message:</para>
    <code>The specified DSN contains an architecture mismatch between the Driver and Application</code>
    <para>To resolve this error, use the 32-bit odbcad32.exe to configure or remove the DSN.</para>
    <para>A data source associates a particular ODBC driver with the data you want to access through that driver. For example, you might create a data source to use the ODBC dBASE driver to access one or more dBASE files found in a specific directory on your hard disk or a network drive. Using the ODBC Data Source Administrator, you can add, modify, and delete data sources, as described in the following table.</para>
    <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
      <thead>
        <tr>
          <TD>
            <para>Action</para>
          </TD>
          <TD>
            <para>Description</para>
          </TD>
        </tr>
      </thead>
      <tbody>
        <tr>
          <TD>
            <para>Adding data sources</para>
          </TD>
          <TD>
            <para>It is possible to add multiple data sources, each one associating a driver with some data you want to access by using that driver. Give each data source a name that uniquely identifies that data source. For example, if you create a data source for a set of dBASE files that contain customer information, you might name the data source "Customers." Applications typically display data source names for users to choose from.</para>
            <para>Adding a file data source is slightly different from adding user or system data sources. For more information, see the ODBC Data Source Administrator help file.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>Modifying data sources</para>
          </TD>
          <TD>
            <para>Depending on your requirements, you might find it necessary to reconfigure data sources. You can reset options by clicking <legacyBold>Configure</legacyBold> in any driver setup dialog box.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>Deleting data sources</para>
          </TD>
          <TD>
            <para>Click <legacyBold>Remove</legacyBold> after selecting a data source.</para>
          </TD>
        </tr>
      </tbody>
    </table>
    <para>For more information about file data sources, see <legacyLink xlink:href="3003f8c2-8be6-41cc-8d9c-612e9bd0f3ae">Connecting Using File Data Sources</legacyLink> or the <legacyLink xlink:href="e299be1d-5c74-4ede-b6a3-430eb189134f">SQLDriverConnect Function</legacyLink>.</para>
  </introduction>
  <relatedTopics>
<link xlink:href="a2f66b4c-a4ac-401b-8e95-d8f96332e0b5">ODBC Data Source Administrator</link>
</relatedTopics>
</developerConceptualDocument>