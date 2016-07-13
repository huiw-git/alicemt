---
title: Closing the Cursor
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4f19bf5e-6d8c-40ae-a975-cfd62a0790ec
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Closing the Cursor
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>When an application has finished using a cursor, it calls <legacyBold>SQLCloseCursor</legacyBold> to close the cursor. For example:</para>
    <code>SQLCloseCursor(hstmt);</code>
    <para>Until the application closes the cursor, the statement on which the cursor is opened cannot be used for most other operations, such as executing another SQL statement. For a complete list of functions that can be called while a cursor is open, see <legacyLink xlink:href="15088dbe-896f-4296-b397-02bb3d0ac0fb">Appendix B: ODBC State Transition Tables</legacyLink>.</para>
    <alert class="note">
      <para>To close a cursor, an application should call <legacyBold>SQLCloseCursor</legacyBold>, not <legacyBold>SQLCancel</legacyBold>.</para>
    </alert>
    <para>Cursors remain open until they are explicitly closed, except when a transaction is committed or rolled back, in which case some data sources close the cursor. In particular, reaching the end of the result set, when <legacyBold>SQLFetch</legacyBold> returns SQL_NO_DATA, does not close a cursor. Even cursors on empty result sets (result sets created when a statement executed successfully but which returned no rows) must be explicitly closed.</para>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>