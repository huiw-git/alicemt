---
title: Oracle Software Patches
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1275157b-f4e1-4c24-b273-c02555e261c2
translation.priority.ht: 
  - en-gb
---
# Oracle Software Patches
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <alert class="important">
      <para>This feature will be removed in a future version of Windows. Avoid using this feature in new development work, and plan to modify applications that currently use this feature. Instead, use the ODBC driver provided by Oracle.</para>
    </alert>
    <para>Patches for the Oracle server products and its client component are required for the proper functioning of several Microsoft products and technologies, including the Microsoft ODBC Driver for Oracle, the Microsoft OLE DB Provider for Oracle, Internet Information Services (IIS), Component Services (or Microsoft Transaction Server, if you are using Windows NT), and so forth.</para>
    <alert class="note">
      <para>The following instructions may not be completely accurate because the Oracle FTP site is subject to change.</para>
    </alert>
    <procedure>
      <title>To download the Oracle software patches</title>
      <steps class="ordered">
        <step>
          <content>
            <para>Connect to the public FTP site at oracle-ftp.oracle.com. The user ID is "anonymous" and the password is your e-mail address.</para>
          </content>
        </step>
        <step>
          <content>
            <para>Navigate to the following directory: /server/wgt_tech/server/windowsNT.</para>
          </content>
        </step>
        <step>
          <content>
            <para>To download patches most relevant for Windows 95, Windows 98 and Windows NT/Windows 2000, navigate to the subdirectory for your version of Oracle — 7.3 or 8.0. The two subdirectories are /73patchsets and /80patchsets.</para>
          </content>
        </step>
        <step>
          <content>
            <para>To download patches for Oracle's network technology, either SQL*Net or Net8, navigate to the following directory: /network.</para>
          </content>
        </step>
      </steps>
      <conclusion>
        <content>
          <para>Accessing this FTP site from your Web browser might not work. If you experience problems, try using a "traditional" FTP client or use the DOS command prompt.</para>
          <alert class="note">
            <para>Because Oracle fixes bugs in current versions and then retrofits them to earlier versions using software patches, it is recommended that you download the latest patch available. This is especially true for the Oracle Server Client components. If you have questions about installing these patches, contact Oracle Support.</para>
          </alert>
        </content>
      </conclusion>
    </procedure>
  </introduction>
  <relatedTopics />
</developerConceptualDocument>