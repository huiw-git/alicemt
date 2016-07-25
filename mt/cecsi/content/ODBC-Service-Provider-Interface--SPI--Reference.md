---
title: "ODBC Service Provider Interface (SPI) Reference"
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: cdeffb4a-f344-4abe-97f3-be2ede1c8e59
caps.latest.revision: 15
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# ODBC Service Provider Interface (SPI) Reference
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Traditionally, ODBC defined an application programming interface (API). The functions in the API can be called by applications and they should be implemented inside both the Driver Manager and the driver.</para>
    <para>With the addition of the driver-aware connection pooling feature, ODBC introduces the service provider interface (SPI). The functions in the SPI are used for communication between the Driver Manager and driver. SPI functions are implemented by the driver; the Driver Manager does not expose SPI functions to applications. Applications should not call these functions directly.</para>
    <para>Include sqlspi.h for ODBC driver development.</para>
    <para>This section contains the following topics </para>
    <list class="bullet">
      <listItem>
        <para>
          <legacyLink xlink:href="1fc61908-e003-4587-b91a-32f40569fb99">SQLCleanupConnectionPoolID</legacyLink>
        </para>
      </listItem>
      <listItem>
        <para>
          <legacyLink xlink:href="95a8666a-ad68-4d89-bf65-f2cc797f8820">SQLGetPoolID</legacyLink>
        </para>
      </listItem>
      <listItem>
        <para>
          <legacyLink xlink:href="41322737-890d-4a81-aed2-06cc3d546962">SQLPoolConnect</legacyLink>
        </para>
      </listItem>
      <listItem>
        <para>
          <legacyLink xlink:href="e8da2ffb-d6ef-4ca7-824f-57afd29585d8">SQLRateConnection</legacyLink>
        </para>
      </listItem>
      <listItem>
        <para>
          <legacyLink xlink:href="a28fadb9-b998-472a-b252-709507e92005">SQLSetConnectAttrForDbcInfo</legacyLink>
        </para>
      </listItem>
      <listItem>
        <para>
          <legacyLink xlink:href="0782a1c3-c5d1-499b-a8ba-134162db9990">SQLSetConnectInfo</legacyLink>
        </para>
      </listItem>
      <listItem>
        <para>
          <legacyLink xlink:href="bfd4dfc2-fbca-4ef3-81e5-2706f2389256">SQLSetDriverConnectInfo</legacyLink>
        </para>
      </listItem>
    </list>
  </introduction>
  <relatedTopics>
    <link xlink:href="3225a011-5605-46ba-bb74-1ca6106a5271">Developing an ODBC Driver</link>
<link xlink:href="c63d5cae-24fc-4fee-89a9-ad0367cddc3e">Developing Connection-Pool Awareness in an ODBC Driver</link>
<link xlink:href="ee95ffdb-5aa1-49a3-beb2-7695b27c3df9">Driver Manager Connection Pooling</link></relatedTopics>
</developerConceptualDocument>