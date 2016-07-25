---
title: "Identifiers Limitations"
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b3466382-71cb-4f82-8318-092a8fcef3df
caps.latest.revision: 4
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Identifiers Limitations
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>If an identifier contains a space or a special symbol, the identifier must be enclosed in back quotes. A valid name is a string of no more than 64 characters, of which the first character must not be a space. Valid names cannot include control characters or the following special characters: ` | # * ? [ ] . ! $ .</para>
    <para>Do not use the reserved words listed in the SQL grammar in Appendix C of the <legacyItalic>ODBC Programmer's Reference</legacyItalic> (or the shorthand form of these reserved words) as identifiers (that is, table or column names), unless you surround the word in back quotes (`).</para>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>