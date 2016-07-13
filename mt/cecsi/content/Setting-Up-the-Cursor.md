---
title: Setting Up the Cursor
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b80afb0e-ef2f-408f-86f5-a392edd99a56
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Setting Up the Cursor
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The application can specify the cursor type before executing a statement that creates a result set. It does this with the SQL_ATTR_CURSOR_TYPE statement attribute. If the application does not explicitly specify a type, a forward-only cursor will be used. To get a mixed cursor, an application specifies a keyset-driven cursor but declares a keyset size less than the result set size.</para>
    <para>For keyset-driven and mixed cursors, the application can also specify the keyset size. It does this with the SQL_ATTR_KEYSET_SIZE statement attribute. If the keyset size is set to 0, which is the default, the keyset size is set to the result set size and a keyset-driven cursor is used. The keyset size can be changed after the cursor has been opened.</para>
    <para>The application can also set the rowset size; for more information, see <legacyLink xlink:href="2aad7d6b-216e-47e7-b3cb-f95ad096f21a">Using Block Cursors</legacyLink>, earlier in this section.</para>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>