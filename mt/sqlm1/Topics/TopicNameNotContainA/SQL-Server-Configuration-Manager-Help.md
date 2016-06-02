---
title: SQL Server Configuration Manager Help
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6e909911-39a6-469b-b22a-3afdfd08a30b
---
# SQL Server Configuration Manager Help
  Use [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Configuration Manager to configure [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] services and configure network connectivity. To create or manage database objects, configure security, and write [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] queries, use [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)]. For more information about [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)], see [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Books Online.  
  
 This section contains the F1 Help topics for the dialogs in [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Configuration Manager.  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Configuration Manager cannot configure versions of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] earlier than [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)][!INCLUDE[ssVersion2005](../../Token\Other/ssVersion2005_md.md)].  
  
## Services  
 [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Configuration Manager manages services that are related to [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]. Although many of these tasks can be accomplished using the [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] Windows Services dialog, is important to note that [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Configuration Manager performs additional operations on the services it manages, such as applying the correct permissions when the service account is changed. Using the normal Windows Services dialog to configure any of the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] services might cause the service to malfunction.  
  
 Use [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Configuration Manager for the following tasks for services:  
  
-   Start, stop, and pause services  
  
-   Configure services to start automatically or manually, disable the services, or change other service settings  
  
-   Change the passwords for the accounts used by the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] services  
  
-   Start [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] using trace flags \(command line parameters\)  
  
-   View the properties of services  
  
## SQL Server Network Configuration  
 Use [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Configuration Manager for the following tasks related to the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] services on this computer:  
  
-   Enable or disable a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] network protocol  
  
-   Configure a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] network protocol  
  
> [!NOTE]  
>  For a short tutorial about how to configure protocols and connect to the [!INCLUDE[ssDEnoversion](../../Token\Other/ssDEnoversion_md.md)], see [Tutorial: Getting Started with the Database Engine](../Topic/Tutorial:%20Getting%20Started%20with%20the%20Database%20Engine.md).  
  
## SQL Server Native Client Configuration  
 [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] clients connect to [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] by using the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Native Client network library. Use [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Configuration Manager for the following tasks related to client applications on this computer:  
  
-   For [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] client applications on this computer, specify the protocol order, when connecting to instances of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)].  
  
-   Configure client connection protocols.  
  
-   For [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] client applications, create aliases for instances of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)], so that clients can connect using a custom connection string.  
  
 For more information about each of these tasks, see F1 help for each task.  
  
#### To open SQL Server Configuration Manager  
  
-   On the **Start** menu, point to **All Programs**, point to **Microsoft SQL Server** \(version\), point to **Configuration Tools**, and then click **SQL Server Configuration Manager**.  
  
## See Also  
 [SQL Server Services](../../Topics\TopicNameNotContainA/SQL-Server-Services.md)   
 [SQL Server Network Configuration](../../Topics\TopicNameNotContainA/SQL-Server-Network-Configuration.md)   
 [SQL Native Client 11.0 Configuration](../../Topics\TopicNameNotContainA/SQL-Native-Client-11.0-Configuration.md)   
 [Choosing a Network Protocol](../Topic/Choosing%20a%20Network%20Protocol.md)  
  
  