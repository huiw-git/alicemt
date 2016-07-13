---
title: Interoperability
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 43b7c849-9d59-4002-9977-9e2c8730b859
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Interoperability
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>       <legacyItalic>Interoperability</legacyItalic> is the ability of a single application to operate with many different DBMSs. The need to write generic, interoperable applications was one of the major factors leading to the development of ODBC. However, interoperability is not a simple path followed from "not interoperable" to "completely interoperable." The path has many branches, and each requires trade-offs among features, speed, code complexity, and development time.</para>
    <para>The process of writing an interoperable application follows several steps:  </para>
    <list class="ordered">
      <listItem>
        <para>Deciding whether the application will use ODBC.</para>
      </listItem>
      <listItem>
        <para>Choosing a level of interoperability and deciding which trade-offs are necessary to reach that level.</para>
      </listItem>
      <listItem>
        <para>Writing interoperable code and testing it as fully as possible.</para>
      </listItem>
    </list>
    <para>It should be noted that interoperability is primarily the domain of the application writer. Drivers are designed to work with a single DBMS and, by definition, are not interoperable. They play a role in interoperability by correctly implementing and exposing ODBC over a single DBMS.</para>
    <para>This section contains the following topics.  </para>
    <list class="bullet">
      <listItem>
        <para>             <legacyLink xlink:href="bfa5e6ee-5979-42a9-be6f-a84d1ee7a54c">Is ODBC the Answer?</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="1f915832-a7c1-41cd-8c4f-bf6d976951b0">Choosing a Level of Interoperability</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="23bee0f6-e12a-4598-b34e-df11a8086829">Determining the Target DBMSs and Drivers</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="59760114-508e-46c5-81d2-8f2498c0d778">Considering Database Features to Use</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="4d08d886-6d8b-40fd-8544-13032f4bf6c7">Length of the Product Cycle</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="8b42b8ae-7862-4b63-a0b3-2a204e0c43a5">Writing an Interoperable Application</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="489083cb-8430-40be-9ef2-d75b9a2eea88">Testing Interoperable Applications</legacyLink>           </para>
      </listItem>
    </list>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>