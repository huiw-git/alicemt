---
title: The ODBC Cursor Library
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 32fb7df0-953a-4f68-b041-7d2852e45d0f
translation.priority.ht: 
  - en-gb
---
# The ODBC Cursor Library
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <alert class="important">
      <para>This feature will be removed in a future version of Windows. Avoid using this feature in new development work and plan to modify applications that currently use this feature. Microsoft recommends using the driver's cursor functionality.</para>
    </alert>
    <para>Block and scrollable cursors are very useful additions to many applications. However, not all drivers support block and scrollable cursors. The same is true of positioned update and delete statements and <legacyBold>SQLSetPos</legacyBold>, which are discussed in Updating Data. Therefore, the ODBC component of the Windows SDK, formerly included in the Microsoft Data Access Components (MDAC) SDK, includes a cursor library. The cursor library implements block, static cursors, positioned update and delete statements, and <legacyBold>SQLSetPos</legacyBold> for any driver that meets the Open Group Standard CLI conformance level. The cursor library may be redistributed with ODBC applications; see the licensing agreement in the SDK for more information.</para>
    <para>To use the cursor library, an application sets the SQL_ATTR_ODBC_CURSORS connection attribute before it connects to the data source. For more information about the cursor library, see <legacyLink xlink:href="a03084df-4e48-48ef-917d-4a3fae48a605">Appendix F: ODBC Cursor Library</legacyLink>.</para>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>