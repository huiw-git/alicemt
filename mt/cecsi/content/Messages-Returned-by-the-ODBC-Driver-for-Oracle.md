---
title: Messages Returned by the ODBC Driver for Oracle
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 150bde1d-adb6-4e77-90e9-4dc93499a746
manager:jhubbard
translation.priority.ht: 
  - en-gb
---
# Messages Returned by the ODBC Driver for Oracle
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <alert class="important">
      <para>This feature will be removed in a future version of Windows. Avoid using this feature in new development work, and plan to modify applications that currently use this feature. Instead, use the ODBC driver provided by Oracle.</para>
    </alert>
    <para>If an Oracle error message is available, it will be returned preceded by the [Microsoft], [ODBC Driver for Oracle], and [Oracle] tags; otherwise, the message is returned without the [Oracle] tag as in the following examples:</para>
  </introduction>
  <section>
    <title>Oracle error message:</title>
    <content>
      <code>[Microsoft][ODBC driver for Oracle][Oracle]ORA-nnnnn message-text</code>
    </content>
  </section>
  <section>
    <title>ODBC Driver for Oracle error message:</title>
    <content>
      <code>[Microsoft][ODBC driver for Oracle]</code>
    </content>
  </section>
  <relatedTopics />
</developerConceptualDocument>