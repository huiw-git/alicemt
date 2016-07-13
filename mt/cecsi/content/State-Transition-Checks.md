---
title: State Transition Checks
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0706db7d-e125-4845-a13a-7fe4308f7360
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# State Transition Checks
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The Driver Manager checks that the state of the environment, connection, or statement is appropriate for the function being called. For example, a connection must be in an allocated state when <legacyBold>SQLConnect</legacyBold> is called; a statement must be in a prepared state when <legacyBold>SQLExecute</legacyBold> is called. The Driver Manager returns SQL_ERROR for state transition errors.</para>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>