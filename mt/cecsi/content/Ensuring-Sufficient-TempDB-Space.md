---
title: "Ensuring Sufficient TempDB Space"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 09130db1-6248-4234-a1e5-a9c8e1622c06
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
# Ensuring Sufficient TempDB Space
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>If errors occur while handling <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink> objects that need processing space on Microsoft SQL Server 6.5, you may need to increase the size of the TempDB. (Some queries require temporary processing space; for example, a query with an ORDER BY clause requires a sort of the <legacyBold>Recordset</legacyBold>, which requires some temporary space.)</para>
    <alert class="important">
      <para>Beginning with Windows 8 and Windows Server 2012, RDS server components are no longer included in the Windows operating system (see Windows 8 and <externalLink><linkText>Windows Server 2012 Compatibility Cookbook</linkText><linkUri>http://download.microsoft.com/download/2/C/9/2C9C7B01-A1FC-47B6-9166-2151FB6E007C/Windows 8 and Windows Server 2012 Compatibility Cookbook.docx</linkUri></externalLink> for more detail). RDS client components will be removed in a future version of Windows. Avoid using this feature in new development work, and plan to modify applications that currently use this feature. Applications that use RDS should migrate to <externalLink><linkText>WCF Data Service</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=199565</linkUri></externalLink>.</para>
    </alert>
    <alert class="important">
      <para>Read through this procedure before performing the actions because it isn't as easy to shrink a device once it is expanded.</para>
    </alert>
    <alert class="note">
      <para>By default inMicrosoft SQL Server 7.0 and later, TempDB is set to automatically grow as needed. Therefore, this procedure may only be necessary on servers running versions earlier than 7.0.</para>
    </alert>
    <procedure>
      <title>To increase the TempDB space on SQL Server 6.5</title>
      <steps class="ordered">
        <step>
          <content>
            <para>Start Microsoft SQL Server Enterprise Manager, open the tree for the Server, and then open the Database Devices tree.</para>
          </content>
        </step>
        <step>
          <content>
            <para>Select a (physical) device to expand, such as Master, and double-click the device to open the <legacyBold>Edit Database Device</legacyBold> dialog box. </para>
            <para>This dialog box shows how much space the current databases are using. </para>
          </content>
        </step>
        <step>
          <content>
            <para>In the <legacyBold>Size</legacyBold> box, increase the device to the desired amount (for example, 50 megabytes (MB) of hard disk space).</para>
          </content>
        </step>
        <step>
          <content>
            <para>Click <legacyBold>Change Now</legacyBold> to increase the amount of space to which the (logical) TempDB can expand.</para>
          </content>
        </step>
        <step>
          <content>
            <para>Open the Databases tree on the server, and then double-click <legacyBold>TempDB</legacyBold> to open the <legacyBold>Edit Database</legacyBold> dialog box. The <legacyBold>Database</legacyBold> tab lists the amount of space currently allocated to TempDB (<legacyBold>Data Size</legacyBold>). By default, this is 2 MB.</para>
          </content>
        </step>
        <step>
          <content>
            <para>Under the <legacyBold>Size</legacyBold> group, click <legacyBold>Expand</legacyBold>. The graphs show the available and allocated space on each of the physical devices. The bars in maroon color represent available space.</para>
          </content>
        </step>
        <step>
          <content>
            <para>Select a <legacyBold>Log Device</legacyBold>, such as Master,to display the available size in the <legacyBold>Size (MB)</legacyBold> box.</para>
          </content>
        </step>
        <step>
          <content>
            <para>Click <legacyBold>Expand Now</legacyBold> to allocate that space to the TempDB database. </para>
            <para>The <legacyBold>Edit Database</legacyBold> dialog box displays the new allocated size for TempDB. </para>
          </content>
        </step>
      </steps>
      <conclusion>
        <content>
          <para>For more information about this topic, search the Microsoft SQL Server Enterprise Manager Help file for "Expand Database dialog box."</para>
        </content>
      </conclusion>
    </procedure>
  </introduction>
  <relatedTopics>
<link xlink:href="a676f0a7-7d17-45db-87c1-3fc78627465f">RDS Fundamentals</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>