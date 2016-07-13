---
title: Processing SELECT FOR UPDATE Statements
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 8d2e79a4-5daf-458e-a536-d8b6e588753e
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Processing SELECT FOR UPDATE Statements
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <alert class="important">
      <para>This feature will be removed in a future version of Windows. Avoid using this feature in new development work and plan to modify applications that currently use this feature. Microsoft recommends using the driver's cursor functionality.</para>
    </alert>
    <para>For maximum interoperability, applications should generate result sets that will be updated with a positioned update statement by executing a <legacyBold>SELECT FOR UPDATE</legacyBold> statement. Although the cursor library does not require this, it is required by most data sources that support positioned update statements.</para>
  </introduction>
  <section>
    <content>
      <para>The cursor library ignores the columns in the <legacyBold>FOR UPDATE </legacyBold>clause of a <legacyBold>SELECT FOR UPDATE</legacyBold> statement; it removes this clause before passing the statement to the driver. In the cursor library, the SQL_ATTR_CONCURRENCY statement attribute, along with the restrictions mentioned in the previous section, controls whether the columns in a result set can be updated.</para>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>