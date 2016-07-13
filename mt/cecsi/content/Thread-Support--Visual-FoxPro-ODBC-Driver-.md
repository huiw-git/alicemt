---
title: Thread Support (Visual FoxPro ODBC Driver)
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0c6abbbc-012b-41aa-bded-5e7e362d015b
manager:jhubbard
translation.priority.ht: 
  - en-gb
---
# Thread Support (Visual FoxPro ODBC Driver)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The Visual FoxPro ODBC Driver is thread-safe. Access to environment handles (<legacyItalic>hen</legacyItalic>), connection handles (<legacyItalic>hdbc</legacyItalic>), and statement handles (<legacyItalic>hstmt</legacyItalic>) is wrapped in appropriate semaphores to prevent other processes from accessing and potentially altering the driver's internal data structures.</para>
    <para>In a multithreaded application, you can cancel a function that is running synchronously on an <legacyItalic>hstmt</legacyItalic> by calling <legacyLink xlink:href="4f7baa1d-37ef-4051-ae13-7dc38033af16">SQLCancel</legacyLink> on a separate thread.</para>
    <para>The driver uses a separate thread to fetch data when you use progressive fetching. To use progressive fetching for a data source, select the <legacyBold>Fetch data in background</legacyBold> check box on the <legacyLink xlink:href="de020197-7f53-4643-9cbf-b7887ba88de9">ODBC Visual FoxPro Setup dialog box</legacyLink> or use the BackgroundFetch attribute keyword in your connection string. Avoid using background fetch when you call the driver from multithreaded applications. For information about connection string attribute keywords, see <legacyLink xlink:href="57634960-47e9-49bf-95c1-6e3702ac8166">Using Connection Strings</legacyLink>.</para>
    <para>For more information about threads and <legacyBold>SQLCancel</legacyBold>, see <legacyLink xlink:href="ac0b5972-627f-4440-8c5a-0e8da728726d">SQLCancel</legacyLink> in the <legacyItalic>ODBC Programmer's Reference</legacyItalic>.</para>
  </introduction>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>