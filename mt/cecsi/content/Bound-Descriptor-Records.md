---
title: "Bound Descriptor Records"
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 55d09344-6682-40f6-b634-036b134ff650
caps.latest.revision: 4
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Bound Descriptor Records
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>When the application sets the SQL_DESC_DATA_PTR field of a descriptor record so that it no longer contains a null value, the record is said to be <legacyItalic>bound</legacyItalic>.</para>
    <para>If the descriptor is an APD, each bound record constitutes a bound parameter. For input parameters, the application must bind a parameter for each dynamic parameter marker in the SQL statement before executing the statement. For output parameters, the application need not bind the parameter. </para>
    <para>If the descriptor is an ARD, which describes a row of database data, each bound record constitutes a bound column.</para>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>