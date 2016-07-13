---
title: ODBC Architecture
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2604f492-587b-4a51-9876-59a7870b3ef2
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# ODBC Architecture
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The ODBC architecture has four components:  </para>
    <list class="bullet">
      <listItem>
        <para>
          <legacyBold>Application</legacyBold> Performs processing and calls ODBC functions to submit SQL statements and retrieve results.</para>
      </listItem>
      <listItem>
        <para>
          <legacyBold>Driver Manager</legacyBold> Loads and unloads drivers on behalf of an application. Processes ODBC function calls or passes them to a driver.</para>
      </listItem>
      <listItem>
        <para>
          <legacyBold>Driver</legacyBold> Processes ODBC function calls, submits SQL requests to a specific data source, and returns results to the application. If necessary, the driver modifies an application's request so that the request conforms to syntax supported by the associated DBMS.</para>
      </listItem>
      <listItem>
        <para>
          <legacyBold>Data Source</legacyBold> Consists of the data the user wants to access and its associated operating system, DBMS, and network platform (if any) used to access the DBMS.</para>
      </listItem>
    </list>
    <para>Note the following points about the ODBC architecture. First, multiple drivers and data sources can exist, which allows the application to simultaneously access data from more than one data source. Second, the ODBC API is used in two places: between the application and the Driver Manager, and between the Driver Manager and each driver. The interface between the Driver Manager and the drivers is sometimes referred to as the <legacyItalic>service provider interface,</legacyItalic> or <legacyItalic>SPI</legacyItalic>. For ODBC, the application programming interface (API) and the service provider interface (SPI) are the same; that is, the Driver Manager and each driver have the same interface to the same functions.</para>
    <para>This section contains the following topics.  </para>
    <list class="bullet">
      <listItem>
        <para>
          <legacyLink xlink:href="39d6461f-0d24-4b7d-a723-843ade15ad73">Applications</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>
          <legacyLink xlink:href="559e4de1-16c9-4998-94f5-6431122040cd">The Driver Manager</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>
          <legacyLink xlink:href="d6795d92-877e-44e1-b7d5-2ff2fd3989bd">Drivers</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>
          <legacyLink xlink:href="4ae44fa2-0b9b-4e19-ab45-c1dc93b68406">Data Sources</legacyLink>           </para>
      </listItem>
    </list>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>