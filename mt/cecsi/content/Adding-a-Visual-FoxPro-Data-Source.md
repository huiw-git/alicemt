---
title: "Adding a Visual FoxPro Data Source"
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1487e188-52c8-4f48-b4fe-25a650dd9e97
caps.latest.revision: 8
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Adding a Visual FoxPro Data Source
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>To access Visual FoxPro data from your application, you must have a data source. You can create a data source as follows:  </para>
    <list class="bullet">
      <listItem>
        <para>In an application, such as Microsoft® Word, Microsoft Excel, or Microsoft Access, that uses ODBC drivers.</para>
      </listItem>
      <listItem>
        <para>Outside your application, using the Microsoft Windows® 95, Microsoft Windows 98, or Microsoft Windows NT®/Windows 2000 Control Panel.</para>
      </listItem>
    </list>
    <para>After a data source exists on your system, you can reuse the same data source every time that you want to access Visual FoxPro data. If you have several different databases or tables you want to access, you can create a separate data source for each database or directory.</para>
    <para>The following procedure creates a data source by using Control Panel. For more information about how to create a data source from an application, see <legacyLink xlink:href="116efee6-2cd1-4d54-a6e4-1ee7b2fe82e2">Accessing Visual FoxPro Data from Microsoft Office</legacyLink>.</para>
    <procedure>
      <title>To add a Visual FoxPro data source</title>
      <steps class="ordered">
        <step>
          <content>
            <para>On computers that are running Windows 2000, open the Windows Control panel and double-click Administrative Tools.</para>
          </content>
        </step>
        <step>
          <content>
            <para>Double-click Data Sources (ODBC) to open the ODBC Data Source Administrator dialog box. This icon is available after you have installed the Visual FoxPro ODBC Driver or any ODBC driver software. </para>
            <alert class="note">
              <para>If you are running an earlier version of Windows, open the Windows Control panel and double-click 32-bit ODBC or ODBC to open the ODBC Data Source Administrator dialog box.</para>
            </alert>
          </content>
        </step>
        <step>
          <content>
            <para>Click Add.</para>
          </content>
        </step>
        <step>
          <content>
            <para>In the Create New Data Source dialog box, select Microsoft Visual FoxPro Driver and then click Finish.</para>
          </content>
        </step>
        <step>
          <content>
            <para>In the <legacyLink xlink:href="de020197-7f53-4643-9cbf-b7887ba88de9">ODBC Visual FoxPro Setup dialog box</legacyLink>, type the data source name and description, select the database type, select the database or directory, and then click OK. </para>
            <para>The new data source name is displayed in the User Data Sources list in the User DSN tab of the ODBC Data Source Administrator dialog box. </para>
          </content>
        </step>
        <step>
          <content>
            <para>Click OK to save the new data source and close the ODBC Data Source Administrator dialog box.</para>
          </content>
        </step>
      </steps>
    </procedure>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>