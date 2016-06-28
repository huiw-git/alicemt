---
title: Generic Applications
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: dda2a3c4-76ef-40a6-b3a1-9e95bed61618
translation.priority.ht: 
  - en-gb
---
# Generic Applications
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Generic applications sometimes perform a hard-coded task, such as a spreadsheet retrieving data from a database. They might also perform a variety of user-defined tasks, such as a generic query application allowing the user to enter and execute an SQL statement. What generic applications have in common is that they must work with a variety of different DBMSs and that the developer does not know beforehand what these DBMSs will be.</para>
    <para>Therefore, generic applications need to be highly interoperable. The developer must make many choices, trading off interoperability for features, and must write code that expects drivers to support a wide range of functionality. While generic applications might be tuned to work with popular DBMSs, they rarely contain driver-specific or DBMS-specific code.</para>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>