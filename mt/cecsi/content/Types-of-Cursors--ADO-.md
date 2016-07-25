---
title: "Types of Cursors (ADO)"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7cc01544-e814-403b-bbfe-a2750bf921bd
caps.latest.revision: 4
manager: sonalm
translation.priority.ht: 
  - de-de
  - es-es
  - fr-fr
  - it-it
  - ja-jp
  - ko-kr
  - pt-br
  - ru-ru
  - zh-cn
  - zh-tw
---
# Types of Cursors (ADO)
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>As a general rule, your application should use the simplest cursor that provides the required data access. Each additional cursor characteristic beyond the basics (forward-only, read-only, static, scrolling, unbuffered) has a price — in client memory, network load, or performance. In many cases, the default cursor options generate a more complex cursor than your application actually needs.</para>
    <para>Your choice of cursor type depends on how your application uses the result set and also on several design considerations, including the size of the result set, the percentage of the data likely to be used, sensitivity to data changes, and application performance requirements.</para>
    <para>At its most basic, your cursor choice depends on whether you need to change or simply view the data:  </para>
    <list class="bullet">
      <listItem>
        <para>If you just need to scroll through a set of results, but not change data, use a <legacyLink xlink:href="2b1e062f-3294-4a6f-8241-a17045c4df18">forward-only</legacyLink> or <legacyLink xlink:href="cce93ace-c4ed-4c6c-940c-28a50ff2fd12">static</legacyLink> cursor.</para>
      </listItem>
      <listItem>
        <para>If you have a large result set and need to select just a few rows, use a <legacyLink xlink:href="14b51b17-6fd9-4146-af45-ca4b0fe6d48a">keyset</legacyLink> cursor.</para>
      </listItem>
      <listItem>
        <para>If you want to synchronize a result set with recent adds, changes, and deletes by all concurrent users, use a <legacyLink xlink:href="00460f30-8cf7-494e-82df-41012f40ae51">dynamic</legacyLink> cursor.</para>
      </listItem>
    </list>
    <para>Although each cursor type seems to be distinct, keep in mind that these cursor types are not so much different varieties as simply the result of overlapping characteristics and options.</para>
    <para>This section contains the following topics.  </para>
    <list class="bullet">
      <listItem>
        <para>             <legacyLink xlink:href="2b1e062f-3294-4a6f-8241-a17045c4df18">Forward-Only Cursors</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="cce93ace-c4ed-4c6c-940c-28a50ff2fd12">Static Cursors</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="14b51b17-6fd9-4146-af45-ca4b0fe6d48a">Keyset Cursors</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="00460f30-8cf7-494e-82df-41012f40ae51">Dynamic Cursors</legacyLink>           </para>
      </listItem>
    </list>
  </introduction>
  <relatedTopics>
<link xlink:href="2b1e062f-3294-4a6f-8241-a17045c4df18">Forward-Only Cursors</link>
<link xlink:href="cce93ace-c4ed-4c6c-940c-28a50ff2fd12">Static Cursors</link>
<link xlink:href="14b51b17-6fd9-4146-af45-ca4b0fe6d48a">Keyset Cursors</link>
<link xlink:href="00460f30-8cf7-494e-82df-41012f40ae51">Dynamic Cursors</link>
</relatedTopics>
</developerConceptualDocument>