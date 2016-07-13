---
title: Descriptors
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ef2cbb93-cd00-40f8-b1d2-5f5723a991aa
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Descriptors
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>A descriptor handle refers to a data structure that holds information about either columns or dynamic parameters. </para>
    <para>ODBC functions that operate on column and parameter data implicitly set and retrieve descriptor fields. For instance, when <legacyBold>SQLBindCol</legacyBold> is called to bind column data, it sets descriptor fields that completely describe the binding. When <legacyBold>SQLColAttribute</legacyBold> is called to describe column data, it returns data stored in descriptor fields. </para>
    <para>An application calling ODBC functions need not concern itself with descriptors. No database operation requires that the application gain direct access to descriptors. However, for some applications, gaining direct access to descriptors streamlines many operations. For example, direct access to descriptors provides a way to rebind column data, which can be more efficient than calling <legacyBold>SQLBindCol</legacyBold> again.</para>
    <alert class="note">
      <para>The physical representation of the descriptor is not defined. Applications gain direct access to a descriptor only by manipulating its fields by calling ODBC functions with the descriptor handle.</para>
    </alert>
    <para>This section contains the following topics.  </para>
    <list class="bullet">
      <listItem>
        <para>             <legacyLink xlink:href="ec20e446-e540-41ad-8559-d9c0a5b8358f">Types of Descriptors</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="f38623c8-fdd4-4601-b1f0-97c593d31177">Descriptor Fields</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="c615ab7a-f631-4783-a37f-d429873b6047">Allocating and Freeing Descriptors</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="394fe500-803d-463f-ae95-f8eb87b66bc8">Getting and Setting Descriptor Fields</legacyLink>           </para>
      </listItem>
    </list>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>