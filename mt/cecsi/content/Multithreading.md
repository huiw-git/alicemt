---
title: "Multithreading"
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: cdfebdf5-12ff-4e28-8055-41f49b77f664
caps.latest.revision: 4
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Multithreading
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>On multithread operating systems, drivers must be thread-safe. That is, it must be possible for applications to use the same handle on more than one thread. How this is achieved is driver-specific, and it is likely that drivers will serialize any attempts to concurrently use the same handle on two different threads.</para>
    <para>Applications commonly use multiple threads instead of asynchronous processing. The application creates a separate thread, calls an ODBC function on it, and then continues processing on the main thread. Rather than having to continually poll the asynchronous function, as is the case when the SQL_ATTR_ASYNC_ENABLE statement attribute is used, the application can simply let the newly created thread finish.</para>
    <para>Functions that accept a statement handle and are running on one thread can be canceled by calling <legacyBold>SQLCancel</legacyBold> with the same statement handle from another thread. Although drivers should not serialize the use of <legacyBold>SQLCancel</legacyBold> in this manner, there is no guarantee that calling <legacyBold>SQLCancel</legacyBold> will actually cancel the function running on the other thread.</para>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>