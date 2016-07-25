---
title: "International Support (Visual FoxPro ODBC Driver)"
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: cd3fab32-13f1-4a86-abc4-5e18667669fc
caps.latest.revision: 4
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# International Support (Visual FoxPro ODBC Driver)
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The Microsoft Visual FoxPro ODBC Driver supports:  </para>
    <list class="bullet">
      <listItem>
        <para>Double-byte character sets (DBCS)</para>
      </listItem>
      <listItem>
        <para>Multiple collating sequences</para>
      </listItem>
    </list>
    <para>A collating sequence defines the <legacyItalic>sort order</legacyItalic> for data stored in a Visual FoxPro table or database. By default, the driver is configured to use the collating sequences that support the language version of your operating system.</para>
    <para>For a list of supported collating sequences, see <legacyLink xlink:href="00efbcd4-fea8-4061-86a5-82de413cb753">SET COLLATE</legacyLink>.</para>
  </introduction>
  <section>
    <title>locale</title>
    <content>
      <para>The set of information that corresponds to a given language and country/region. A locale indicates specific settings such as decimal separators, date and time formats, and character-sorting order.</para>
    </content>
  </section>
  <section>
    <title>sort order</title>
    <content>
      <para>Sort orders incorporate the sorting rules of different <legacyItalic>locale</legacyItalic>s, allowing you to sort data in those languages correctly. In Visual FoxPro, the current sort order determines the results of character expression comparisons and the order in which the records appear in indexed or sorted tables.</para>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>