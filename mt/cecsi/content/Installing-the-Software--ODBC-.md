---
title: Installing the Software (ODBC)
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: dfac8ade-eebe-4ebe-a199-feb740ed5bae
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Installing the Software (ODBC)
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <alert class="important">
      <para>This feature will be removed in a future version of Windows. Avoid using this feature in new development work, and plan to modify applications that currently use this feature. Instead, use the ODBC driver provided by Oracle.</para>
    </alert>
    <para>The ODBC Driver for Oracle is one of the data access components. It accompanies other ODBC components, such as the ODBC Data Source Administrator, and should already be installed. The driver also can be found under "Drivers and Other Downloads" on the Microsoft Product Support Services Online Web site at www.microsoft.com.</para>
    <para>Network software must be installed according to its own documentation. The ODBC Driver for Oracle requires no special installation considerations as long as the network software is supported. </para>
    <para>Oracle software must be installed according to its own documentation. The ODBC Driver for Oracle generally requires no special installation considerations as long as the driver supports the version. However, to keep products compatible, install the ODBC Driver for Oracle last to ensure you have the latest version of the driver. Oracle maintains a public FTP site where it posts, among other things, patches to the Oracle server products and the client component that ships with the server products. These patches are required for the proper functioning of several Microsoft products and technologies. For more information about this site, see <legacyLink xlink:href="1275157b-f4e1-4c24-b273-c02555e261c2">Oracle Software Patches</legacyLink>.</para>
    <alert class="caution">
      <para>Installing Oracle software over MDAC/Windows DAC may overwrite current versions of MDAC. If problems arise using ODBC components, reinstall MDAC.</para>
    </alert>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>