---
title: Creating and Terminating Threads
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a2cf98ef-1c71-4742-8ee2-b53fd8e04333
translation.priority.ht: 
  - en-gb
---
# Creating and Terminating Threads
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Multithread applications that use ODBC should call the Microsoft® Visual C++® Run-Time Library functions <legacyBold>_beginthread</legacyBold> and <legacyBold>_endthread</legacyBold> (or <legacyBold>_beginthreadex</legacyBold> and <legacyBold>_endthreadex</legacyBold>) to create and terminate threads that call the ODBC Driver Manager. If applications call the Microsoft Windows NT® functions <legacyBold>CreateThread</legacyBold> and <legacyBold>EndThread</legacyBold> instead, memory leaks will occur because the Driver Manager and some ODBC drivers call C run-time functions that will not work on a thread created by calling <legacyBold>CreateThread</legacyBold>. For more information, see the Microsoft Windows® documentation.</para>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>