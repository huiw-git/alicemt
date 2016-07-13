---
title: Testing Interoperable Applications
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 489083cb-8430-40be-9ef2-d75b9a2eea88
manager:jhubbard
translation.priority.ht: 
  - en-gb
---
# Testing Interoperable Applications
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Testing interoperable applications is at best a time-consuming business and at worst impossible because new drivers continually appear on the market. However, a reasonable degree of testing is possible. Applications with limited or low interoperability need only be tested against those drivers they are guaranteed to support. However, they must be fully tested against these drivers.</para>
    <para>Highly interoperable applications cannot be tested practically against all drivers. The best that most application developers can do is to test them fully against a small number of drivers and cursorily against several more. Tested drivers should include the most popular drivers for the most popular DBMSs in the application's market; if the market covers all DBMSs, drivers for both desktop and server DBMSs should be tested.</para>
    <para>One of the problems in testing ODBC applications is the number of components involved: the application itself, the Driver Manager, the driver, the DBMS, and possibly network software or gateways. Applications can make it easier to track errors by posting the error messages returned by ODBC functions through <legacyBold>SQLGetDiagField</legacyBold> and <legacyBold>SQLGetDiagRec</legacyBold>. These messages identify the manufacturer and component in which errors occur. For more information, see <legacyLink xlink:href="450abd88-90a1-4fbc-b417-8efbdd8e1dea">Diagnostics</legacyLink>.</para>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>