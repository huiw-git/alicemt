---
title: "Scrolling by Bookmark"
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4862f098-41a4-4bd2-894e-f71bb97f9bc0
caps.latest.revision: 4
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Scrolling by Bookmark
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>When fetching rows with <legacyBold>SQLFetchScroll</legacyBold>, an application can use a bookmark as a basis for selecting the starting row. This is a form of absolute addressing because it does not depend on the current cursor position. To scroll to a bookmarked row, the application calls <legacyBold>SQLFetchScroll</legacyBold> with a <legacyItalic>FetchOrientation</legacyItalic> of SQL_FETCH_BOOKMARK. This operation uses the bookmark pointed to by the SQL_ATTR_FETCH_BOOKMARK_PTR statement attribute. It returns the rowset starting with the row identified by that bookmark. An application can specify an offset for this operation in the <legacyItalic>FetchOffset</legacyItalic> argument of the call to <legacyBold>SQLFetchScroll</legacyBold>. When an offset is specified, the first row of the returned rowset is determined by adding the number in the <legacyItalic>FetchOffset</legacyItalic> argument to the number of the row identified by the bookmark. This use of the <legacyItalic>FetchOffset</legacyItalic> argument is not supported when used with ODBC 2.<legacyItalic>x</legacyItalic> drivers; when an application calls <legacyBold>SQLFetchScroll</legacyBold> in an ODBC 2.<legacyItalic>x</legacyItalic> driver with <legacyItalic>FetchOrientation</legacyItalic> set to SQL_FETCH_BOOKMARK, the <legacyItalic>FetchOffset</legacyItalic> argument must be set to 0.</para>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>