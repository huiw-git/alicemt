---
title: "About Drivers and Data Sources"
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2bb83ef1-4bbe-4be3-8c32-c4d1140aae1d
caps.latest.revision: 4
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# About Drivers and Data Sources
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>
      <legacyItalic>Drivers</legacyItalic> are the components that process ODBC requests and return data to the application. If necessary, drivers modify an application's request into a form that is understood by the data source. You must use the driver's setup program to add or delete a driver from your computer.</para>
  </introduction>
  <section>
    <content>
      <para>
        <legacyItalic>Data sources</legacyItalic> are the databases or files accessed by a driver and are identified by a data source name (DSN). Use the ODBC Data Source Administrator to add, configure, and delete data sources from your system. The types of data sources that can be used are described in the following table.</para>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>Data source</para>
            </TD>
            <TD>
              <para>Description</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>User </para>
            </TD>
            <TD>
              <para>User DSNs are local to a computer and can be used only by the current user. They are registered in the HKEY_CURRENT_USER registry subtree.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>System </para>
            </TD>
            <TD>
              <para>System DSNs are local to a computer rather than dedicated to a user. The system or any user with privileges can use a data source set up with a system DSN. System DSNs are registered in the HKEY_LOCAL_MACHINE registry subtree.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>File </para>
            </TD>
            <TD>
              <para>File DSNs are file-based sources that can be shared among all users who have the same drivers installed and therefore have access to the database. These data sources need not be dedicated to a user nor be local to a computer. File data source names are not identified by dedicated registry entries; instead, they are identified by a file name with a .dsn extension.</para>
            </TD>
          </tr>
        </tbody>
      </table>
      <para>User and system data sources are collectively known as <legacyItalic>machine</legacyItalic> data sources because they are local to a computer.</para>
      <para>Each of these data sources has a tab in the <legacyBold>ODBC Data Source Administrator</legacyBold> dialog box. For more information about data sources, see <legacyLink xlink:href="4ae44fa2-0b9b-4e19-ab45-c1dc93b68406">Data Sources</legacyLink>.</para>
    </content>
  </section>
  <relatedTopics />
</developerConceptualDocument>