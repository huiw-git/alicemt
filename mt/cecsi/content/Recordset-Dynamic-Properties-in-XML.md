---
title: "Recordset Dynamic Properties in XML"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 52f8e379-812a-4db8-9210-94458926301c
caps.latest.revision: 2
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
# Recordset Dynamic Properties in XML
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The following Recordset provider-specific properties (from the Client Cursor Engine) are currently persisted into the XML format: </para>
    <list class="bullet">
      <listItem>
        <para>Update Resync </para>
      </listItem>
      <listItem>
        <para>Unique Table </para>
      </listItem>
      <listItem>
        <para>Unique Schema </para>
      </listItem>
      <listItem>
        <para>Unique Catalog </para>
      </listItem>
      <listItem>
        <para>Resync Command </para>
      </listItem>
      <listItem>
        <para>IRowsetChange </para>
      </listItem>
      <listItem>
        <para>IRowsetUpdate </para>
      </listItem>
      <listItem>
        <para>CommandTimeout </para>
      </listItem>
      <listItem>
        <para>BatchSize </para>
      </listItem>
      <listItem>
        <para>UpdateCriteria </para>
      </listItem>
      <listItem>
        <para>Reshape Name </para>
      </listItem>
      <listItem>
        <para>AutoRecalc </para>
      </listItem>
    </list>
    <para>These properties are saved in the schema section as attributes of the element definition for the Recordset being persisted. These attributes are defined in the rowset schema namespace and must have the prefix "rs:".</para>
  </introduction>
  <relatedTopics>
<link xlink:href="f3113ec4-ae31-428f-89c6-bc1024f128ea">Persisting Records in XML Format</link>
</relatedTopics>
</developerConceptualDocument>