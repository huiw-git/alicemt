---
title: "Running the Address Book SQL Script"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 409b3f8b-0ced-4867-acbe-b245dcdf6702
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
# Running the Address Book SQL Script
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <alert class="important">
      <para>Beginning with Windows 8 and Windows Server 2012, RDS server components are no longer included in the Windows operating system (see Windows 8 and <externalLink><linkText>Windows Server 2012 Compatibility Cookbook</linkText><linkUri>http://download.microsoft.com/download/2/C/9/2C9C7B01-A1FC-47B6-9166-2151FB6E007C/Windows 8 and Windows Server 2012 Compatibility Cookbook.docx</linkUri></externalLink> for more detail). RDS client components will be removed in a future version of Windows. Avoid using this feature in new development work, and plan to modify applications that currently use this feature. Applications that use RDS should migrate to <externalLink><linkText>WCF Data Service</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=199565</linkUri></externalLink>.</para>
    </alert>
    <para>You must use either the ISQL/Query Analyzer command-line utility or the SQL Server Enterprise Manager to run the included SQL script (Sampleemp.sql) that:  </para>
    <list class="bullet">
      <listItem>
        <para>Creates a new database, AddrBookDB, on the default device.</para>
      </listItem>
      <listItem>
        <para>Connects to the database, AddrBookDB.</para>
      </listItem>
      <listItem>
        <para>Creates an Employee table.</para>
      </listItem>
      <listItem>
        <para>Populates the table with sample data.</para>
      </listItem>
      <listItem>
        <para>Runs a simple SELECT statement to verify the population of the database table.</para>
      </listItem>
      <listItem>
        <para>Sets up a user account called "adcdemo" with a password of "adcdemo."</para>
      </listItem>
    </list>
  </introduction>
  <section>
    <content>
      <procedure>
        <title>To run the Sampleemp.sql script in Microsoft SQL Server 6.5</title>
        <steps class="ordered">
          <step>
            <content>
              <para>Click <legacyBold>Start</legacyBold>, point to <legacyBold>Programs</legacyBold>, and then point to <legacyBold>Microsoft SQL Server 6.5</legacyBold>. Click <legacyBold>SQL Enterprise Manager</legacyBold>.</para>
            </content>
          </step>
          <step>
            <content>
              <para>From the <legacyBold>Tools</legacyBold> menu, click <legacyBold>SQL Query Tool</legacyBold>.</para>
            </content>
          </step>
          <step>
            <content>
              <para>Click <legacyBold>Load SQL Script</legacyBold> and browse to c:\Platform SDK\Samples\DataAccess\RDS\AddressBook.</para>
            </content>
          </step>
          <step>
            <content>
              <para>Select the file Sampleemp.sql. Click <legacyBold>Open</legacyBold>.</para>
            </content>
          </step>
          <step>
            <content>
              <para>Click the <legacyBold>Execute Query</legacyBold> button (the green arrow on the toolbar).</para>
            </content>
          </step>
          <step>
            <content>
              <para>After it executes, close the <legacyBold>Query</legacyBold> and <legacyBold>Enterprise Manager</legacyBold> windows. </para>
            </content>
          </step>
        </steps>
      </procedure>
    </content>
  </section>
  <section>
    <content>
      <procedure>
        <title>To run the Sampleemp.sql script in Microsoft SQL Server 7.0</title>
        <steps class="ordered">
          <step>
            <content>
              <para>Click <legacyBold>Start</legacyBold>, point to <legacyBold>Programs</legacyBold>, and then point to <legacyBold>Microsoft SQL Server 7.0</legacyBold>. Click <legacyBold>Enterprise Manager</legacyBold>.</para>
            </content>
          </step>
          <step>
            <content>
              <para>Be sure that the SQL Server that you want to use is selected from your list of registered servers in Enterprise Manager.</para>
            </content>
          </step>
          <step>
            <content>
              <para>From the <legacyBold>Tools</legacyBold> menu, click <legacyBold>SQL Server Query Analyzer</legacyBold>.</para>
            </content>
          </step>
          <step>
            <content>
              <para>Click the <legacyBold>Load SQL Script</legacyBold> button (the open folder on the toolbar) and browse to c:\Platform SDK\Samples\DataAccess\RDS\AddressBook.</para>
            </content>
          </step>
          <step>
            <content>
              <para>Select the file Sampleemp.sql. Click <legacyBold>Open</legacyBold>.</para>
            </content>
          </step>
          <step>
            <content>
              <para>Click the <legacyBold>Execute Query</legacyBold> button (the green arrow on the toolbar) or <legacyBold>F5</legacyBold>.</para>
            </content>
          </step>
          <step>
            <content>
              <para>After it executes, close the <legacyBold>Query</legacyBold>, <legacyBold>Query Analyzer</legacyBold>, and <legacyBold>Enterprise Manager</legacyBold> windows.</para>
            </content>
          </step>
        </steps>
      </procedure>
    </content>
  </section>
  <relatedTopics>
<link xlink:href="3a2644e9-d634-4ae6-a5b7-13fb7b317ec7">Running the Address Book Sample Application</link>
</relatedTopics>
</developerConceptualDocument>