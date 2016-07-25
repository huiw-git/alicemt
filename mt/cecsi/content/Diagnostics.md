---
title: "Diagnostics"
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 450abd88-90a1-4fbc-b417-8efbdd8e1dea
caps.latest.revision: 4
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Diagnostics
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Functions in ODBC return diagnostic information in two ways. The return code indicates the overall success or failure of the function, while diagnostic records provide detailed information about the function. At least one diagnostic record — the header record — is returned even if the function succeeds.</para>
    <para>Diagnostic information is used at development time to catch programming errors such as invalid handles and syntax errors in hard-coded SQL statements. It is used at run time to catch run-time errors and warnings such as data truncation, access violations, and syntax errors in SQL statements entered by the user.</para>
    <para>This section contains the following topics.  </para>
    <list class="bullet">
      <listItem>
        <para>             <legacyLink xlink:href="e893b719-4392-476f-911a-5ed6da6f7e94">Return Codes</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="92c73f9b-3ed7-410d-9cec-2771004aae60">Diagnostic Records</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="4f486bb1-fad8-4064-ac9d-61f2de85b68b">Using SQLGetDiagRec and SQLGetDiagField</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="11ba1857-b533-4517-8131-a2a8a0154a0a">Implementing SQLGetDiagRec and SQLGetDiagField</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="57f88c22-e7fa-4270-a0bf-443a2684cf6e">Diagnostic Handling Examples</legacyLink>           </para>
      </listItem>
    </list>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>