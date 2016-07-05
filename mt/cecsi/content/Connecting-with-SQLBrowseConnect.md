---
title: Connecting with SQLBrowseConnect
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6c2e9f76-b766-48df-b109-246bb05ae45d
translation.priority.ht: 
  - en-gb
---
# Connecting with SQLBrowseConnect
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>       <legacyBold>SQLBrowseConnect</legacyBold>, like <legacyBold>SQLDriverConnect</legacyBold>, uses a connection string. However, by using <legacyBold>SQLBrowseConnect</legacyBold>, an application can construct a complete connection string at run time. This allows the application to do two things:  </para>
    <list class="bullet">
      <listItem>
        <para>Build its own dialog boxes to prompt for this information, thereby retaining control over its "look and feel."</para>
      </listItem>
      <listItem>
        <para>Browse the system for data sources that can be used by a particular driver, possibly in several steps. For example, the user might first browse the network for servers and, after choosing a server, browse the server for databases accessible by the driver.</para>
      </listItem>
    </list>
    <para>The application calls <legacyBold>SQLBrowseConnect</legacyBold> and passes a connection string, known as the <legacyItalic>browse request connection string,</legacyItalic> that specifies a driver or data source. The driver returns a connection string, known as the <legacyItalic>browse result connection string,</legacyItalic> that contains keywords, possible values (if the keyword accepts a discrete set of values), and user-friendly names. The application builds a dialog box with the user-friendly names and prompts the user for values. It then builds a new browse request connection string from these values and returns this to the driver with another call to <legacyBold>SQLBrowseConnect</legacyBold>.</para>
    <para>Because connection strings are passed back and forth, the driver can provide several levels of browsing by returning a new connection string when the application returns the old one. For example, the first time an application calls <legacyBold>SQLBrowseConnect</legacyBold>, the driver might return keywords to prompt the user for a server name. When the application returns the server name, the driver might return keywords to prompt the user for a database. The browsing process would be complete after the application returned the database name.</para>
    <para>Each time <legacyBold>SQLBrowseConnect</legacyBold> returns a new browse result connection string, it returns SQL_NEED_DATA as its return code. This tells the application that the connection process is not complete. Until <legacyBold>SQLBrowseConnect</legacyBold> returns SQL_SUCCESS, the connection is in a Need Data state and cannot be used for other purposes, such as to set a connection attribute. The application can terminate the connection browsing process by calling <legacyBold>SQLDisconnect</legacyBold>.</para>
    <para>This section contains the following topic.  </para>
    <list class="bullet">
      <listItem>
        <para>             <legacyLink xlink:href="6e0d5fd1-ec93-4348-a77a-08f5ba738bc6">SQL Server Browsing Example</legacyLink>           </para>
      </listItem>
    </list>
  </introduction>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>