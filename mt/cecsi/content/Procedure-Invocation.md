---
title: "Procedure Invocation"
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b9ff2c3a-2003-4832-adbe-08dd0f5ad948
caps.latest.revision: 4
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Procedure Invocation
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>When the Microsoft Access driver is used, procedures can be invoked from the driver by using the <legacyBold>SQLExecDirect</legacyBold> or <legacyBold>SQLPrepare</legacyBold> function with the following syntax: {CALL <legacyItalic>procedure-name</legacyItalic> [(<legacyItalic>parameter</legacyItalic>[,<legacyItalic>parameter</legacyItalic>]...)]}. Note that expressions are not supported as parameters to a called procedure.</para>
  </introduction>
  <section>
    <content>
      <para>If a procedure name includes a dash, the name must be delimited with back quotes (`).</para>
      <para>A parameterized query can be called using the previous statement.</para>
    </content>
  </section>
  <relatedTopics />
</developerConceptualDocument>