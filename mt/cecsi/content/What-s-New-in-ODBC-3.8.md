---
title: "What&#39;s New in ODBC 3.8"
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 854f0bb4-17e9-489b-9595-eefffb8ba99f
caps.latest.revision: 23
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# What&#39;s New in ODBC 3.8
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Windows 8 includes an updated version of ODBC 3.8. ODBC 3.8 in Windows 8 includes the following features:</para>
    <list class="bullet">
      <listItem>
        <para>
          <link xlink:href="53e7e3f7-edab-4d0b-8943-45442ba3ebc9">Driver-Aware Connection Pooling</link>
        </para>
      </listItem>
      <listItem>
        <para>
          <link xlink:href="e509dad9-5263-4a10-9a4e-03b84b66b6b3">Asynchronous Execution (Notification Method)</link>
        </para>
      </listItem>
      <listItem>
        <para>
          <externalLink>
            <linkText>Data Access Tracing (Windows 8)</linkText>
            <linkUri>https://msdn.microsoft.com/library/windows/desktop/hh829624.aspx</linkUri>
          </externalLink>
        </para>
      </listItem>
      <listItem>
        <para> PowerShell commands have been added to help you manage ODBC data sources, ODBC drivers, ODBC Performance Counter, and data access tracing at the command line.  For more information see <externalLink><linkText>Windows Data Access Components PowerShell Commands</linkText><linkUri>https://msdn.microsoft.com/library/windows/desktop/jj134064.aspx</linkUri></externalLink>.</para>
      </listItem>
    </list>
    <para>Windows 7 includes an updated version of ODBC, ODBC 3.8. ODBC 3.8 includes the following features:</para>
    <list class="bullet">
      <listItem>
        <para>Executing connection operations asynchronously. For more information, see <link xlink:href="8cd21734-ef8e-4066-afd5-1f340e213f9c">Asynchronous Execution</link>.</para>
      </listItem>
      <listItem>
        <para>Streamed output parameters. For more information, see <link xlink:href="7a8c298a-2160-491d-a300-d36f45568d9c">Retrieving Output Parameters by SQLGetData</link>.</para>
      </listItem>
      <listItem>
        <para>ODBC C data type extensibility. For more information, see <link xlink:href="c91bef31-3794-4736-966a-d50997b2233c">C Data Types in ODBC</link>.</para>
      </listItem>
    </list>
    <para>Driver writers should read <link xlink:href="ffba36ac-d22e-40b9-911a-973fa9e10bd3">Upgrading a 3.5 Driver to a 3.8 Driver</link>.</para>
    <para>Asynchronous connection operations can be used by ODBC 3.x and ODBC 2.x applications with an ODBC 3.8 driver.</para>
    <para>For more information, see <link xlink:href="0690b463-15a1-48fa-9d0b-9cc9e5bf7fc6">Compatibility Matrix</link>.</para>
  </introduction>
  <relatedTopics>
<link xlink:href="b33c3c43-ae66-44a3-be17-9cd82624dd96">ODBC Programmer's Reference</link>
</relatedTopics>
</developerConceptualDocument>