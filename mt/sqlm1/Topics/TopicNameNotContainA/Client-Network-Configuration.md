---
title: Client Network Configuration
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c382eacd-0a0c-40a4-958f-9b774eb2d734
---
# Client Network Configuration
  Client software enables client computers to connect to an instance of [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] on a network. A "client" is a front\-end application that uses the services provided by a server such as the [!INCLUDE[ssDEnoversion](../../Token\Other/ssDEnoversion_md.md)]. The computer that hosts this application is referred to as the *client computer*.  
  
 At the simplest level, a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] client can reside on the same machine as an instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]. Typically, however, a client connects to one or more remote servers over a network. The client\/server architecture of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] allows it to seamlessly manage multiple clients and servers on a network. The default client configurations suffice in most situations.  
  
 [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] clients can include applications of various types, such as:  
  
-   OLE DB consumers  
  
     These applications use the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Native Client OLE DB provider to connect to an instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]. The OLE DB provider mediates between [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] and client applications that consume [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] data as OLE DB rowsets. The **sqlcmd** command prompt utility and [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)], are examples of OLE DB applications.  
  
-   ODBC applications  
  
     These applications include client utilities installed with previous versions of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)], such as the **osql** command prompt utility, as well as other applications that use the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Native Client ODBC driver to connect to an instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)].  
  
-   DB\-Library clients  
  
     These applications include the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] **isql** command prompt utility and clients written to DB\-Library. [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] support for client applications using DB\-Library is limited to [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] 7.0 features.  
  
> [!NOTE]  
>  Although the [!INCLUDE[ssDEnoversion](../../Token\Other/ssDEnoversion_md.md)] still supports connections from existing applications using the DB\-Library and Embedded SQL APIs, it does not include the files or documentation needed to do programming work on applications that use these APIs. A future version of the [!INCLUDE[ssDEnoversion](../../Token\Other/ssDEnoversion_md.md)] will drop support for connections from DB\-Library or Embedded SQL applications. Do not use DB\-Library or Embedded SQL to develop new applications. Remove any dependencies on either DB\-Library or Embedded SQL when modifying existing applications. Instead of these APIs, use the SQLClient namespace or an API such as OLE DB or ODBC. [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] does not include the DB\-Library DLL required to run these applications. To run DB\-Library or Embedded SQL applications you must have available the DB\-Library DLL from [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] version 6.5, [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] 7.0, or [!INCLUDE[ssVersion2000](../../Token\Other/ssVersion2000_md.md)].  
  
 Regardless of the type of application, managing a client consists mainly of configuring its connection with the server components of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]. Depending on the requirements of your site, client management can range from little more than entering the name of the server computer to building a library of custom configuration entries to accommodate a diverse multiserver environment.  
  
 The [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Native Client DLL contains the network libraries and is installed by the setup program. The network protocols are not enabled during setup for new installations of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]. Upgraded installations enable the previously enabled protocols. The underlying network protocols are installed as part of Windows Setup \(or through Networks in Control Panel\). The following tools are used to manage [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] clients:  
  
-   [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Configuration Manager  
  
     Both client and server network components are managed with [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Configuration Manager, which combines the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Network Utility, [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Client Network Utility, and Service Manager of previous versions. [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Configuration Manager is a [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] Management Console \(MMC\) snap\-in. It also appears as a node in the Windows Computer Manager snap\-in. Individual network libraries can be enabled, disabled, configured, and prioritized using [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Configuration Manager.  
  
-   Setup  
  
     Run [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] setup to install the network components on a client computer. Individual network libraries can be enabled or disabled during setup when Setup is started from the command prompt.  
  
-   ODBC Data Source Administrator  
  
     The ODBC Data Source Administrator lets you create and modify ODBC data sources on computers running the Microsoft Windows operating system.  
  
## In This Section  
 [Configure Client Protocols](../../Topics\TopicNameNotContainA/Configure-Client-Protocols.md)  
  
 [Create or Delete a Server Alias for Use by a Client &#40;SQL Server Configuration Manager&#41;](../Topic/Create%20or%20Delete%20a%20Server%20Alias%20for%20Use%20by%20a%20Client%20\(SQL%20Server%20Configuration%20Manager\).md)  
  
 [Logging In to SQL Server](../../Topics\TopicNameNotContainA/Logging-In-to-SQL-Server.md)  
  
 [Open the ODBC Data Source Administrator](../../Topics\TopicNameNotContainA/Open-the-ODBC-Data-Source-Administrator.md)  
  
 [Check the ODBC SQL Server Driver Version &#40;Windows&#41;](../Topic/Check%20the%20ODBC%20SQL%20Server%20Driver%20Version%20\(Windows\).md)  
  
## Related Content  
 [Server Network Configuration](../../Topics\TopicNameNotContainA/Server-Network-Configuration.md)  
  
 [Manage the Database Engine Services](../../Topics\TopicNameNotContainA/Manage-the-Database-Engine-Services.md)  
  
  