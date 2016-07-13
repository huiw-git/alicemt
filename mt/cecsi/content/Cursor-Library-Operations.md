---
title: Cursor Library Operations
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 04d514b1-dc4d-4b84-bf35-60f4657ef1f6
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Cursor Library Operations
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <alert class="important">
      <para>This feature will be removed in a future version of Windows. Avoid using this feature in new development work and plan to modify applications that currently use this feature. Microsoft recommends using the driver's cursor functionality.</para>
    </alert>
    <para>If an application working with an ODBC 2<legacyItalic>.x</legacyItalic> driver makes calls to the ODBC 3.<legacyItalic>x</legacyItalic> cursor library, the application might be able to use ODBC 3.<legacyItalic>x</legacyItalic> features that are not supported by the ODBC 2<legacyItalic>.x</legacyItalic> driver. An application writer should be careful how these features are used, however. Use of the ODBC 3.<legacyItalic>x</legacyItalic> cursor library does not make an ODBC 2<legacyItalic>.x</legacyItalic> driver into an ODBC 3.<legacyItalic>x</legacyItalic> driver.</para>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>