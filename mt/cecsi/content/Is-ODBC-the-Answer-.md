---
title: Is ODBC the Answer?
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: bfa5e6ee-5979-42a9-be6f-a84d1ee7a54c
translation.priority.ht: 
  - en-gb
---
# Is ODBC the Answer?
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Before delving into the question of interoperability, consider the following question: Should the application use ODBC at all? This might seem a strange question to ask in a guide to ODBC, but it is, in fact, a legitimate one. ODBC was not designed to completely replace native database APIs, nor was it designed to provide database access in all circumstances. It was designed to provide a common interface to databases and was intended to free application programmers from having to learn about and maintain links to multiple databases.</para>
    <para>Custom applications are prime candidates for native database APIs. The main reason is that custom applications often work with a single DBMS and have no need to be interoperable. Native database APIs might do a better job than ODBC of exposing the capabilities of a particular DBMS and might expose capabilities not exposed by ODBC. Furthermore, because the developers of custom applications are usually familiar with the native database API for their DBMS, there is little reason to learn ODBC. However, it is interesting to note that for some DBMSs, ODBC is the native database API.</para>
    <para>So which applications are candidates for ODBC? The best candidates are applications that work with more than one DBMS. This includes virtually all generic and vertical applications. It also includes a number of custom applications. For example, custom applications that use several different DBMSs are much easier and cleaner to write with ODBC than with multiple native APIs. And custom applications written with ODBC are much easier to migrate as a company moves from one DBMS to another or deploys the same application against different DBMSs.</para>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>