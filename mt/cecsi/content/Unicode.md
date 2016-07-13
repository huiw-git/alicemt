---
title: Unicode
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 113e1c9a-8333-4805-86f2-e4b57ab816a5
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Unicode
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Unicode defines encoding for characters in many languages.</para>
    <para>For more information about the Unicode standard, see <externalLink><linkText>The Unicode Consortium</linkText><linkUri>http://www.unicode.org</linkUri></externalLink>.</para>
    <para>Unicode defines a universal character set. A Windows ANSI code page defines a character set, typically containing characters for one language. It may be more difficult to write an application that is required to use different code pages.</para>
    <para>Unicode does not require a code page. Every code point is mapped to a single character in some language.</para>
    <para>Currently, the only Unicode encoding that ODBC supports is UCS-2, which uses a 16-bit integer (fixed length) to represent a character. Unicode allows applications to work in different languages.</para>
    <para>The ODBC 3.5 (or higher) Driver Manager is Unicode-enabled. This affects two major areas: function calls and string data types. The Driver Manager maps function string arguments and string data as required by the application and driver, both of which can be either Unicode-enabled or ANSI-enabled. These two areas are discussed in detail in the sections, <legacyLink xlink:href="eafe8c7e-f6d2-44d7-99ee-cf2148a30f4f">Unicode Function Arguments</legacyLink> and <legacyLink xlink:href="abc28718-e6d9-49fb-97ff-402d50c3c375">Unicode Data</legacyLink>.</para>
    <para>The ODBC 3.5 (or higher) Driver Manager supports the use of a Unicode driver with both a Unicode application and an ANSI application. It also supports the use of an ANSI driver with an ANSI application. The Driver Manager provides limited Unicode-to-ANSI mapping for a Unicode application working with an ANSI driver.</para>
    <para>This section contains the following topics.</para>
    <list class="bullet">
      <listItem>
        <para>
          <legacyLink xlink:href="eafe8c7e-f6d2-44d7-99ee-cf2148a30f4f">Unicode Function Arguments</legacyLink>
        </para>
      </listItem>
      <listItem>
        <para>
          <legacyLink xlink:href="abc28718-e6d9-49fb-97ff-402d50c3c375">Unicode Data</legacyLink>
        </para>
      </listItem>
    </list>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>