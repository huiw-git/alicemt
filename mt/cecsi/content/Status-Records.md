---
title: Status Records
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4a987f69-158f-4cc4-a31b-2b7dd8dcbb87
translation.priority.ht: 
  - en-gb
---
# Status Records
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The fields in the status records contain information about specific errors or warnings returned by the Driver Manager, driver, or data source, including the SQLSTATE, native error number, diagnostic message, column number, and row number. Status records can be created only if the function returns SQL_ERROR, SQL_SUCCESS_WITH_INFO, SQL_NO_DATA, SQL_NEED_DATA, or SQL_STILL_EXECUTING. For a complete list of fields in the status records, see the <legacyLink xlink:href="1dbc4398-97a8-4585-bb77-1f7ea75e24c4">SQLGetDiagField</legacyLink> function description.</para>
    <para>This section contains the following topics.  </para>
    <list class="bullet">
      <listItem>
        <para>             <legacyLink xlink:href="0e0436cc-230f-44b0-b373-04a57e83ee76">Sequence of Status Records</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="f29fff2e-3d09-4a8c-a2f9-2059062cbebf">SQLSTATEs</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="98027871-9901-476e-a722-ee58b7723c1f">Diagnostic Messages</legacyLink>           </para>
      </listItem>
    </list>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>