---
title: Retrieving Bookmarks
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a34c8f09-b786-4835-a44b-b7294c970aff
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Retrieving Bookmarks
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>If the application will use bookmarks, it must set the SQL_ATTR_USE_BOOKMARKS statement attribute to SQL_UB_VARIABLE before preparing or executing the statement. This is necessary because building and maintaining bookmarks can be an expensive operation, so bookmarks should be enabled only when an application can make good use of them.</para>
    <para>Bookmarks are returned as column 0 of the result set. There are three ways an application can retrieve them:  </para>
    <list class="bullet">
      <listItem>
        <para>Bind column 0 of the result set. <legacyBold>SQLFetch</legacyBold> or <legacyBold>SQLFetchScroll</legacyBold> returns the bookmarks for each row in the rowset along with the data for other bound columns.</para>
      </listItem>
      <listItem>
        <para>Call <legacyBold>SQLSetPos</legacyBold> to position to a row in the rowset and then call <legacyBold>SQLGetData</legacyBold> for column 0. If a driver supports bookmarks, it must always support the ability to call <legacyBold>SQLGetData</legacyBold> for column 0, even if it does not allow applications to call <legacyBold>SQLGetData</legacyBold> for other columns before the last bound column.</para>
      </listItem>
      <listItem>
        <para>Call <legacyBold>SQLBulkOperations</legacyBold> with the <legacyItalic>Operation</legacyItalic> argument set to SQL_ADD, and column 0 bound. The cursor inserts the row and returns the bookmark for the row in the bound buffer.</para>
      </listItem>
    </list>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>