---
title: "SQLAllocConnect Mapping"
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ac89dd1f-c565-47cc-8fa3-6fa5f80b5d63
caps.latest.revision: 4
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# SQLAllocConnect Mapping
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>When an application calls <legacyBold>SQLAllocConnect</legacyBold> through an ODBC 3.<legacyItalic>x</legacyItalic> driver, the call to <legacyBold>SQLAllocConnect</legacyBold>(<legacyItalic>henv</legacyItalic>, <legacyItalic>phdbc</legacyItalic>) is mapped to <legacyBold>SQLAllocHandle</legacyBold> as follows:

</para>
  </introduction>
  <section>
    <content>
      <list class="ordered">
        <listItem>
          <para>The Driver Manager allocates a connection and returns it to the application.</para>
        </listItem>
        <listItem>
          <para>When the application establishes a connection, the Driver Manager calls
</para>
          <code>SQLAllocHandle(SQL_HANDLE_DBC, InputHandle, OutputHandlePtr)</code>
          <para>in the driver with <legacyItalic>InputHandle</legacyItalic> set to <legacyItalic>henv</legacyItalic>, and <legacyItalic>OutputHandlePtr</legacyItalic> set to <legacyItalic>phdbc</legacyItalic>.
</para>
        </listItem>
      </list>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>