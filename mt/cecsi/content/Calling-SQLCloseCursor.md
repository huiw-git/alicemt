---
title: Calling SQLCloseCursor
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ef448c39-a9ad-4f07-8ef3-65bd4cef672a
translation.priority.ht: 
  - en-gb
---
# Calling SQLCloseCursor
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Because <legacyBold>SQLCloseCursor</legacyBold> is almost the same as <legacyBold>SQLFreeStmt</legacyBold> with SQL_CLOSE, the Driver Manager does not map this function. Replacement functions are mapped so that existing ODBC 2<legacyItalic>.x</legacyItalic> applications can easily move to ODBC 3.<legacyItalic>x</legacyItalic> by using the new functions. Such a move makes it easier for such applications to begin using new ODBC 3.<legacyItalic>x</legacyItalic> functionality inside of conditional code in a modular fashion. <legacyBold>SQLCloseCursor</legacyBold> does not represent any new functionality. An application does not gain any advantage by moving to <legacyBold>SQLCloseCursor</legacyBold> from <legacyBold>SQLFreeStmt</legacyBold> with SQL_CLOSE.</para>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>