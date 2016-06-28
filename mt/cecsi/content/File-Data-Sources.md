---
title: File Data Sources
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: db245c80-981a-4638-bd03-69d04bc67af0
translation.priority.ht: 
  - en-gb
---
# File Data Sources
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>       <legacyItalic>File data sources</legacyItalic> are stored in a file and allow connection information to be used repeatedly by a single user or shared among several users. When a file data source is used, the Driver Manager makes the connection to the data source using the information in a .dsn file. This file can be manipulated like any other file. A file data source does not have a data source name, as does a machine data source, and is not registered to any one user or machine.</para>
    <para>A file data source streamlines the connection process, because the .dsn file contains the connection string that would otherwise have to be built for a call to the <legacyBold>SQLDriverConnect</legacyBold> function. Another advantage of the .dsn file is that it can be copied to any machine, so identical data sources can be used by many machines as long as they have the appropriate driver installed. A file data source can also be shared by applications. A shareable file data source can be placed on a network and used simultaneously by multiple applications.</para>
    <para>A .dsn file can also be unshareable. An unshareable .dsn file resides on a single machine and points to a machine data source. Unshareable file data sources exist mainly to allow the easy conversion of machine data sources to file data sources so that an application can be designed to work solely with file data sources. When the Driver Manager is sent the information in an unshareable file data source, it connects as necessary to the machine data source that the .dsn file points to.</para>
    <para>For more information about file data sources, see <legacyLink xlink:href="3003f8c2-8be6-41cc-8d9c-612e9bd0f3ae">Connecting Using File Data Sources</legacyLink>, or the <legacyLink xlink:href="e299be1d-5c74-4ede-b6a3-430eb189134f">SQLDriverConnect</legacyLink> function description.</para>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>