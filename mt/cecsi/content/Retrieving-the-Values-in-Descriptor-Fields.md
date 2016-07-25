---
title: "Retrieving the Values in Descriptor Fields"
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c05b180f-c2b0-437b-8d1c-ce7f4da93287
caps.latest.revision: 4
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Retrieving the Values in Descriptor Fields
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>An application can call <legacyBold>SQLGetDescField</legacyBold> to obtain a single field of a descriptor record. <legacyBold>SQLGetDescField</legacyBold> gives the application access to all the descriptor fields defined in ODBC, and to driver-defined fields as well. </para>
    <para>         <legacyBold>SQLGetDescRec</legacyBold> can be called to retrieve the settings of multiple descriptor fields that affect the data type and storage of column or parameter data.</para>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>