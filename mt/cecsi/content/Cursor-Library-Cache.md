---
title: "Cursor Library Cache"
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d6a91cd6-3905-4e3a-98ab-37fce893dbe1
caps.latest.revision: 7
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Cursor Library Cache
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <alert class="important">
      <para>This feature will be removed in a future version of Windows. Avoid using this feature in new development work and plan to modify applications that currently use this feature. Microsoft recommends using the driver's cursor functionality.</para>
    </alert>
    <para>For each row of data in the result set, the cursor library caches the data for each bound column, the length of the data in each bound column, and the status of the row. The cursor library uses the values in the cache both to return through <legacyBold>SQLFetch</legacyBold> and <legacyBold>SQLFetchScroll</legacyBold> and to construct searched statements for positioned operations. For more information, see <legacyLink xlink:href="e429254c-c43f-4fbf-98b2-5f1ed53501ff">Constructing Searched Statements</legacyLink>.</para>
  </introduction>
  <section>
    <content>
      <para>This section contains the following topics.  </para>
      <list class="bullet">
        <listItem>
          <para>
            <legacyLink xlink:href="0425818c-9469-493f-9e3c-fc03d9411c5c">Column Data</legacyLink> </para>
        </listItem>
        <listItem>
          <para>
            <legacyLink xlink:href="c762c881-ebe0-4eac-84d5-f30281fc3eca">Length of Column Data</legacyLink> </para>
        </listItem>
        <listItem>
          <para>
            <legacyLink xlink:href="0f0b1fb6-f697-4ced-811c-2908e210bc71">Row Status</legacyLink> </para>
        </listItem>
        <listItem>
          <para>
            <legacyLink xlink:href="240d6162-4da6-4b1f-96c7-f379f4ecb16f">Location of Cache</legacyLink>
          </para>
        </listItem>
      </list>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>