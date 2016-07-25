---
title: "Loading by Ordinal"
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 337d90ab-68eb-4940-a2f3-f7d5693ee766
caps.latest.revision: 5
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Loading by Ordinal
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>In ODBC 2.<legacyItalic>x</legacyItalic>, loading by ordinal could be performed to improve the performance of the connection process. An ODBC 2.<legacyItalic>x</legacyItalic> driver exports a dummy function with the ordinal 199; when the Driver Manager detects it, it resolves the addresses of the ODBC functions by ordinal, not by name. This functionality is still supported for ODBC 2.<legacyItalic>x</legacyItalic> drivers but is not supported for ODBC 3<legacyItalic>.x</legacyItalic> drivers.</para>
  </introduction>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>