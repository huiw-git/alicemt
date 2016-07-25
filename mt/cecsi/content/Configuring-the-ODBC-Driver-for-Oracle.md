---
title: "Configuring the ODBC Driver for Oracle"
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0a5f827c-0b80-4627-85cb-f10292b9fb33
caps.latest.revision: 8
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Configuring the ODBC Driver for Oracle
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <alert class="important">
      <para>This feature will be removed in a future version of Windows. Avoid using this feature in new development work, and plan to modify applications that currently use this feature. Instead, use the ODBC driver provided by Oracle.</para>
    </alert>
    <para>You can control performance of the ODBC Driver for Oracle by knowing the data environment and correctly setting the parameters of the data source connection through the <legacyLink xlink:href="a2f66b4c-a4ac-401b-8e95-d8f96332e0b5">ODBC Data Source Administrator</legacyLink> dialog box or through connect string parameters. The dialog box provides the following controls for connecting to a data source using the dialog box or using connect strings:  </para>
    <list class="bullet">
      <listItem>
        <para>
          <legacyBold>User DSN tab</legacyBold>   Lists the Data Source Names that are local to the computer.</para>
      </listItem>
      <listItem>
        <para>
          <legacyBold>System DSN tab</legacyBold>   Enables you to add or remove a system data source. System data sources can be accessed by all users on the local computer.</para>
      </listItem>
      <listItem>
        <para>
          <legacyBold>File DSN tab</legacyBold>   Enables you to add or remove a file data source from the local computer. File data sources can be shared by all users who have the same driver installed.</para>
      </listItem>
      <listItem>
        <para>
          <legacyBold>Drivers tab</legacyBold>   Lists the installed ODBC drivers.</para>
      </listItem>
      <listItem>
        <para>
          <legacyBold>Tracing tab</legacyBold>   Enables you to specify how the ODBC Driver Manager traces calls to ODBC functions. You can configure tracing separately for each installed ODBC application.</para>
      </listItem>
      <listItem>
        <para>
          <legacyBold>Connection Pooling tab</legacyBold>   Enables you to select connection options for each installed driver.</para>
      </listItem>
      <listItem>
        <para>
          <legacyBold>About tab</legacyBold>   Lists the installed ODBC component files.</para>
      </listItem>
    </list>
    <para>After you add a data source, you can use the <legacyBold>ODBC Data Source Administrator</legacyBold> dialog box to configure the access to your data source. Select a data source, and then click one of the tabs to edit or review the information.</para>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>