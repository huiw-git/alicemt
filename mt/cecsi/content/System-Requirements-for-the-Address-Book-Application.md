---
title: "System Requirements for the Address Book Application"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: da385405-1c9a-478b-9bf6-fba70015324c
caps.latest.revision: 12
manager: sonalm
translation.priority.ht: 
  - de-de
  - es-es
  - fr-fr
  - it-it
  - ja-jp
  - ko-kr
  - pt-br
  - ru-ru
  - zh-cn
  - zh-tw
---
# System Requirements for the Address Book Application
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>To set up the Address Book sample application, you need to meet the following software and database requirements:</para>
    <alert class="important">
      <para>Beginning with Windows 8 and Windows Server 2012, RDS server components are no longer included in the Windows operating system (see Windows 8 and <externalLink><linkText>Windows Server 2012 Compatibility Cookbook</linkText><linkUri>http://download.microsoft.com/download/2/C/9/2C9C7B01-A1FC-47B6-9166-2151FB6E007C/Windows 8 and Windows Server 2012 Compatibility Cookbook.docx</linkUri></externalLink> for more detail). RDS client components will be removed in a future version of Windows. Avoid using this feature in new development work, and plan to modify applications that currently use this feature. Applications that use RDS should migrate to <externalLink><linkText>WCF Data Service</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=199565</linkUri></externalLink>.</para>
    </alert>
  </introduction>
  <section>
    <title>Software Requirements</title>
    <content>
      <para>The server computer software requirements for running this Web application include:  </para>
      <list class="bullet">
        <listItem>
          <para>Microsoft Windows NT® Server 4.0, with Service Pack 3 or later, or Microsoft Windows® 2000 Server.</para>
        </listItem>
        <listItem>
          <para>Microsoft Internet Information Services (IIS) version 3.0 or later, with Active Server Pages.</para>
        </listItem>
      </list>
      <para>The client computer software requirements for running this Web application include:  </para>
      <list class="bullet">
        <listItem>
          <para>Microsoft Internet Explorer 4.0 or later.</para>
        </listItem>
        <listItem>
          <para>Microsoft Windows NT 4.0 Workstation or Server, Windows 2000, or Microsoft Windows 98.</para>
        </listItem>
      </list>
    </content>
  </section>
  <section>
    <title>Database Requirements</title>
    <content>
      <para>To use this sample, you must have:  </para>
      <list class="bullet">
        <listItem>
          <para>An operational Microsoft® SQL Server version 6.5 or later database server.</para>
        </listItem>
        <listItem>
          <para>Privileges to create the database and populate it with the sample data.</para>
        </listItem>
        <listItem>
          <para>Verification of the populated data through Enterprise Manager or the ISQL utilities (called Query Analyzer in SQL Server 7.0).</para>
        </listItem>
      </list>
      <para>If you do not have privileges, your database administrator may need to set up the system and give you access permission to the database, or set up the database for you.</para>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="409b3f8b-0ced-4867-acbe-b245dcdf6702">Running the Address Book SQL Script</link>
<link xlink:href="d85ea4fc-451c-436e-97b8-58f92b149dd0">DataControl Object (RDS)</link>
<link xlink:href="3a2644e9-d634-4ae6-a5b7-13fb7b317ec7">Running the Address Book Sample Application</link>
</relatedTopics>
</developerConceptualDocument>