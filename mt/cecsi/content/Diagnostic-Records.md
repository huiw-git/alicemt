---
title: "Diagnostic Records"
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 92c73f9b-3ed7-410d-9cec-2771004aae60
caps.latest.revision: 4
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Diagnostic Records
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Associated with each environment, connection, statement, and descriptor handle are <legacyItalic>diagnostic records</legacyItalic>. These records contain diagnostic information about the last function called that used a particular handle. The records are replaced only when another function is called using that handle. There is no limit to the number of diagnostic records that can be stored at any one time.</para>
    <para>There are two types of diagnostic records: a <legacyItalic>header record</legacyItalic> and zero or more <legacyItalic>status records</legacyItalic>. The header record is record 0; the status records are records 1 and above. Diagnostic records are composed of a number of separate fields, which are different for the header record and the status records. In addition, ODBC components can define their own diagnostic record fields.</para>
    <para>Although diagnostic records can be thought of as structures, there is no requirement for them to actually be structures; how a driver stores the diagnostic information is driver-specific.</para>
    <para>Fields in diagnostic records are retrieved with <legacyBold>SQLGetDiagField</legacyBold>. The SQLSTATE, native error number, and diagnostic message fields of status records can be retrieved in a single call with <legacyBold>SQLGetDiagRec</legacyBold>.</para>
    <para>This section contains the following topics.  </para>
    <list class="bullet">
      <listItem>
        <para>             <legacyLink xlink:href="d0fff1ed-5616-422a-a394-7ea1d2486f89">Header Record</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="4a987f69-158f-4cc4-a31b-2b7dd8dcbb87">Status Records</legacyLink>           </para>
      </listItem>
    </list>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>