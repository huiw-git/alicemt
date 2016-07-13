---
title: Using 16-Bit and 32-Bit Applications with 32-Bit Drivers
ms.custom: na
ms.date: 07/12/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: fc65c988-b31f-4cc9-851f-30d2119604fd
manager: jhubbard
translation.priority.ht: 
  - en-gb
---
# Using 16-Bit and 32-Bit Applications with 32-Bit Drivers
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <alert class="important">
      <para>16-bit application support will be removed in a future version of Windows. Avoid using this feature in new development work, and plan to modify applications that currently use this feature. Develop 32-bit or 64-bit applications instead.</para>
    </alert>
    <para>With the ODBC data access component, you can use 16-bit and 32-bit applications with 32-bit drivers. The Microsoft® Windows® 95/98 and Microsoft Windows NT®/Windows 2000 operating systems support the following combinations of applications and drivers:  </para>
    <list class="bullet">
      <listItem>
        <para>16-bit applications with 32-bit drivers</para>
      </listItem>
      <listItem>
        <para>32-bit applications with 32-bit drivers</para>
      </listItem>
    </list>
    <para>Using a 32-bit application with a 16-bit driver is not supported.</para>
    <alert class="note">
      <para>Beginning with the release of ODBC version 3.0, Windows NT 4.0 has been supported. </para>
    </alert>
    <para>ODBC includes the ODBC components necessary to support the above configurations by "thunking" dynamic-link libraries (DLLs) to convert 16-bit addresses to 32-bit addresses and vice versa. The Setup program determines which operating system you are using and installs ODBC components required by that system. You can also choose to install the ODBC components used by all systems.</para>
    <para>In most cases, porting an application or driver from 16-bit to 32-bit involves five types of changes:  </para>
    <list class="bullet">
      <listItem>
        <para>Changes to message-handling code</para>
      </listItem>
      <listItem>
        <para>Changes because integers and handles are 32 bits</para>
      </listItem>
      <listItem>
        <para>Changes in calls to Windows application programming interfaces (APIs)</para>
      </listItem>
      <listItem>
        <para>Changes to make the driver thread-safe</para>
      </listItem>
      <listItem>
        <para>Changes to ODBC components</para>
      </listItem>
    </list>
    <para>From an application or driver programming standpoint, the major difference between 16-bit and 32-bit ODBC components is that they have different file names. From a system standpoint, the architecture of each application or driver connection is different and the tools used to manage data sources are different.</para>
    <para>This section contains the following topics.  </para>
    <list class="bullet">
      <listItem>
        <para>
          <legacyLink xlink:href="68feb3b7-c01a-4f42-8df9-f9c182d89325">Using 16-Bit Applications with 32-Bit Drivers</legacyLink>
        </para>
      </listItem>
      <listItem>
        <para>
          <legacyLink xlink:href="0cdd5788-5642-4280-8d53-b4ec461aafa1">Using 32-Bit Applications with 32-Bit Drivers</legacyLink>
        </para>
      </listItem>
    </list>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>