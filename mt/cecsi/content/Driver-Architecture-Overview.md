---
title: Driver Architecture Overview
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ef5a91cd-158e-40bf-b5a8-8ba535c4705e
translation.priority.ht: 
  - en-gb
---
# Driver Architecture Overview
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The Microsoft Visual FoxPro ODBC Driver is a 32-bit driver that enables you to open and query a Microsoft Visual FoxPro database or FoxPro tables through the Open Database Connectivity (ODBC) interface. You can access FoxPro data using the following types of applications:  </para>
  </introduction>
  <section>
    <content>
      <list class="bullet">
        <listItem>
          <para>A Microsoft Office application, such as Microsoft Excel or Microsoft Word, that uses Microsoft Query to communicate with ODBC.</para>
        </listItem>
        <listItem>
          <para>An application written in Microsoft Visual C++ or C that uses the ODBC SDK API.</para>
        </listItem>
        <listItem>
          <para>An application written in Microsoft Visual Basic or Microsoft Visual Basic for Applications.</para>
        </listItem>
      </list>
      <para>In each case, the request for information uses the ODBC API. The ODBC Driver Manager works with the Visual FoxPro ODBC Driver to open and retrieve data from FoxPro tables and databases.</para>
      <para>The architecture is represented in the following diagram:</para>
      <mediaLink>
        <image xlink:href="c68ab6e5-9dbd-498b-a491-176965e02980" />
      </mediaLink>
      <para>This section contains the following topics.  </para>
      <list class="bullet">
        <listItem>
          <para>
            <legacyLink xlink:href="a379b3cb-0393-46e7-b03b-724a56d8f31c">Visual FoxPro Terminology</legacyLink>           </para>
        </listItem>
        <listItem>
          <para>
            <legacyLink xlink:href="4202165e-b89c-47a5-ae59-0c98988caad5">Installing and Configuring the Visual FoxPro ODBC Driver</legacyLink>           </para>
        </listItem>
        <listItem>
          <para>
            <legacyLink xlink:href="c50371a0-b1b2-406c-a4e5-d5191d519f5b">Using the Visual FoxPro ODBC Driver</legacyLink>           </para>
        </listItem>
      </list>
    </content>
  </section>
  <relatedTopics />
</developerConceptualDocument>