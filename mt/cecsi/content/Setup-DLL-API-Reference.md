---
title: Setup DLL API Reference
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f9d03f17-1c0d-4e7c-9c04-8c316e07ef25
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Setup DLL API Reference
<?xml version="1.0" encoding="utf-8"?>
<developerOrientationDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This section describes the syntax of the driver setup DLL API,which consists of two functions (<legacyBold>ConfigDriver</legacyBold> and <legacyBold>ConfigDSN</legacyBold>). <legacyBold>ConfigDriver </legacyBold>and <legacyBold>ConfigDSN</legacyBold> can be either in the driver DLL or in a separate setup DLL. </para>
    <para>In addition, this section describes the syntax of the translator setup DLL API, which consists of a single function (<legacyBold>ConfigTranslator</legacyBold>). <legacyBold>ConfigTranslator</legacyBold> can be either in the translator DLL or in a separate setup DLL.</para>
    <para>Each function is labeled with the version of ODBC in which it was introduced.</para>
    <para>This section contains the following topics.

</para>
    <list class="bullet">
      <listItem>
        <para>
          <legacyLink xlink:href="9473f48f-bcae-4784-89c1-7839bad4ed13">ConfigDriver Function</legacyLink>
        </para>
      </listItem>
      <listItem>
        <para>
          <legacyLink xlink:href="01ced74e-c575-4a25-83f5-bd7d918123f8">ConfigDSN Function</legacyLink>
        </para>
      </listItem>
      <listItem>
        <para>
          <legacyLink xlink:href="7c22f07e-36de-425b-aa67-e32a84afae92">ConfigTranslator Function</legacyLink>
        </para>
      </listItem>
    </list>
  </introduction>
  <relatedTopics />
</developerOrientationDocument>