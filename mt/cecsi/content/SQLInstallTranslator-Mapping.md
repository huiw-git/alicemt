---
title: SQLInstallTranslator Mapping
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: bcd9ba4f-7834-4bc4-876e-c7478998e524
manager:jhubbard
translation.priority.ht: 
  - en-gb
---
# SQLInstallTranslator Mapping
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>When an ODBC 2.<legacyItalic>x</legacyItalic> application calls <legacyBold>SQLInstallTranslator</legacyBold> through an ODBC 3<legacyItalic>.x</legacyItalic> driver, the Driver Manager maps the call to <legacyBold>SQLInstallTranslatorEx</legacyBold>.An application should not call <legacyBold>SQLInstallTranslator</legacyBold> in the ODBC 3<legacyItalic>.x</legacyItalic> Driver Manager with the <legacyItalic>lpszInfFile</legacyItalic> argument set to a value other than NULL. The ODBC.INF file used in ODBC 2.<legacyItalic>x</legacyItalic> is no longer supported in ODBC 3<legacyItalic>.x</legacyItalic>, even for backward compatibility.</para>
  </introduction>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>