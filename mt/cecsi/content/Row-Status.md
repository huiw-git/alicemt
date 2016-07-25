---
title: "Row Status"
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0f0b1fb6-f697-4ced-811c-2908e210bc71
caps.latest.revision: 7
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Row Status
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <alert class="important">
      <para>This feature will be removed in a future version of Windows. Avoid using this feature in new development work and plan to modify applications that currently use this feature. Microsoft recommends using the driver's cursor functionality.</para>
    </alert>
    <para>The cursor library creates a buffer in the cache for the row status. The cursor library retrieves values for the row status array (specified with the SQL_ATTR_ROW_STATUS_PTR statement attribute) from this buffer. For each row, the cursor library sets this buffer to:  </para>
  </introduction>
  <section>
    <content>
      <list class="bullet">
        <listItem>
          <para>SQL_ROW_DELETED when it executes a positioned delete statement on the row.</para>
        </listItem>
        <listItem>
          <para>SQL_ROW_ERROR when it encounters an error retrieving the row from the data source with <legacyBold>SQLFetch</legacyBold>.</para>
        </listItem>
        <listItem>
          <para>SQL_ROW_SUCCESS when it successfully fetches the row from the data source with <legacyBold>SQLFetch</legacyBold>.</para>
        </listItem>
        <listItem>
          <para>SQL_ROW_UPDATED when it executes a positioned update statement on the row.</para>
        </listItem>
      </list>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>