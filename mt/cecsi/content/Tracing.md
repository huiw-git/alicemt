---
title: Tracing
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 77ed4c6c-d976-4eb2-8526-a12697b0ef83
manager:jhubbard
translation.priority.ht: 
  - en-gb
---
# Tracing
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The ODBC Driver Manager has a trace facility that allows the sequence of function calls made by an ODBC application to be recorded and transcribed into a log file. Tracing is performed by a trace DLL that captures calls between the application and the Driver Manager, and between the Driver Manager and the driver. This method of tracing replaces the tracing performed by the ODBC 2<legacyItalic>.x</legacyItalic> Driver Manager and the tracing performed in ODBC 2<legacyItalic>.x</legacyItalic> by ODBC Spy.</para>
    <para>This section contains the following topics.  </para>
    <list class="bullet">
      <listItem>
        <para>             <legacyLink xlink:href="5ab99bd3-cdc3-4e2c-8827-932d1fcb6e00">Trace DLL</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="ec97f949-126f-40a2-b67e-e74520a524cb">Trace File</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="48e318bd-2487-4708-a698-ea01f36a45e9">Enabling Tracing</legacyLink>           </para>
      </listItem>
      <listItem>
        <para>             <legacyLink xlink:href="ebe58a83-a7b0-4747-86c8-2af2940471ef">Dynamic Tracing</legacyLink>           </para>
      </listItem>
    </list>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>