---
title: Connecting Directly to Drivers
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f86e198f-a088-4401-9106-aa62a0eb8f6e
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Connecting Directly to Drivers
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>As was discussed in <legacyLink xlink:href="10aaf570-01ab-4478-8339-bdde2a5e3dd1">Choosing a Data Source or Driver</legacyLink>, earlier in this section, some applications do not want to use a data source at all. Instead, they want to connect directly to a driver. <legacyBold>SQLDriverConnect</legacyBold> provides a way for the application to connect directly to a driver without specifying a data source. Conceptually, a temporary data source is created at run time.</para>
    <para>To connect directly to a driver, the application specifies the <legacyBold>DRIVER</legacyBold> keyword in the connection string instead of the <legacyBold>DSN</legacyBold> keyword. The value of the <legacyBold>DRIVER</legacyBold> keyword is the description of the driver as returned by <legacyBold>SQLDrivers</legacyBold>. For example, suppose a driver has the description Paradox Driver and requires the name of a directory containing the data files. To connect to this driver, the application might use either of the following connection strings:</para>
    <code>DRIVER={Paradox Driver};Directory=C:\PARADOX;
DRIVER={Paradox Driver};</code>
    <para>With the first string, the driver would not need any additional information. With the second string, the driver would need to prompt for the name of the directory containing the data files.</para>
  </introduction>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>