---
title: "Default Data Source"
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: dd473cc6-f051-4aa0-ab14-3dd1b37fe99e
caps.latest.revision: 4
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Default Data Source
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The driver may select a data source, called the default data source, in certain cases where the application does not explicitly specify one:  </para>
    <list class="bullet">
      <listItem>
        <para>In a call to <legacyBold>SQLConnect</legacyBold> where the <legacyItalic>ServerName</legacyItalic> argument is a zero-length string, a null pointer, or DEFAULT.</para>
      </listItem>
      <listItem>
        <para>In a call to <legacyBold>SQLDriverConnect</legacyBold> where <legacyItalic>InConnectionString</legacyItalic> either specifies <legacyBold>DSN</legacyBold>=DEFAULT or specifies with the <legacyBold>DSN</legacyBold> keyword a data source that is not contained in the system information.</para>
      </listItem>
    </list>
    <para>It is driver-defined how the default data source is specified. This may involve administrative action and may depend on the user.</para>
  </introduction>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>