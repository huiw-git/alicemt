---
title: Location of Cache
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 240d6162-4da6-4b1f-96c7-f379f4ecb16f
manager:jhubbard
translation.priority.ht: 
  - en-gb
---
# Location of Cache
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <alert class="important">
      <para>This feature will be removed in a future version of Windows. Avoid using this feature in new development work and plan to modify applications that currently use this feature. Microsoft recommends using the driver's cursor functionality.</para>
    </alert>
    <para>The cursor library caches data in memory and in Windows® temporary files. This limits the size of the result set that the cursor library can handle only by available disk space. A temporary file is used when the data to be cached would cross the segment boundary if inserted at the end of the cursor library cache. Instead, the data to be cached is added in place of the last-saved block of data in the cache. The last-saved block of data is saved in a temporary file. If the cursor library terminates abnormally, such as when the power fails, it can leave Windows temporary files on the disk. These are named ~CTT<legacyItalic>nnnn</legacyItalic>.tmp and are created in the current directory.</para>
  </introduction>
  <section>
    <content>
      <alert class="note">
        <para>If the cursor library in Microsoft® WindowsNT®/Windows2000 attempts to cache data in a temporary file on the current directory while the application is running from a read-only share or a compact disk (such as a Microsoft Foundation Class Library sample), SQLSTATE HY000 (General Error-Unable to create a file buffer) will be returned.</para>
      </alert>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>