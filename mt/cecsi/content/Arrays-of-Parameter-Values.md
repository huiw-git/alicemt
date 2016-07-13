---
title: Arrays of Parameter Values
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9b572c5b-1dfe-40af-bebd-051548ab6d90
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Arrays of Parameter Values
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>It is often useful for applications to pass arrays of parameters. For example, using arrays of parameters and a parameterized <legacyBold>INSERT</legacyBold> statement, an application can insert a number of rows at once. There are several advantages to using arrays. First, network traffic is reduced because the data for many statements is sent in a single packet (if the data source supports parameter arrays natively). Second, some data sources can execute SQL statements using arrays faster than executing the same number of separate SQL statements. Finally, when the data is stored in an array, as is often the case for screen data, the application can bind all of the rows in a particular column with a single call to <legacyBold>SQLBindParameter</legacyBold> and update them by executing a single statement.</para>
    <para>Unfortunately, not many data sources support parameter arrays. However, a driver can emulate parameter arrays by executing an SQL statement once for each set of parameter values. This can lead to increases in speed because the driver can then prepare the statement that it plans to execute once for each parameter set. It might also lead to simpler application code.</para>
    <para>This section contains the following topics.  </para>
    <list class="bullet">
      <listItem>
        <para>             <legacyLink xlink:href="037afe23-052d-4f3a-8aa7-45302b199ad0">Binding Arrays of Parameters</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="5a28be88-e171-4f5b-bf4d-543c4383c869">Using Arrays of Parameters</legacyLink>           </para>
      </listItem>
    </list>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>