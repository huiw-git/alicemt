---
title: "Driver Manager Error and Warning Checks"
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: eeb5ab3f-987d-4f30-87d2-7425a81ad1d7
caps.latest.revision: 4
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Driver Manager Error and Warning Checks
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The Driver Manager completely or partially implements a number of functions and therefore checks for all or some of the errors and warnings in those functions.  </para>
    <list class="bullet">
      <listItem>
        <para>The Driver Manager implements <legacyBold>SQLDataSources</legacyBold> and <legacyBold>SQLDrivers</legacyBold> and checks for all errors and warnings in these functions.</para>
      </listItem>
      <listItem>
        <para>The Driver Manager checks whether a driver implements <legacyBold>SQLGetFunctions</legacyBold>. If the driver does not implement <legacyBold>SQLGetFunctions</legacyBold>, the Driver Manager implements and checks for all errors and warnings in it.</para>
      </listItem>
      <listItem>
        <para>The Driver Manager partially implements <legacyBold>SQLAllocHandle</legacyBold>, <legacyBold>SQLConnect</legacyBold>, <legacyBold>SQLDriverConnect</legacyBold>, <legacyBold>SQLBrowseConnect</legacyBold>, <legacyBold>SQLFreeHandle</legacyBold>, <legacyBold>SQLGetDiagRec</legacyBold>, and <legacyBold>SQLGetDiagField</legacyBold> and checks for some errors in these functions. It may return the same errors as the driver for some of these functions because both perform similar operations. For example, the Driver Manager or driver may return SQLSTATE IM008 (Dialog failed) if either one is unable to display a login dialog box for <legacyBold>SQLDriverConnect</legacyBold>.</para>
      </listItem>
    </list>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>