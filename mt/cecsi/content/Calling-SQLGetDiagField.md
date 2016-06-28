---
title: Calling SQLGetDiagField
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3c4fb606-b81c-4f11-9820-f0a54e3bc401
translation.priority.ht: 
  - en-gb
---
# Calling SQLGetDiagField
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>When an ODBC 3.<legacyItalic>x</legacyItalic> application calls <legacyBold>SQLGetDiagField</legacyBold> in an ODBC 2<legacyItalic>.x</legacyItalic> driver, the driver will return SQL_SUCCESS and the appropriate information in <legacyItalic>*DiagInfoPtr</legacyItalic> if the <legacyItalic>DiagIdentifier</legacyItalic> argument is SQL_DIAG_CLASS_ORIGIN, SQL_DIAG_CLASS_SUBCLASS_ORIGIN, SQL_DIAG_CONNECTION_NAME, SQL_DIAG_MESSAGE_TEXT, SQL_DIAG_NATIVE, SQL_DIAG_NUMBER, SQL_DIAG_RETURNCODE, SQL_DIAG_SERVER_NAME, or SQL_DIAG_SQLSTATE. All other diagnostic fields will return SQL_ERROR.</para>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>