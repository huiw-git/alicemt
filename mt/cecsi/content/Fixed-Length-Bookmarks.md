---
title: Fixed-Length Bookmarks
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: cbd8185e-fb03-408f-b80b-1a2e164534fd
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Fixed-Length Bookmarks
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>If an ODBC 3<legacyItalic>.x</legacyItalic> driver should work with an ODBC 2.<legacyItalic>x</legacyItalic> application that uses fixed-length bookmarks, the driver must support the following:

</para>
  </introduction>
  <section>
    <content>
      <list class="bullet">
        <listItem>
          <para>SQL_UB_ON as a value for the SQL_USE_BOOKMARKS statement option. (SQL_UB_ON is deprecated in ODBC 3<legacyItalic>.x</legacyItalic>.)</para>
        </listItem>
        <listItem>
          <para>The SQL_GET_BOOKMARK statement option.</para>
        </listItem>
      </list>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>