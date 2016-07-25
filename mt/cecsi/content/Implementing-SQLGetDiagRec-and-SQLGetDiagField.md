---
title: "Implementing SQLGetDiagRec and SQLGetDiagField"
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 11ba1857-b533-4517-8131-a2a8a0154a0a
caps.latest.revision: 4
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Implementing SQLGetDiagRec and SQLGetDiagField
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>       <legacyBold>SQLGetDiagRec</legacyBold> and <legacyBold>SQLGetDiagField</legacyBold> are implemented by the Driver Manager and each driver. The Driver Manager and each driver maintain diagnostic records for each environment, connection, statement, and descriptor handle, and free those records only when another function is called with that handle or the handle is freed.</para>
    <para>Although both the Driver Manager and each driver must determine the first status record according to the rankings in <legacyLink xlink:href="0e0436cc-230f-44b0-b373-04a57e83ee76">Sequence of Status Records</legacyLink>, the Driver Manager determines the final sequence of records.</para>
    <para>         <legacyBold>SQLGetDiagRec</legacyBold> and <legacyBold>SQLGetDiagField</legacyBold> do not post diagnostic records about themselves.</para>
    <para>This section contains the following topics.  </para>
    <list class="bullet">
      <listItem>
        <para>             <legacyLink xlink:href="74387c3a-d6b3-4c35-b209-b9612602b20a">Diagnostic Handling Rules</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="7b861c82-357e-4590-8074-45136e9ed15e">Role of the Driver Manager</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="cac64c24-a27d-4884-96c0-ea7988351711">Role of the Driver</legacyLink>           </para>
      </listItem>
    </list>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>