---
title: "Securing RDS Applications"
ms.custom: na
ms.date: 07/11/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 82fb1330-d6c6-4c17-ad3e-d417ff822b25
caps.latest.revision: 14
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
# Securing RDS Applications
<?xml version="1.0" encoding="utf-8"?>
<developerReferenceWithoutSyntaxDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>This topic provides security information for RDS.</para>
    <alert class="important">
      <para>Beginning with Windows 8 and Windows Server 2012, RDS server components are no longer included in the Windows operating system (see Windows 8 and <externalLink><linkText>Windows Server 2012 Compatibility Cookbook</linkText><linkUri>http://download.microsoft.com/download/2/C/9/2C9C7B01-A1FC-47B6-9166-2151FB6E007C/Windows 8 and Windows Server 2012 Compatibility Cookbook.docx</linkUri></externalLink> for more detail). RDS client components will be removed in a future version of Windows. Avoid using this feature in new development work, and plan to modify applications that currently use this feature. Applications that use RDS should migrate to <externalLink><linkText>WCF Data Service</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=199565</linkUri></externalLink>.</para>
    </alert>
  </introduction>
  <section>
    <title>Microsoft Internet Explorer Security Issues</title>
    <content>
      <para>With new security enhancements added to Microsoft Internet Explorer, some ADO and RDS objects are restricted to running only in a "safe" mode environment. This requires that you are aware of these issues, including different zones, security levels, restrictive behavior, unsafe operations, and customized security settings.</para>
    </content>
  </section>
  <section>
    <title>Security and Your Web Server</title>
    <content>
      <para>If you use the <legacyLink xlink:href="e75240c2-b749-471e-b6ea-98cae232efbe">RDSServer.DataFactory</legacyLink> object on your Internet Web server, remember that doing so creates a potential security risk. External users who obtain valid data source name (DSN), user ID, and password information could write pages to send any query to that data source. If you want more restricted access to a data source, one option is to unregister and delete the <legacyBold>RDSServer.DataFactory</legacyBold> object (msadcf.dll), and instead use custom business objects with hard-coded queries.</para>
      <para>For more information on the security implications of using the RDSServer.DataFactory object, see the Microsoft Security Bulletin MS99-025 on the Microsoft Security Web site.</para>
    </content>
  </section>
  <section>
    <title>Client Impersonation and Security</title>
    <content>
      <para>If the <legacyBold>Password Authentication</legacyBold> property for your IIS Web server is set to Windows NT Challenge/Response authentication (for Windows NT 4.0) or to Integrated Windows authentication (for Windows 2000), then business objects are invoked under the client's security context. This is a new feature in RDS 1.5 that allows Client Impersonation over HTTP. When working in this mode, the logon to the Web server (IIS) is not anonymous but uses the user ID and password that the client computer is running under. If the ODBC DSNs are set up to use Trusted Connection, then access to databases, such as SQL Server, also happens under the client's security context. But this only works if the database is on the same computer as the IIS; the client credentials cannot be carried over to yet another computer.</para>
      <para>For example, a client, John Doe, with userid="JohnD" and password="secret" is logged on to a client computer. He runs a browser-based application that needs to access the <legacyBold>RDSServer.DataFactory</legacyBold> object to create a <legacyLink xlink:href="ede1415f-c3df-4cc5-a05b-2576b2b84b60">Recordset</legacyLink> by executing an SQL query on the "MyServer" computer running IIS. MyServer, a system running Windows NT Server 4.0, is set up to use Windows NT Challenge/Response authentication, its ODBC DSN has "Use Trusted Connection" selected, and the server also contains the SQL Server data source. When a request is received on the Web server, it asks the client for the user ID and password. Thus, the request is logged on MyServer as coming from "JohnD"/"Secret" instead of IUSER_MyServer (which is the default when Anonymous Password Authentication is on). Similarly, when logging on to SQL Server, "JohnD"/"Secret" is used.</para>
      <para>Consequently, the IIS Windows NT Challenge/Response authentication mode allows HTML pages to be created without the user being explicitly prompted for the user ID and password information needed to log on to the database. If the IIS Basic Authentication were being used, then this also would be required.</para>
    </content>
  </section>
  <section>
    <title>Password Authentication</title>
    <content>
      <para>RDS can communicate with an IIS Web server running in any one of the three Password Authentication modes: Anonymous, Basic, or NT Challenge/Response authentication (called Integrated Windows authentication in Windows 2000). These settings define how a Web server controls access through it, such as requiring that a client computer have explicit access privileges on the NT Web server.</para>
    </content>
  </section>
  <relatedTopics />
</developerReferenceWithoutSyntaxDocument>