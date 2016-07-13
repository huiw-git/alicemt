---
title: Obtaining Descriptor Handles
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 936f983f-c7e9-43f3-97ea-dd4b1bbf4654
manager:jhubbard
translation.priority.ht: 
  - en-gb
---
# Obtaining Descriptor Handles
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>An application obtains the handle of any explicitly allocated descriptor as an output argument of the call to <legacyBold>SQLAllocHandle</legacyBold>. The handle of an implicitly allocated descriptor is obtained by calling <legacyBold>SQLGetStmtAttr</legacyBold>.</para>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>