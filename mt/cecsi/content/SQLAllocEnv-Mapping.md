---
title: SQLAllocEnv Mapping
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4bb51845-ee91-4b97-9dd4-2fab977f2aec
translation.priority.ht: 
  - en-gb
---
# SQLAllocEnv Mapping
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>When an application calls <legacyBold>SQLAllocEnv</legacyBold> through an ODBC 3<legacyItalic>.x</legacyItalic> driver, the call to <legacyBold>SQLAllocEnv</legacyBold>(<legacyItalic>phenv</legacyItalic>) is mapped to <legacyBold>SQLAllocHandle</legacyBold> as follows:

</para>
  </introduction>
  <section>
    <content>
      <list class="ordered">
        <listItem>
          <para>The Driver Manager allocates an environment handle and returns it to the application. The Driver Manager calls <legacyBold>SQLSetEnvAttr</legacyBold> to set the SQL_ATTR_ODBC_VERSION environment attribute to SQL_OV_ODBC2.</para>
        </listItem>
        <listItem>
          <para>When the application establishes the first connection to a driver, the Driver Manager calls
</para>
          <code>SQLAllocHandle(SQL_HANDLE_ENV, SQL_NULL_HANDLE, OutputHandlePtr)</code>
          <para>in the driver with <legacyItalic>OutputHandlePtr</legacyItalic> set to <legacyItalic>phenv</legacyItalic>.
</para>
        </listItem>
      </list>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>