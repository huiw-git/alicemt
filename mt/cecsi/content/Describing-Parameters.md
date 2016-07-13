---
title: Describing Parameters
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 118d0f47-2afd-4955-bb47-38b1e2c2f38f
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Describing Parameters
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>       <legacyBold>SQLBindParameter</legacyBold> has arguments that describe the parameter: its SQL type, precision, and scale. The driver uses this information, or <legacyItalic>metadata,</legacyItalic> to convert the parameter value to the type needed by the data source. At first glance, it might seem that the driver is in a better position to know the parameter metadata than the application; after all, the driver can easily discover the metadata for a result set column. As it turns out, this is not the case. First, most data sources do not provide a way for the driver to discover parameter metadata. Second, most applications already know the metadata.</para>
    <para>If an SQL statement is hard-coded in the application, the application writer already knows the type of each parameter. If an SQL statement is constructed by the application at run time, the application can determine the metadata as it builds the statement. For example, when the application constructs the clause</para>
    <code>WHERE OrderID = ?</code>
    <para>it can call <legacyBold>SQLColumns</legacyBold> for the OrderID column.</para>
    <para>The only situation in which the application cannot easily determine the parameter metadata is when the user enters a parameterized statement. In this case, the application calls <legacyBold>SQLPrepare</legacyBold> to prepare the statement, <legacyBold>SQLNumParams</legacyBold> to determine the number of parameters, and <legacyBold>SQLDescribeParam</legacyBold> to describe each parameter. However, as was noted earlier, most data sources do not provide a way for the driver to discover parameter metadata, so <legacyBold>SQLDescribeParam</legacyBold> is not widely supported.</para>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>