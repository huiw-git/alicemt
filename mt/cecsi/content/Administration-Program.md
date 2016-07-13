---
title: Administration Program
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a6c8248a-7a01-42e7-aaed-99dc94d50028
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Administration Program
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <alert class="note">
      <para>Starting with Windows XP and Windows Server 2003, ODBC is included in the Windows operation system. You should only explicitly install ODBC on earlier versions of Windows.</para>
    </alert>
    <para>An administration program, the ODBC Administrator, is included with the Windows SDK/MDAC SDK. This program and can be redistributed by users of the SDK. In addition, developers can write their own administration programs. Generally, developers write their own administration programs only if they want to retain complete control over data source configuration, or if they are configuring data sources directly from an application that is acting as an administration program. For example, a spreadsheet program might allow users to add and then use data sources at run time.</para>
    <para>The administration program first loads the installer DLL. It then calls functions in the installer DLL to perform the following tasks:  </para>
    <list class="bullet">
      <listItem>
        <para>
          <legacyBold>Add, modify, or delete data sources interactively.</legacyBold> The administration program can call <legacyBold>SQLManageDataSources</legacyBold>, <legacyBold>SQLCreateDataSource</legacyBold>, or <legacyBold>SQLConfigDataSource</legacyBold>. </para>
        <para>
          <legacyBold>SQLManageDataSources</legacyBold> displays a dialog box with which the user can add, modify, or delete data sources and specify tracing options; this function is called when the installer DLL is invoked directly from the Control Panel. <legacyBold>SQLCreateDataSource</legacyBold> displays a dialog box with which the user can only add data sources. <legacyBold>SQLConfigDataSource</legacyBold> passes the call directly to the driver setup DLL.  </para>
        <para>In all cases, the installer DLL calls <legacyBold>ConfigDSN</legacyBold> in the driver setup DLL to actually add, modify, or delete the data source. The driver setup DLL might prompt the user for additional information. </para>
      </listItem>
      <listItem>
        <para>
          <legacyBold>Add, modify, or delete data sources silently.</legacyBold> The administration program calls <legacyBold>SQLConfigDataSource</legacyBold> in the installer DLL and passes it a null window handle, the name of a data source to add, modify, or delete, and a list of values for the registry. The installer DLL calls <legacyBold>ConfigDSN</legacyBold> in the driver setup DLL to actually add, modify, or delete the data source.</para>
      </listItem>
      <listItem>
        <para>
          <legacyBold>Add, modify, or delete a default data source.</legacyBold> The default data source is the same as any other data source, except that its name is Default. It is added, modified, or deleted in the same fashion as any other data source.</para>
      </listItem>
    </list>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>