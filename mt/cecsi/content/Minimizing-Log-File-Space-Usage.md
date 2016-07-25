---
title: "Minimizing Log File Space Usage"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 669662a0-e20f-483e-ab28-53f66c524c98
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
# Minimizing Log File Space Usage
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>A log file may fill quickly (thus halting the server) if there is a large volume of activity on an SQL Server database. You can set the log file to <legacyBold>Truncate on Checkpoint </legacyBold>to significantly extend the life of the log file for a database.</para>
    <alert class="important">
      <para>Beginning with Windows 8 and Windows Server 2012, RDS server components are no longer included in the Windows operating system (see Windows 8 and <externalLink><linkText>Windows Server 2012 Compatibility Cookbook</linkText><linkUri>http://download.microsoft.com/download/2/C/9/2C9C7B01-A1FC-47B6-9166-2151FB6E007C/Windows 8 and Windows Server 2012 Compatibility Cookbook.docx</linkUri></externalLink> for more detail). RDS client components will be removed in a future version of Windows. Avoid using this feature in new development work, and plan to modify applications that currently use this feature. Applications that use RDS should migrate to <externalLink><linkText>WCF Data Service</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=199565</linkUri></externalLink>.</para>
    </alert>
    <procedure>
      <title>To enable Truncate on Checkpoint in Microsoft SQL Server 6.5</title>
      <steps class="ordered">
        <step>
          <content>
            <para>Start Microsoft SQL Server Enterprise Manager, open the tree for the Server, and then open the Database Devices tree.</para>
          </content>
        </step>
        <step>
          <content>
            <para>Double-click the name of the database on which this feature will be enabled.</para>
          </content>
        </step>
        <step>
          <content>
            <para>From the <legacyBold>Database</legacyBold> tab, select <legacyBold>Truncate</legacyBold>.</para>
          </content>
        </step>
        <step>
          <content>
            <para>From the <legacyBold>Options</legacyBold> tab, select <legacyBold>Truncate Log on Checkpoint</legacyBold>, and then click <legacyBold>OK</legacyBold>.</para>
          </content>
        </step>
      </steps>
    </procedure>
    <procedure>
      <title>To enable Truncate on Checkpoint in Microsoft SQL Server 7.0</title>
      <steps class="ordered">
        <step>
          <content>
            <para>Start Microsoft SQL Server Enterprise Manager, open the tree for the Server, and then open the Databases tree.</para>
          </content>
        </step>
        <step>
          <content>
            <para>Right-click the name of the database on which this feature will be enabled and choose <legacyBold>Properties</legacyBold>.</para>
          </content>
        </step>
        <step>
          <content>
            <para>From the <legacyBold>Options</legacyBold> tab, select <legacyBold>Truncate Log on Checkpoint</legacyBold>, and then click <legacyBold>OK</legacyBold>.</para>
          </content>
        </step>
      </steps>
      <conclusion>
        <content>
          <para>For more information about the <legacyBold>Truncate on Checkpoint</legacyBold> feature, see the Microsoft SQL Server documentation.</para>
        </content>
      </conclusion>
    </procedure>
  </introduction>
  <relatedTopics>
<link xlink:href="a676f0a7-7d17-45db-87c1-3fc78627465f">RDS Fundamentals</link>
</relatedTopics>
</developerReferenceWithoutSyntaxDocument>