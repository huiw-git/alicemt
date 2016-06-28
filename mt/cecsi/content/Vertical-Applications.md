---
title: Vertical Applications
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d50ea3e6-7a9e-4fb6-8cd8-1d429d2f7b3c
translation.priority.ht: 
  - en-gb
---
# Vertical Applications
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Vertical applications typically perform a well-defined task against a single DBMS. For example, an order entry application tracks the orders in a company. What these types of applications have in common is that the database schema is usually designed by the application developer and, while the application might work with a number of different DBMSs, it works with a single DBMS for a single customer.</para>
    <para>Because vertical applications usually require certain functionality, such as scrollable cursors or transactions, they rarely support all DBMSs. Instead, they tend to be highly interoperable among a limited set of DBMSs. Typically, vertical application developers choose to support those DBMSs that represent a large fraction of the market and ignore the rest. They might even choose to support specific drivers for those DBMSs to reduce their testing and product support costs.</para>
    <para>Because vertical applications can support a known set of DBMSs, they sometimes contain driver-specific or DBMS-specific code. However, such code is best kept to a minimum because it requires extra time to maintain.</para>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>