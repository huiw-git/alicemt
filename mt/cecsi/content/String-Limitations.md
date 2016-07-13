---
title: String Limitations
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ec1da65f-c69d-415d-bf75-8fda8aa2b39f
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# String Limitations
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The maximum length of an SQL statement string is 65,000 characters. </para>
    <para>When the Microsoft Access driver is used, only SQL-92 string constants (with single quotation marks, not double quotation marks) are supported.</para>
    <para>The pipe character (|) cannot be used in a string, whether the character is enclosed in back quotes or not.</para>
    <para>For maximum interoperability, applications should pass strings in parameters, rather than passing quoted strings.</para>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>