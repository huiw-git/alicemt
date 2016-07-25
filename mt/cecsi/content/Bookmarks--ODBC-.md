---
title: "Bookmarks (ODBC)"
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1d7cccc5-f847-4321-b240-28570854ee5c
caps.latest.revision: 4
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Bookmarks (ODBC)
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>A bookmark is a value used to identify a row of data. The meaning of the bookmark value is known only to the driver or data source. For example, it might be as simple as a row number or as complex as a disk address. Bookmarks in ODBC are a bit different from bookmarks in real books. In a real book, the reader places a bookmark at a specific page and then looks for that bookmark to return to the page. In ODBC, the application requests a bookmark for a particular row, stores it, and passes it back to the cursor to return to the row. Thus, bookmarks in ODBC are similar to a reader writing down a page number, remembering it, and then looking up the page again.</para>
    <para>To determine a driver's support of bookmarks, an application calls <legacyBold>SQLGetInfo</legacyBold> with the SQL_BOOKMARK_PERSISTENCE option. The bits in this value describe what operations bookmarks survive, such as whether bookmarks are still valid after the cursor is closed.</para>
    <para>This section contains the following topics.  </para>
    <list class="bullet">
      <listItem>
        <para>             <legacyLink xlink:href="cb2e7443-0260-4d1a-930f-0154db447979">Bookmark Types</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="a34c8f09-b786-4835-a44b-b7294c970aff">Retrieving Bookmarks</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="4862f098-41a4-4bd2-894e-f71bb97f9bc0">Scrolling by Bookmark</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="e2ee58d7-c28f-435f-b537-06207215dd2f">Updating, Deleting, or Fetching by Bookmark</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="ea347635-fbe3-41c1-b537-4048b7c0f7da">Comparing Bookmarks</legacyLink>           </para>
      </listItem>
    </list>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>