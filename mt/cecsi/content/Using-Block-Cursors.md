---
title: "Using Block Cursors"
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2aad7d6b-216e-47e7-b3cb-f95ad096f21a
caps.latest.revision: 5
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Using Block Cursors
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Support for block cursors is built into ODBC 3.<legacyItalic>x</legacyItalic>. <legacyBold>SQLFetch</legacyBold> can be used only for multirow fetches when called in ODBC 3.<legacyItalic>x</legacyItalic>; if an ODBC 2.<legacyItalic>x</legacyItalic> application calls <legacyBold>SQLFetch</legacyBold>, it will open only a single-row, forward-only cursor. When an ODBC 3.<legacyItalic>x</legacyItalic> application calls <legacyBold>SQLFetch</legacyBold> in an ODBC 2.<legacyItalic>x</legacyItalic> driver, it returns a single row unless the driver supports <legacyBold>SQLExtendedFetch</legacyBold>. For more information, see <legacyLink xlink:href="d9d271f6-d2d9-49b9-a365-4909ca06caae">Block Cursors, Scrollable Cursors, and Backward Compatibility</legacyLink> in Appendix G: Driver Guidelines for Backward Compatibility.</para>
    <para>To use block cursors, the application sets the rowset size, binds the rowset buffers (as described in the previous section), optionally sets the SQL_ATTR_ROWS_FETCHED_PTR and SQL_ATTR_ROW_STATUS_PTR statement attributes, and calls <legacyBold>SQLFetch</legacyBold> or <legacyBold>SQLFetchScroll</legacyBold> to fetch a block of rows. The application can change the rowset size and bind new rowset buffers (by calling <legacyBold>SQLBindCol</legacyBold> or specifying a bind offset) even after rows have been fetched.</para>
    <para>This section contains the following topics.  </para>
    <list class="bullet">
      <listItem>
        <para>             <legacyLink xlink:href="60366ae8-175c-456a-ae5e-bdd860786911">Rowset Size</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="a069b979-5108-4905-932f-8ae8e7905ff2">Number of Rows Fetched and Status</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="12599cdc-7725-4faf-bcae-e163ea0f5851">SQLGetData and Block Cursors; block curso</legacyLink>           </para>
      </listItem>
    </list>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>